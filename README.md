# minnowTraits
Using trait segmentation to understand minnow trait evolution across an ecological gradient

## Minnow image selection
Images were previously segmented using machine learning (<a href="https://github.com/hdr-bgnn/BGNN-trait-segmentation">BGNN trait segementation</a>).

We used the combined violation tables merged with the image quality metadata and image metadata (<a href="https://drive.google.com/file/d/1rrXSM77S7iduVbNogI-_0bucrpqZdzvM/view?usp=sharing">fish.meta.qual.tax.csv</a>), this was done using this <a href=
"https://drive.google.com/file/d/13o_ComN2cNaZxT_gqjqFi6_If0FFavBQ/view?usp=sharing">R code</a>. See the <a href="https://drive.google.com/file/d/1mtSAuxQKvctaUp4ksPPGYpsvNzsoypc9/view?usp=sharing">Batch Info</a> for how these violation tables were made and <a href="https://drive.google.com/file/d/1H0AQSLY3-Akr4DFa2zYo8JJ_N_ET0I7m/view?usp=sharing">CSV Info</a> for information about the column headers.

The minnow.selected.csv file was derived from the fish.meta.qual.tax.csv, and filtered on institution.y == “INHS”, specimen.viewing == “left”, as well as only one “blob” for the head and the eye (CC.HEAD == 1, CC.EYE == 1). 


### 1- Creation of minnow.images.for.segmenting.csv

R code (Minnows.R) was used to filter out high quality, minnow images using the Image_Quality_Metadata_v1_202111206_151204.csv matching the following criteria:

List of criteria chosen :

* family == "Cyprinidae" 
* specimen_viewing == "left" 
* straight_curved == "straight" 
* brightness == "normal" 
* color_issues == "none" 
* has_ruler == "True" 
* if_overlapping == "False" 
* if_focus == "True"
* if_missing_parts == "False"
* if_parts_visible == "True"
* fins_folded_oddly == "False"
* at least 10 images per species

The resulting dataset hs 65 species and 10145 images.

We ignored if_background_uniform == "True" because it reduced the sample size too much (3268 records)

The resulting dataset was then merged with the Image_Metadata_v1_20211206_151152.csv.
