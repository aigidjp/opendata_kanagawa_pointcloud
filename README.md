# Overview of 3D Point Cloud Data in Kanagawa

## Summary

This is 3D point cloud data obtained through aerial laser surveys conducted between FY2019 and FY2022.

## License

[Creative Commons Attribution 4.0 International  (CC-BY 4.0)](https://creativecommons.org/licenses/by/4.0/)

## Data

### About

This dataset consists of 3D point cloud data and related materials, including micro-topography representation maps, obtained through aerial laser surveys with a measurement density of 4 points per square meter or higher.

The horizontal datum is JGD2011 (Japan Geodetic Datum 2011), using the Plane Rectangular Coordinate System Zone IX, and the vertical datum is elevation above mean sea level of Tokyo Bay.

Since the 3D point cloud data were primarily acquired for forest resource analysis, data for urban areas and port zones without forest coverage are not included. In addition, data were not collected for national forests or areas near military bases where aircraft operation is restricted.

### Coordinate System

[EPSG:6677 (JGD2011 / Japan Plane Rectangular CS IX)](https://epsg.io/6677)

The Japanese Geodetic System Rectangular Plane Coordinate System is essential for local and regional mapping and surveying in Japan. Its division into zones, combined with the use of the Gauss-Krüger projection, ensures high accuracy in representing geographic positions.

Japan is divided into 19 zones, each with its own local coordinate system. Each zone has a different origin (reference point) from which positions are measured.

In this system, coordinates are expressed as an east-west (x-coordinate) and north-south (y-coordinate) distance from the origin of each zone. This allows for precise identification of locations on a map.

#### References

* [わかりやすい平面直角座標系（国土交通省国土地理院）](https://www.gsi.go.jp/sokuchikijun/jpc.html)
* [State Plane Coordinate System (National Geodetic Survey)](https://geodesy.noaa.gov/SPCS/)

### Grid System

The National Basic Map Grid system is used to divide and identify sections of Japan's National Basic Maps. It's based on the Japan Plane Rectangular Coordinate System, using distances (in meters) from the origin point to define grid sections. It differs from the standard regional mesh system, which uses latitude and longitude for division.

The grid system has five levels of map information: 50000, 5000, 2500, 1000, and 500. Each level has a specific naming convention for its grid sections. The grid code for each map section provides information about its location within the coordinate system.

#### References

- [国土基本図図郭とは｜図郭コードの読み方](https://club.informatix.co.jp/?p=1293)
- [United States National Grid (Federal Geographic Data Committee)](https://www.fgdc.gov/usng/)
- [Using the National Grid (Ordnance Survey)](https://www.ordnancesurvey.co.uk/documents/resources/guide-to-nationalgrid.pdf)

### Format

[LAS](https://www.ogc.org/standard/las/) is a standard file format for point cloud data. The distributed files are compressed in zip or 7z format.

#### References

- [LAS Specification 1.4 - R15 (ASPRS)](https://www.asprs.org/wp-content/uploads/2019/07/LAS_1_4_r15.pdf)

### Data acquisition area

The acquisition of point cloud data was conducted over multiple years, with each year targeting different areas.

| FY | Area |
| --- | --- |
| 2019 | Western Kanagawa |
| 2020 | Central Kanagawa and Sagamihara|
| 2020 | Sagamihara, Kanagawa |
| 2021 | Southern Yokohama, Shonan, and Yokosuka-Miura, Kanagawa |
| 2022 | Northern Yokohama and Kawasaki, Kanagawa|

### Data Types

| Type | Format | Description |
| --- | --- | --- |
| Original / Ground | LAS / TXT | Point cloud data obtained by laser profiling |
| Grid | CSV / MESH | Elevation data at regular intervals created based on ground data |
| Waterbody | TXT | Terrain data of a waterbody obtained by laser profiling |
| Contour | DXF | Contour data automatically generated from grid data |
| Ortho / RedReliefImage | TIFF / JPEG | Orthophoto and Red-relief-image data derived from aerial photographs and converted into orthographic projection |
| DEM / DCHM / DSM | CSV /TXT | DEM, DCHM, and DSM data obtained through laser profiling |

### Files

The point cloud data is divided into a large number of files correspondings to each grid of the National Basic Map Grid system, at the level of map information 500. The name of each file contains the grid code.

The datasets are available at `s3://kanagawa-pointcloud` bucket.

The object key consists of year (with sequence number), acquisition method, data type, zone number and grid codes.

- YEAR
  - year of data acquisition
- SEQUENCE
  - sequence number within the same acquisition year
- METHOD
  - LP
- TYPE
  - Original / Ground / Grid / Waterbody / Ortho / Contour / RedReliefImage / DEM / DCHM / DSM
- FORMAT
  - LAS / TXT / CSV / MESH / TIFF / JPEG / DXF
- ZONE
  - '09' : Kanagawa Prefecture
- GRID_CODE_50000
  - grid code of Map Information Level 50000
- GRID_CODE_5000
  - grid code of Map Information Level 5000


s3://kanagawa-pointcloud/**YEAR**/**SEQUENCE**/**METHOD**/**TYPE**/**FORMAT**/**ZONE**/**GRID_CODE_50000**/**GRID_CODE_5000**/**FILENAME**

***
