# Forest Topology

Protecting biodiversity and curbing carbon emissions from deforestation demands
a deeper understanding of global forest cover. Informed decision-making hinges
not only on knowing where forests are, but on understanding their composition
and distinguishing natural forests that play critical roles as biodiversity
hotspots and major carbon sinks.

In a collaboration between [Google DeepMind](https://deepmind.google/) (GDM),
[World Resources Institute](https://www.wri.org/) (WRI) and
[Google Geo Sustainability](https://earthoutreachonair.withgoogle.com/), we
developed a novel approach to map natural forests, including primary and
secondary naturally regenerating forests, using semantic segmentation deep
learning model based on a multi-modal, multi-temporal vision transformer. The
resulting global natural forest map for 2020, produced in support of the
[European Union's Deforestation Regulations](https://environment.ec.europa.eu/topics/forests/deforestation/regulation-deforestation-free-products_en) (EUDR), provides a comprehensive
baseline for monitoring deforestation and guiding conservation efforts. To
support decision making in these efforts, next to the estimated probabilities of
natural forests we also release a layer of model uncertainty.

<div style="text-align:center">
    <figure>
        <img src ="img/natural_forest.png" width="1000">
        <figcaption>
        Natural forests of the world (primary and secondary naturally regenerating).
        </figcaption>
    </figure>
</div>


## Definitions

**Forest**: We follow the Food and Agriculture Organization's (FAO) Forest Resources Assessment (FRA) [definitions](https://openknowledge.fao.org/server/api/core/bitstreams/531a9e1b-596d-4b07-b9fd-3103fb4d0e72/content#:~:text=OTHER%20WOODED%20LAND-,FOREST,agricultural%20or%20urban%20land%20use) of forest to have patches areas of
at least 0.5 hectares with trees heights being able to reach 5 meters and canopy
cover of at least 10%.

**Natural forest**: A forest that is a natural ecosystem, in terms of species
composition, structure, and ecological function. It includes primary forests,
with no major human impact in recent history, as well as naturally regenerating
secondary forests, where the forest ecosystem has attained much of the prior or
other contemporary natural ecosystems. The natural forest can include managed forests,
where much of the ecosystem's composition, structure, and ecological function
exists in presence of harvesting of timber or other forest products, including
promoting high-value species, and low-intensity, small-scale cultivation within
the forest. Also, partly degraded forests are included (as long as it is not
converted to other forest or land use types and degradation does not result in
the sustained reduction of tree cover below the FAO defined thresholds).

## Natural Forests of the World (v1)
Below are the details for the first release of the natural forest map (v1).

### Data characteristics

*   Resolution: 10 meters
*   Spatial extent: global
*   Temporal extent: version `2020_v1_0` estimates natural forest confidence score (pseudo-probability) for the year 2020.
*   The data is available on Google Cloud Storage in 10,190 GeoTIFF files (271 GB), usually split into multiple files per UTM  zone cell.
*   File naming: `"raster_{UTM_CELL}_{SUB_SPLIT}.tif"`, where `UTM_CELL` represents the
    [Universal Transverse Mercator (UTM)](https://en.wikipedia.org/wiki/Universal_Transverse_Mercator_coordinate_system)
    cell ID of the form `{longitude number id}{latitude letter id}` (for example
    `"18T"` is the UTM ID for the cell containing New York City), and `SUB_SPLIT` is a indicating the sub-split of the UTM zone cell.
*   Bands (`uint8` data type):
    *   Band 1: Confidence score (pseudo-probability) of "Natural forest" class (originally float in the range [0-1], but for disk space reduction it is scaled to [0-250] and quantized to `uint8`).

### Data locations and download instructions

Google Cloud Storage data location:
[https://storage.googleapis.com/forest_typology/natural_forest_2020_v1_0](https://storage.googleapis.com/forest_typology/natural_forest_2020_v1_0)

You can download the data using
[Cloud SDK](https://cloud.google.com/sdk/docs/quickstart), which provides the
`gcloud` utility, with a [command](https://cloud.google.com/storage/docs/discover-object-storage-gcloud#download_the_object_from_your_bucket) like

```bash
gsutil storage cp -r gs://forest_typology/natural_forest_2020_v1_0 /tmp/
```

or using `wget` via:

```bash
wget https://storage.googleapis.com/forest_typology/natural_forest_2020_v1_0/raster_10J_5_0_1.tif
```

<!-- GEE asset ID: TBD -->

## Citing this work

You can cite this work as

```latex
@article{natural_forest,
    title={Natural forests of the world: A 2020 baseline for
           deforestation monitoring},
    author={TBD},
    journal={TBD},
    year={2025},
    note={Draft},
}
```

## License and disclaimer

Copyright 2025 DeepMind Technologies Limited

All non-software materials are licensed under the Creative Commons Attribution 4.0
International License (CC-BY). You may obtain a copy of the CC-BY license at:
https://creativecommons.org/licenses/by/4.0/legalcode

Unless required by applicable law or agreed to in writing, all software and
materials distributed here under the Apache 2.0 or CC-BY licenses are
distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
either express or implied. See the licenses for the specific language governing
permissions and limitations under those licenses.

This is not an official Google product.
