# GIMPNotebooks
Notebooks for working with Greenland Ice Mapping Project (GIMP) data archived at NSIDC

## NSIDCLoginNotebook.ipynb
This notebook creates a cookie file and .netrc file with authentication information that GDAL based programs (e.g., other Notebooks in this repo and *QGIS*) can download /vsicurl links to allow remote access of data archive at NSDIC. The notebook contains full setup instructions. Users should view the notebook on github before trying to run.

The directions for setup are contained in the notebook, so its a good idea to read the github rendered notebook before proceeding.

## qgisRremoteNotebook.ipynb

This notebook has a search tool to search for *GIMP* products at NSIDC. Following the search, the result can automically be incorporated in a new *QGIS* project that accesses the data remotely. It can also group and save the data as *QGIS Layer Definition Files*, which allow subsets of the data to easily be imported into an existing *QGIS* project.