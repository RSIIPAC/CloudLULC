# Land cover mapping with multimodal satellite imagery: a high-order heterogeneous knowledge modulation strategy for land use classification under various cloudy conditions
## Jiangong Xu, Weibao Xue, Xiaoyu Yu, Jun Pan, Mi Wang, Junli Li
![p1](https://github.com/RSIIPAC/CloudLULC/blob/main/Subsidiaries/conceptual.png)
To mitigate the impact of cloud contamination on spatiotemporal seamless LULC mapping and overcome the limitations of existing multimodal fusion methods, this study proposes a novel LULC mapping framework, called the multi-model high-order collaboration network (MHC-Net).

## Dataset
We have also developed the first public dataset, LuojiaSET-PolCR, which explicitly introduces PolSAR polarimetric scattering characteristics into cloud-contaminated optical satellite image reconstruction to advance research in this field.
Links to **[here](https://www.wenjuan.com/s/JnyMzq1/#)** download the data.
![p2](https://github.com/RSIIPAC/CloudLULC/blob/main/Subsidiaries/location.png)

We divide all the patches into three subdatasets, namely, training set, validation set, testing, and write the division in a .csv file as:
```
1	Sen-1_auxiliary-Alpha	Sen-1_auxiliary-Anisotropy	Sen-1_auxiliary-C11	Sen-1_auxiliary-C12_imag	Sen-1_auxiliary-C12_real	Sen-1_auxiliary-C22	Sen-1_auxiliary-Entropy	Sen-2_cloudy	Sen-2_reference	ROIs_40_p_4790.tif
2	Sen-1_auxiliary-Alpha	Sen-1_auxiliary-Anisotropy	Sen-1_auxiliary-C11	Sen-1_auxiliary-C12_imag	Sen-1_auxiliary-C12_real	Sen-1_auxiliary-C22	Sen-1_auxiliary-Entropy	Sen-2_cloudy	Sen-2_reference	ROIs_09_p_3372.tif
3	Sen-1_auxiliary-Alpha	Sen-1_auxiliary-Anisotropy	Sen-1_auxiliary-C11	Sen-1_auxiliary-C12_imag	Sen-1_auxiliary-C12_real	Sen-1_auxiliary-C22	Sen-1_auxiliary-Entropy	Sen-2_cloudy	Sen-2_reference	ROIs_37_p_0903.tif
```
Here label is a number and 1 represents training set, 2 represents validation set and 3 represents testing set. 
Then build the file structure in your computer as the folder dataset shown.
```
./
+-- LuojiaSET-PolCR
    +--	Sen-1_auxiliary
        +-- Alpha
        |   +-- patch_ROIs_01_name.tif
        |   +-- ...
        +-- Anisotropy
        |   +-- patch_ROIs_01_name.tif
        |   +-- ...
        +-- C11
        |   +-- patch_ROIs_01_name.tif
        |   +-- ...
        +-- C12_imag
        |   +-- patch_ROIs_01_name.tif
        |   +-- ...
        +-- C12_real
        |   +-- patch_ROIs_01_name.tif
        |   +-- ...
        +-- C22
        |   +-- patch_ROIs_01_name.tif
        |   +-- ...
        +-- Entropy
        |   +-- patch_ROIs_01_name.tif
        |   +-- ...
     +-- Sen-2_cloudy
        |   +-- patch_ROIs_01_name.tif
        |   +-- ...
     +-- Sen-2_reference
        |   +-- patch_ROIs_01_name.tif
        |   +-- ...
```

## Contact
If you have any questions about this work please concat me. E-mail: panjun1215@whu.edu.cn, dd_xjg@whu.edu.cn
