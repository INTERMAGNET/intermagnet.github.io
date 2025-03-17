---
title: INTERMAGNET Data - conditions of use
---

<!-- This section copied from Creative Commons - please don't change -->
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Creative Commons Licence" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br />Unless otherwise noted, data downloaded through INTERMAGNET is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License</a>. A list of institutes with different license conditions is given at the [end of this page](#institutes-with-different-or-additional-license-and-acknowledgment-conditions).

The data made available through INTERMAGNET are provided for non-commercial use.  For commercial use or sale or bulk distribution to third parties please obtain written permission from the [institute](metadata/#/institutes) operating the observatory and their [contact person](metadata/#/imos).

INTERMAGNET data and plots are available, via the [INTERMAGNET data portal](data_portal). The availability of preliminary data files is dependent on the publishing delay of participating institutes. Data from observatories that are not members of INTERMAGNET and data prior to INTERMAGNET commencing operation may be available via one of the World Data Centres for Geomagnetism (WDC) or from the observatory contact of the specific Intermagnet Magnetic Observatory, which can be found at [https://intermagnet.org/metadata/#/imos](https://intermagnet.org/metadata/#/imos).

The member institutes of INTERMAGNET invest considerable resources to operate their magnetic observatories to INTERMAGNET standards. It is important that the institutes producing the data have a measure of the scientific return on their investment.

## Acknowledgement of data from observatories participating in INTERMAGNET

INTERMAGNET publishes its data in the form of Digital Object Identifiers (DOIs). Definitive INTERMAGNET data publications from 2013 onwards are available as [DOIs](/data_download.html#downloading_data_using_dois).

The preferred method for acknowledging INTERMAGNET data is to cite relevant DOIs. However much of INTERMAGNET's data is not available as a DOI. DOIs are not yet available for the original annual publications of definitive data from 1991 to 2012 or for any preliminary INTERMAGNET data.

Where DOIs are not available, publications making use of INTERMAGNET data should include an acknowledgement statement of the form given below. A citation reference should be sent to the [INTERMAGNET Secretary](mailto:secretary_intermagnet@gfz-potsdam.de) for inclusion in a publications list on the INTERMAGNET website.

We offer two acknowledgement templates. The first is for cases where data from many observatories have been used and it is not practical to list them all, or each of their operating institutes. The second is for cases where research results have been produced using a smaller set of observatories.

### Suggested Acknowledgement Text (template 1)

The results presented in this paper rely on data collected at magnetic observatories. We thank the national institutes that support them and INTERMAGNET for promoting high standards of magnetic observatory practice (www.intermagnet.org).

### Suggested Acknowledgement Text (template 2)

The results presented in this paper rely on the data collected at *observatory name*. We thank *institute name*, for supporting its operation and INTERMAGNET for promoting high standards of magnetic observatory practice (www.intermagnet.org).

## Institutes with different or additional license and acknowledgment conditions

Individual INTERMAGNET institutes may have broader license conditions; it is incumbent on the user to contact individual institutes to determine these exceptions.

| Institute | Observatories | License details |
|-----------|---------------|-----------------|
| BCMT (IPGP and EOST) | AAE, AMS, BNG, CLF, CZT, DLT, DMC, DRV, IPM, KOU, MBO, PAF, PHU, PPT, PSM, TAN, VLJ | [http://www.bcmt.fr/termsofuse.html](http://www.bcmt.fr/termsofuse.html) |

## Observatories with temporary data embargos

<div>
    <label for="sortOptions">Sort by:</label>
    <select id="sortOptions">
        <option value="IagaCode">Iaga Code</option>
        <option value="Latitude">Latitude</option>
        <option value="Longitude">Longitude</option>
    </select>

    <table id="observatoryTable">
        <thead>
            <tr>
                <th>Observatory Iaga Code</th>
                <th>Latitude</th>
                <th>Longitude</th>
                <th>Plot Embargo</th>
                <th>Data Embargo</th>
            </tr>
        </thead>
        <tbody>
            <!-- Rows will be added here dynamically -->
        </tbody>
    </table>

    <script>
        const dataUrl = 'https://imag-data.bgs.ac.uk/GIN_V1/GINServices?Request=GetCapabilities&format=json';
        let observatories = []; // Store fetched data

        // Convert hours into "X days, Y hours"
        function formatEmbargo(hours) {
            if (hours === 0) return ""; // Return empty string for zero embargo

            const days = Math.floor(hours / 24);
            const remainingHours = hours % 24;

            const dayLabel = days === 1 ? "day" : "days";
            const hourLabel = remainingHours === 1 ? "hour" : "hours";

            if (days > 0 && remainingHours > 0) {
                return `${days} ${dayLabel}, ${remainingHours} ${hourLabel}`;
            } else if (days > 0) {
                return `${days} ${dayLabel}`;
            } else {
                return `${remainingHours} ${hourLabel}`;
            }
        }

        // Fetch JSON data
        async function fetchObservatoryData() {
            try {
                const response = await fetch(dataUrl);
                const data = await response.json();

                if (data.ObservatoryList && Array.isArray(data.ObservatoryList)) {
                    observatories = data.ObservatoryList.filter(obs =>
                        obs.PlotEmbargoHours !== 0 || obs.DataEmbargoHours !== 0
                    );

                    populateTable(observatories);
                } else {
                    console.error('ObservatoryList is not available in the fetched data.');
                }
            } catch (error) {
                console.error('Error fetching or processing data:', error);
            }
        }

        // Populate table
        function populateTable(observatories) {
            const tableBody = document.getElementById('observatoryTable').getElementsByTagName('tbody')[0];
            tableBody.innerHTML = '';

            observatories.forEach(obs => {
                const row = tableBody.insertRow();

                row.insertCell(0).textContent = obs.IagaCode;
                row.insertCell(1).textContent = obs.Latitude.toFixed(2);
                row.insertCell(2).textContent = obs.Longitude.toFixed(2);
                row.insertCell(3).textContent = formatEmbargo(obs.PlotEmbargoHours);
                row.insertCell(4).textContent = formatEmbargo(obs.DataEmbargoHours);
            });
        }

        // Sort observatories based on selected option
        function sortObservatories(criteria) {
            observatories.sort((a, b) => {
                if (criteria === "IagaCode") {
                    return a.IagaCode.localeCompare(b.IagaCode);
                } else {
                    return a[criteria] - b[criteria]; // Sorting numbers (Latitude, Longitude)
                }
            });
            populateTable(observatories);
        }

        // Event listener for sorting dropdown
        document.getElementById("sortOptions").addEventListener("change", function () {
            sortObservatories(this.value);
        });

        window.onload = fetchObservatoryData;
    </script>
</div>

