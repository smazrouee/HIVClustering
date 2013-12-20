HIVClustering
-------------

A Python 3 library that makes inferences on HIV-1 transmission networks.
To install

    sudo python3 setup.py install

Dependencies
------------

1). The low level HyPhy Python library. 
     
Clone the HyPhy repo <git://github.com/veg/hyphy.git>

    cd [hyphy]/src/lib
    sudo python3 setup.py install
    
2). The higher level Python-HyPhy interface (hppy)

Clone the hppy repo <git://github.com/nlhepler/hppy.git>

    cd [hppy]
    sudo python3 setup.py install

    
USAGE
-----
    usage: hivnetworkcsv [-h] [-i INPUT] [-u UDS] [-d DOT] [-c CLUSTER]
                         [-t THRESHOLD] [-e EDI] [-z OLD_EDI] [-f FORMAT]
                         [-x EXCLUDE] [-r RESISTANCE] [-p PARSER] [-a ATTRIBUTES]
                         [-j] [-k FILTER] [-s SEQUENCES] [-n {remove,report}]

    Read filenames.

    optional arguments:
      -h, --help            show this help message and exit
      -i INPUT, --input INPUT
                            Input CSV file with inferred genetic links (or stdin
                            if omitted). Must be a CSV file with three columns:
                            ID1,ID2,distance.
      -u UDS, --uds UDS     Input CSV file with UDS data. Must be a CSV file with
                            three columns: ID1,ID2,distance.
      -d DOT, --dot DOT     Output DOT file for GraphViz (or stdout if omitted)
      -c CLUSTER, --cluster CLUSTER
                            Output a CSV file with cluster assignments for each
                            sequence
      -t THRESHOLD, --threshold THRESHOLD
                            Only count edges where the distance is less than this
                            threshold
      -e EDI, --edi EDI     A .json file with clinical information
      -z OLD_EDI, --old_edi OLD_EDI
                            A .csv file with legacy EDI dates
      -f FORMAT, --format FORMAT
                            Sequence ID format. One of AEH (ID | sample_date |
                            otherfiels default), LANL (e.g. B_HXB2_K03455_1983 :
                            subtype_country_id_year -- could have more fields),
                            regexp (match a regular expression, use the first
                            group as the ID), or plain (treat as sequence ID only,
                            no meta)
      -x EXCLUDE, --exclude EXCLUDE
                            Exclude any sequence which belongs to a cluster
                            containing a "reference" strain, defined by the year
                            of isolation. The value of this argument is an integer
                            year (e.g. 1983) so that any sequence isolated in or
                            before that year (e.g. <=1983) is considered to be a
                            lab strain. This option makes sense for LANL or AEH
                            data.
      -r RESISTANCE, --resistance RESISTANCE
                            Load a JSON file with resistance annotation by
                            sequence
      -p PARSER, --parser PARSER
                            The reg.exp pattern to split up sequence ids; only
                            used if format is regexp
      -a ATTRIBUTES, --attributes ATTRIBUTES
                            Load a CSV file with optional node attributes
      -j, --json            Output the network report as a JSON object
      -k FILTER, --filter FILTER
                            Only return clusters with ids listed by a newline
                            separated supplied file.
      -s SEQUENCES, --sequences SEQUENCES
                            Provide the MSA with sequences which were used to make
                            the distance file.
      -n {remove,report}, --edge_filtering {remove,report}
                            Compute edge support and mark edges for removal using
                            sequence-based triangle tests (requires the -s
                            argument) and either only report them or remove the
                            edges before doing other analyses

