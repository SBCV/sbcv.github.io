---
layout: default
title: Earth Observation Tiles
description: 
img: assets/img/segmentation/dar_0a4c40_overview_category.jpg
importance: 1
category:
---

<!-- This pages embeds content of:
    https://sbcv.github.io/EarthObservationTilesWebsite/
        qgis2web/potsdam_2_14_jgp_leaflet_full_screen/index.html
        images/dar_0a4c40_overview_category.jpg
        qgis2web/open_cities_dar_0a4c40_subpart_leaflet_full_screen/index.html
-->

<!-- https://getbootstrap.com/docs/4.0/utilities/spacing/
    The classes are named using the format 
        {property}{sides}-{size} for xs 
        and 
        {property}{sides}-{breakpoint}-{size} for sm, md, lg, and xl.
    e.g.
        {property}{sides}-{size} = mt-3
        {property}{sides}-{breakpoint}-{size} = mt-md-0
-->

<style type="text/css">
  /* https://stackoverflow.com/questions/19138758/how-to-align-caption-underneath-image */
  figure {
      display: inline-block;
      margin: 20px; /* margin between images */
  }
  figure img {
      vertical-align: top;
  }
  figure figcaption {
      text-align: center;
  }

  /*
  Overwrite botstrap caption position:
    https://stackoverflow.com/questions/48647942/table-caption-goes-bottom-using-bootstrap
  */
  /*
  caption {
      caption-side:top;   
  }
  */

</style>


<div align="middle"><font size="5">Geo-Tiles for Semantic Segmentation of Earth Observation Imagery</font> </div>
<div align="middle"> Sebastian Bullinger, Florian Fevers, Christoph Bodensteiner and Michael Arens</div>

<div align="middle">
  <figure class="figure">
      <a href="http://arxiv.org/abs/2306.00823"> <img src="/assets/img/header/eot_paper_thumb_cropped.png"/> </a>
      <figcaption> <a href="http://arxiv.org/abs/2306.00823"> Paper </a></figcaption>
  </figure>
  <figure class="figure">
      <a href="https://github.com/SBCV/EarthObservationTiles"> <img src="/assets/img/header/github.png"/> </a>
      <figcaption> <a href="https://github.com/SBCV/EarthObservationTiles"> Code </a></figcaption>
  </figure>
</div>

#### Abstract

<p style="text-align: justify">
To cope with the high requirements during the computation of semantic segmentations of earth observation imagery, current state-of-the-art pipelines divide the corresponding data into smaller images. Existing methods and benchmark datasets oftentimes rely on pixel-based tiling schemes or on geo-tiling schemes employed by web mapping applications. The selection of the subimages (comprising size, location and orientation) is crucial since it affects the available context information of each pixel, defines the number of tiles during training, and influences the degree of information degradation while down- and up-sampling the tile contents to the size required by the segmentation model. In this paper we propose a new segmentation pipeline for earth observation imagery relying on a tiling scheme that creates geo-tiles based on the geo-information of the raster data. This approach exhibits several beneficial properties compared to pixel-based or common web mapping approaches. For instance, the proposed tiling scheme shows flexible customization properties regarding tile granularity, tile stride and image boundary alignment, which allows us to perform a tile specific data augmentation during training and a substitution of pixel predictions with limited context information using data of overlapping tiles during inference. Furthermore, the generated tiles show a consistent spatial tile extent w.r.t. heterogeneous sensors, varying recording distances and different latitudes. In our experiments we demonstrate how the proposed tiling system allows to improve the results of current state-of-the-art semantic segmentation models. To foster future research we make the source code publicly available.
</p>

#### Earth Observation Tiles
Visual comparison of Earth Observation Tiles (left) with a standard web map tiling scheme (right).

<figure class="figure">
  <!-- https://getbootstrap.com/docs/4.0/content/figures/ -->
  <p float="left" align="middle">
    <img src="/assets/img/segmentation/tiling/optimized_overhang_n.jpg" width="45%" />
    <img src="/assets/img/segmentation/tiling/mercator_border_n.jpg" width="45%" />
    <img src="/assets/img/segmentation/tiling/optimized_overhang_y.jpg" width="45%" />
    <img src="/assets/img/segmentation/tiling/mercator_border_y.jpg" width="45%" />
  </p>
  <figcaption class="figure-caption"> Figure 1: Comparison of the proposed tiling approach (left) and a common web map tiling scheme (right).</figcaption>
</figure>

Property comparison of different tiling schemes:

<table class="table table-sm" style="font-size: 14px;">
   <!-- https://getbootstrap.com/docs/4.0/content/tables/ -->
  <caption>Table 1: Comparison of the proposed tiling approach with common tiling schemes.</caption>
  <tr>
    <th style="border-right: 1px solid black; border-bottom: 1px solid black;">Tiling Scheme Property</th>
    <th align="center" style="border-bottom: 1px solid black;">Pixel-based <BR> Tiling</th>
    <th align="center" style="border-bottom: 1px solid black;">Web Map <BR> Tiling</th>
    <th align="center" style="border-bottom: 1px solid black;">Earth Observation <BR> Tiling (ours)</th>
  </tr>
  <tr>
    <td style="border-right: 1px solid black;">Consistent spatial extent for different sensors</td>
    <td align="center">&#x2717;</td>
    <td align="center">&#x2713;</td>
    <td align="center">&#x2713;</td>
  </tr>
  <tr>
    <td style="border-right: 1px solid black;">Consistent spatial extent for different recording distances</td>
    <td align="center">&#x2717;</td>
    <td align="center">&#x2713;</td>
    <td align="center">&#x2713;</td>
  </tr>
  <tr>
    <td style="border-right: 1px solid black;">Consistent spatial extent for different latitudes</td>
    <td align="center">&#x2713;</td>
    <td align="center">&#x2717;</td>
    <td align="center">&#x2713;</td>
  </tr>
    <tr>
    <td style="border-right: 1px solid black;">Optimal raster image coverage / alignment to raster image</td>
    <td align="center">&#x2713;</td>
    <td align="center">&#x2717;</td>
    <td align="center">&#x2713;</td>
  </tr>
    <tr>
    <td style="border-right: 1px solid black;">Customization (e.g. arbitrary granularity or overlap)</td>
    <td align="center">&#x2713;</td>
    <td align="center">&#x2717;</td>
    <td align="center">&#x2713;</td>
  </tr>
    <tr>
    <td style="border-right: 1px solid black;">Arbitrary coordinate system support</td>
    <td align="center">&#x2713;</td>
    <td align="center">&#x2717;</td>
    <td align="center">&#x2713;</td>
  </tr>
    <tr>
    <td style="border-right: 1px solid black;">Non-normalized raster image support</td>
    <td align="center">&#x2713;</td>
    <td align="center">&#x2717;</td>
    <td align="center">&#x2713;</td>
  </tr>
</table>


#### Tile Fusion During Inference Time
<figure class="figure">
 <p float="left" align="middle">
  <img src="/assets/img/segmentation/fusion/top_potsdam_3_14_RGB_image.jpg" width="32%"/>
  <img src="/assets/img/segmentation/fusion/top_potsdam_3_14_RGB_ground_truth.jpg" width="32%"/>
  <img src="/assets/img/segmentation/fusion/top_potsdam_3_14_RGB_fusion_improvement.jpg" width="32%"/>
</p> <p float="left" align="middle">
  <img src="/assets/img/segmentation/fusion/top_potsdam_4_14_RGB_image.jpg" width="32%"/>
  <img src="/assets/img/segmentation/fusion/top_potsdam_4_14_RGB_ground_truth.jpg" width="32%"/>
  <img src="/assets/img/segmentation/fusion/top_potsdam_4_14_RGB_fusion_improvement.jpg" width="32%"/>
</p> <p float="left" align="middle">
  <img src="/assets/img/segmentation/fusion/dar_0a4c40_site_1_image.jpg" width="32%"/>
  <img src="/assets/img/segmentation/fusion/dar_0a4c40_site_1_ground_truth.jpg" width="32%"/>
  <img src="/assets/img/segmentation/fusion/dar_0a4c40_site_1_fusion_improvement.jpg" width="32%"/>
</p> <p float="left" align="middle">
  <img src="/assets/img/segmentation/fusion/dar_f883a0_image.jpg" width="32%"/>
  <img src="/assets/img/segmentation/fusion/dar_f883a0_ground_truth.jpg" width="32%"/>
  <img src="/assets/img/segmentation/fusion/dar_f883a0_fusion_improvement.jpg" width="32%"/>
</p>
  <figcaption class="figure-caption"> Figure 2: Comparison of standard semantic segmentations  with results obtained by fusion of overlapping tiles. The left column shows the input image, the center column highlights the corresponding ground truth and the right column visualizes the fusion results. The meaning of the colors in the fused segmentation (right column) are: blue building pixels are contained in both results, pink building pixels are only part of the fused segmentation and teal building pixels are exclusively present in the standard segmentation.</figcaption>
</figure>


#### Example Segmentations
Example semantic segmentation (**interactive!**) of an area contained in the [ISPRS potsdam dataset](https://www.isprs.org/education/benchmarks/UrbanSemLab/default.aspx):
<iframe src="https://sbcv.github.io/EarthObservationTilesWebsite/qgis2web/potsdam_2_14_jgp_leaflet_full_screen/index.html" width="100%" height="500px" style="display: block;">
</iframe>
<p></p>

Example semantic segmentation (**interactive!**) of an area contained in the [Open Cities AI dataset](https://www.drivendata.org/competitions/60/building-segmentation-disaster-resilience/):
<iframe src="https://sbcv.github.io/EarthObservationTilesWebsite/qgis2web/open_cities_dar_0a4c40_subpart_leaflet_full_screen/index.html" width="100%" height="500px" style="display: block;">
</iframe>
<img src="https://sbcv.github.io/EarthObservationTilesWebsite/images/dar_0a4c40_overview_category.jpg" alt="image info" width="100%"/>
