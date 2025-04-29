# Land cover mapping with multimodal satellite imagery: a high-order heterogeneous knowledge modulation strategy for land use classification under various cloudy conditions
## Jiangong Xu, Weibao Xue, Xiaoyu Yu, Jun Pan, Mi Wang, Junli Li
![image](https://github.com/RSIIPAC/CloudLULC/blob/main/Subsidiaries/conceptual.png)
To mitigate the impact of cloud contamination on spatiotemporal seamless LULC mapping and overcome the limitations of existing multimodal fusion methods, this study proposes a novel LULC mapping framework, called the multi-model high-order collaboration network (MHC-Net).

## Dataset
We have also developed the first public dataset, LuojiaSET-PolCR, which explicitly introduces PolSAR polarimetric scattering characteristics into cloud-contaminated optical satellite image reconstruction to advance research in this field.
Links to **[here](https://www.wenjuan.com/s/JnyMzq1/#)** download the data.
![image](https://github.com/RSIIPAC/CloudLULC/blob/main/Subsidiaries/location.png)

We divide all the patches into three subdatasets, namely, training set, validation set, testing, and write the division in a .csv file as:
```
1	SAR_S1/VH	 SAR_S1/VV    Opt_S2_cloudy	  ROIs_01_p_0001.tif
2	SAR_S1/VH	 SAR_S1/VV    Opt_S2_cloudy	  ROIs_02_p_0001.tif
3	SAR_S1/VH	 SAR_S1/VV    Opt_S2_cloudy	  ROIs_03_p_0001.tif
```
Here label is a number and 1 represents training set, 2 represents validation set and 3 represents testing set. 
Then build the file structure in your computer as the folder dataset shown.
```
./
+-- LuojiaSET-CloudLULC
    +--	SAR_S1
        +-- VH
        |   +-- patch_ROIs_01_name.tif
        |   +-- ...
        +-- VV
        |   +-- patch_ROIs_01_name.tif
        |   +-- ...
     +-- Opt_S2_cloudy
        |   +-- patch_ROIs_01_name.tif
        |   +-- ...
     +-- Opt_S2_clear
        |   +-- patch_ROIs_01_name.tif
        |   +-- ...
     +-- Label
        |   +-- patch_ROIs_01_name.tif
        |   +-- ...
```

## Contact
If you have any questions about this work please concat me. E-mail: panjun1215@whu.edu.cn, dd_xjg@whu.edu.cn
