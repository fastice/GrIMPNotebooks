## Key Features
Several features of these classes are useful for working with the GRiMP data as described below.

### Cloud Optimized Geotiffs
Much of the functionality described here relies on the use of Cloud-optimized Geotiffs ([COGs](https://developers.planet.com/planetschool/an-introduction-to-cloud-optimized-geotiffs-cogs-part-1-overview/)) for GriMP products, which have the following properties:
    
- The header with information about how the data are organized is all located at the beginning of the file. As a result, a result a single read provides all of the information about how the data are organized in the file. In some tiffs this information is distributed throughout the file, requiring many read operations to retrieve all of the metadata.
- The data are tiled (i.e., stored as a series of blocks like a checkerboard) rather than as a line-by-line raster. The tiling facilitates faster access to limited subsets. For example, to read a 50-by-50 km region from a Greeland mosaic, only a few tiles that cover that region need to be downloaded. By contrast, with conventional rastering, a 50km-by-1500km (~width of Greenland mosaics) would have to read (up to 30x more data) and then cropped to the desired width of 50km. 
- A consistent set of overview images (pyramids) are stored with the data, allowing low-resolution images to be quickly extracted to create figures where the full resolution is not required (e.g., for inset figures).


### Built on Xarray
[*Xarray*](https://docs.xarray.dev/en/stable/) is a powerful python tool that bundles metadata with data stored in NumPy arrays. While extremely powerful, it can be cumbersome for novice users. The classes described below are designed so that users can take advantage of the full functionality of Xarray, or bypass it entirely and access the data using either as [numpy](https://numpy.org) arrays or methods that perform tasks commonly applied to the data (interpolation, basic statistics, etc).

### Dask
[Dask](https://dask.org) is a program for applying parallel operations using Xarray, NumPy, and other libraries.  Dask functionality is included implicitly in these libraries as well as the classes described below. It builds on the lazy-open capabilities in that it can operate on the metadata and cue up several complex operations before actual data download, providing the advantages of parallelism in a way that is transparent to the user.

### Local and Remote Subsetting
After one of the classes described below performs a lazy open (e.g., a Greenland-wide map),  often the next task is to apply a subsetting (cropping) operation to limit access to only the region of interest. All subsetting operations are non-destructive with respect to the full data set, so multiple subsetting operations can be applied in series. 

After a subset is created, it initially retains its lazy-open status, which in many cases is a convenient way to work. For many operations, the data will automatically be downloaded as needed (e.g., for a plot). But if the data are used multiple times, it is better to explicitly download the data to avoid multiple downloads of the same data, which can greatly slow operations. In some cases, the system cache will retain the data and void repeat downloading, but large datasets can cause the cache to quickly be flushed and trigger redundant downloads. If there is sufficient memory, multiple downloads can be avoided by explicitly downloading the data to local memory as described below.

### Subsets Can Be Saved For Later Use

Subsets can be written to netCDF files and re-read for later use.