# utl_voronoi_diagram_on_a_shapefile_of_singapore
Voronoi diagram on a shapefile of Singapore and delimit the voronoi diagram with the boundaries of the map.  Keywords: sas sql join merge big data analytics macros oracle teradata mysql sas communities stackoverflow statistics artificial inteligence AI Python R Java Javascript WPS Matlab SPSS Scala Perl C C# Excel MS Access JSON graphics maps NLP natural language processing machine learning igraph DOSUBL DOW loop stackoverflow SAS community.  

    Voronoi diagram on a shapefile of Singapore and delimit the voronoi diagram with the boundaries of the map.

    for graphic outpt see
    https://tinyurl.com/ybcy3p4r
    https://github.com/rogerjdeangelis/utl_voronoi_diagram_on_a_shapefile_of_singapore/blob/master/utl_voronoi_diagram_on_a_shapefile_of_singapore2.pdf
    https://tinyurl.com/y7tpgel3
    https://github.com/rogerjdeangelis/utl_voronoi_diagram_on_a_shapefile_of_singapore/blob/master/utl_voronoi_diagram_on_a_shapefile_of_singapore1.pdf

    goithb
    https://github.com/rogerjdeangelis/utl_voronoi_diagram_on_a_shapefile_of_singapore

    http://mathworld.wolfram.com/VoronoiDiagram.html

    The partitioning of a plane with n points into convex polygons such that each polygon contains
    exactly one generating point and every point in a given polygon is closer to its
    generating point than to any other. A Voronoi diagram is sometimes also known as a Dirichlet
    tessellation. The cells are called Dirichlet regions, Thiessen polytopes, or Voronoi polygons.

    A particularly notable use of a Voronoi diagram was
    the analysis of the 1854 cholera epidemic in London, in which physician John Snow
    determined a strong correlation of deaths with proximity to a
    particular (and infected) water pump on Broad Street.

    In mathematics, a Voronoi diagram is a partitioning of a plane into regions based on
    distance to points in a specific subset of the plane. ... These regions are called Voronoi cells.
    The Voronoi diagram of a set of points is dual to its Delaunay triangulation.

    They find widespread applications in areas such as computer graphics, epidemiology,
    geophysics, and meteorology.
    see
    https://stackoverflow.com/questions/50979999/delimit-voronoi-diagram-with-map-boundary-in-r

    Robert Hijmans profile
    https://stackoverflow.com/users/635245/robert-hijmans


    INPUT
    =====

      Given these lat and long coords

      Outline coords
      coords <- data.frame(Lat=c(1.29370,1.37640,1.25600,1.38370,1.38240,1.31910),
      Long=c(103.8125,103.8492,103.6790,103.8860,103.7603,103.8191));

      Singapore Shapefile
      sg <- getData(country="SGP", level=0);

      Generate convex hull and convex plogons within this boundary using Voronoi mathematics and
      overlay Signgapore

     1.40 +
          |              *
          |            *   *
          |           *      *
          |          *         *
     1.35 +         *          *
          |        *           *
     AAAA |       *            *
          |      *             *
          |     *              *
     1.30 +    *               *
          |    *               *
          |     *              *
          |      *        *   *
          |       *   *     *
     1.25 +         *
          -+-+----------+----------+
            103.7      103.8    103.9

                      LON


    PROCESS (all the code)
    =======================

    %utl_submit_wps64('
    libname sd1 "d:/sd1";
    options set=R_HOME "C:/Program Files/R/R-3.3.2";
    libname wrk  sas7bdat "%sysfunc(pathname(work))";
    libname hlp  sas7bdat "C:\Progra~1\SASHome\SASFoundation\9.4\core\sashelp";
    proc r;
    submit;
      source("C:/Program Files/R/R-3.3.2/etc/Rprofile.site", echo=T);
      library(haven);
      library(dismo);
      library(rgeos);
      have<-as.data.frame(read_sas("d:/sd1/have.sas7bdat"));
      head(have);
      sg <- getData(country="SGP", level=0);
      v <- voronoi(have[, c("LON", "LAT")], ext=extent(sg)+.1);
      sgv <- v * sg;
      pdf("d:/pdf/utl_voronoi_diagram_on_a_shapefile_of_singapore1.pdf");
      plot(sgv);
      pdf();
      g <- gmap(sg, lonlat=TRUE, scale=2);
      pdf("d:/pdf/utl_voronoi_diagram_on_a_shapefile_of_singapore2.pdf");
      plot(g, interpolate=TRUE);
      lines(sgv, col="red");
      pdf();
    endsubmit;
    import r=have data=wantr;
    run;quit;
    ');


    OUTPUT
    ======

    https://tinyurl.com/ybcy3p4r
    https://tinyurl.com/y7tpgel3

    *                _              _       _
     _ __ ___   __ _| | _____    __| | __ _| |_ __ _
    | '_ ` _ \ / _` | |/ / _ \  / _` |/ _` | __/ _` |
    | | | | | | (_| |   <  __/ | (_| | (_| | || (_| |
    |_| |_| |_|\__,_|_|\_\___|  \__,_|\__,_|\__\__,_|

    ;

    options validvarname=upcase;
    libname sd1 "d:/sd1";
    data sd1.have;
     input lat lon;
    cards4;
    1.29370 103.8125
    1.37640 103.8492
    1.25600 103.6790
    1.38370 103.8860
    1.38240 103.7603
    1.31910 103.8191
    ;;;;
    run;quit;

    *          _       _   _
     ___  ___ | |_   _| |_(_) ___  _ __
    / __|/ _ \| | | | | __| |/ _ \| '_ \
    \__ \ (_) | | |_| | |_| | (_) | | | |
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|

    ;

    see process


