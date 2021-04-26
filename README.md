# GIMPNotebooks
Notebooks for working with Greenland Ice Mapping Project (GIMP) data archived at NSIDC

## NSIDCLoginNotebook.ipynb
This notebook creates a cookie file and .netrc file with authentication information that GDAL based programs (e.g., other Notebooks in this repo and *QGIS*) can download /vsicurl links to allow remote access of data archive at NSDIC. The notebook contains full setup instructions. Users should view the notebook on github before trying to run.

The directions for setup are contained in the notebook, so its a good idea to read the github rendered notebook before proceeding.

## qgisRremoteNotebook.ipynb

This notebook has a search tool to search for *GIMP* products at NSIDC. Following the search, the result can automically be incorporated in a new *QGIS* project that accesses the data remotely. It can also group and save the data as *QGIS Layer Definition Files*, which allow subsets of the data to easily be imported into an existing *QGIS* project.

## GIMPSubsetterNotebook.ipynb

This notebook allows users to download subsets of [GIMP](https://nsidc.org/data/measures/gimp) image ([NSIDC-0723](https://nsidc.org/data/nsidc-0723)) and velocity ([NSIDC-481](https://nsidc.org/data/nsidc-0481), [0725](https://nsidc.org/data/nsidc-0725), [0727](https://nsidc.org/data/nsidc-0727), [0731](https://nsidc.org/data/nsidc-0731)) data. For the Sentinel based velocity mosaics (0725, 0727, 0731), the user can select a box on a map and select which components to be downloaded (vv, vx, vy, ex, ey, dT) and saved to a netCDF file. Once the download is complete, users can explore the data by interactively selecting points that are plotted as time series. In the case of the TSX products (NSDIC-0481), given their small size, the full product "box" is downloaded. Because of the sparse nature of these boxes, only the the products can for a single box can be downloaded at a time.
