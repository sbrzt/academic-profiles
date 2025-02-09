# Formal Competency Questions

## C1
Provide a list of all articles authored by Yoyota Vuvuli over the last two years, ranked in a descending order by their citation counts.

```SPARQL
PREFIX bido: <http://purl.org/spar/bido/>
PREFIX c4o: <http://purl.org/spar/c4o/>
PREFIX cito: <http://purl.org/spar/cito/>
PREFIX datacite: <http://purl.org/spar/datacite/>
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX fabio: <http://purl.org/spar/fabio/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX frapo: <http://purl.org/cerif/frapo/>
PREFIX frbr: <http://purl.org/vocab/frbr/core#>
PREFIX literal: <http://purl.org/spar/literal/>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX pro: <http://purl.org/spar/pro/>
PREFIX prov: <http://www.w3.org/ns/prov#>
PREFIX scoro: <http://purl.org/spar/scoro/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX tvc: <http://purl.org/spar/tvc/>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

SELECT DISTINCT

    ?title 
    (YEAR(?issued_date) AS ?year) 
    ?venue 
    ?doi
    (GROUP_CONCAT(DISTINCT ?author; separator=", ") AS ?authors)
    (GROUP_CONCAT(DISTINCT ?affiliation; separator=", ") AS ?affiliations)
    ?multiple_contribution
    ?topics
    ?citations
    ?downloads
    ?reproducibility_badge
    ?reproducibility_doi
    ?reproducibility_score

WHERE {

    ?article a fabio:ScholarlyWork ;
        dcterms:title ?title ;
        datacite:hasIdentifier [
            literal:hasLiteralValue ?doi ;
            datacite:usesIdentifierScheme datacite:doi 
        ] ;
        frbr:realization [
            dcterms:issued ?issued_date ;
            frbr:partOf [
                dcterms:title ?venue 
            ]
        ] ;
        pro:isRelatedToRoleInTime [
            pro:withRole pro:author ;
            pro:relatesToOrganization [
                foaf:name ?affiliation 
            ] ;
            pro:isHeldBy [
                foaf:name ?author 
            ] 
        ] ;
        bido:holdsBibliometricDataInTime [
            bido:withBibliometricData [
                bido:hasMeasure bido:publication-citation-count ;
                bido:hasNumericValue ?citations 
            ]
        ] ,
        [
            bido:withBibliometricData [
                bido:hasMeasure bido:publication-download-count ;
                bido:hasNumericValue ?downloads 
            ]
        ] .

    {
        SELECT DISTINCT
            ?article
            (GROUP_CONCAT(DISTINCT ?topic; separator=", ") AS ?topics)
        WHERE
            {
                ?article a fabio:ScholarlyWork ;
                    bido:holdsBibliometricDataInTime [
                        bido:withBibliometricData [
                            a fabio:SubjectTerm ;
                            skos:prefLabel ?topic
                        ]
                    ]
            }
        GROUP BY ?article
    }
    
    {
        SELECT 
            ?article
            (GROUP_CONCAT(DISTINCT ?full_contribution; separator="; ") AS ?multiple_contribution)
        WHERE 
            {
                {
                    SELECT DISTINCT
                        ?article
                        ?contributor
                        (GROUP_CONCAT(DISTINCT ?contribution_role; separator=", ") AS ?contribution_roles)
                        
                    WHERE {
                        ?article a fabio:ScholarlyWork ;
                            pro:isRelatedToRoleInTime [
                                scoro:withContribution [
                                    skos:prefLabel ?contribution_role
                                ] ;
                                pro:isHeldBy [
                                    foaf:name ?contributor 
                                ] 
                            ] .
                    }
                    GROUP BY ?contributor ?article
                }

                BIND (CONCAT(?contributor, ": ", ?contribution_roles) AS ?full_contribution)
            }
        GROUP BY ?article
    }

    OPTIONAL {
        ?article bido:holdsBibliometricDataInTime [
            bido:withBibliometricData [
                a bido:CategorialBibliometricData ;
                skos:prefLabel ?reproducibility_badge
            ]
        ] 
    }

    OPTIONAL {
        ?article bido:holdsBibliometricDataInTime [
            bido:withBibliometricData [
                a bido:CategorialBibliometricData ;
                tvc:withinContext [
                    datacite:hasIdentifier [
                            literal:hasLiteralValue ?reproducibility_doi ;
                            datacite:usesIdentifierScheme datacite:doi 
                    ] 
                ]
            ]
        ] 
    }

    OPTIONAL {
        ?article bido:holdsBibliometricDataInTime [
            bido:withBibliometricData [
                a bido:CategorialBibliometricData ;
                tvc:withinContext [
                    prov:value ?reproducibility_score
                ]
            ]
        ] 
    }
    

    FILTER (
        ?issued_date >= "2023-01-01T00:00:00+00:00"^^xsd:dateTime 
        && 
        ?issued_date <= "2024-12-31T23:59:59+00:00"^^xsd:dateTime
    )
}
GROUP BY ?article
ORDER BY DESC(?citations)
```

***

## C2

Provide all narratives included in John Doe's narrative CV.

```SPARQL
PREFIX bido: <http://purl.org/spar/bido/>
PREFIX c4o: <http://purl.org/spar/c4o/>
PREFIX cito: <http://purl.org/spar/cito/>
PREFIX datacite: <http://purl.org/spar/datacite/>
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX fabio: <http://purl.org/spar/fabio/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX frapo: <http://purl.org/cerif/frapo/>
PREFIX frbr: <http://purl.org/vocab/frbr/core#>
PREFIX literal: <http://purl.org/spar/literal/>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX pro: <http://purl.org/spar/pro/>
PREFIX prov: <http://www.w3.org/ns/prov#>
PREFIX scoro: <http://purl.org/spar/scoro/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX tvc: <http://purl.org/spar/tvc/>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

SELECT DISTINCT ?narrative_title ?narrative_content
WHERE {
    ?researcher foaf:name ?name ;
        frapo:submits [
            frbr:part [
                dcterms:title ?narrative_title ;
                c4o:hasContent ?narrative_content 
            ]
        ]

    FILTER(?name = "John Doe")
}


```

***

## C3

Provide information about the article-level indicator called "Citations".

```SPARQL
PREFIX bido: <http://purl.org/spar/bido/>
PREFIX c4o: <http://purl.org/spar/c4o/>
PREFIX cito: <http://purl.org/spar/cito/>
PREFIX datacite: <http://purl.org/spar/datacite/>
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX fabio: <http://purl.org/spar/fabio/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX frapo: <http://purl.org/cerif/frapo/>
PREFIX frbr: <http://purl.org/vocab/frbr/core#>
PREFIX literal: <http://purl.org/spar/literal/>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX pro: <http://purl.org/spar/pro/>
PREFIX prov: <http://www.w3.org/ns/prov#>
PREFIX scoro: <http://purl.org/spar/scoro/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX tvc: <http://purl.org/spar/tvc/>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

SELECT DISTINCT ?intuition ?data_used ?methodology ?related_literature ?code
WHERE {
    
    ?article a fabio:ScholarlyWork ;
        bido:holdsBibliometricDataInTime [
            bido:withBibliometricData [
                bido:hasMeasure bido:publication-citation-count 
            ] ;
            dcterms:description ?intuition ;
            prov:wasGeneratedBy [
                prov:used [
                    dcterms:description ?data_used 
                ] ;
                dcterms:description ?methodology ;
                prov:wasAssociatedWith [
                    datacite:hasIdentifier [
                        literal:hasLiteralValue ?code 
                    ] 
                ] 
            ] 
        ] .
}
```

***

## C4

Provide the values of all researcher-level indicators for Yoyota Vuvuli.

```SPARQL
PREFIX bido: <http://purl.org/spar/bido/>
PREFIX c4o: <http://purl.org/spar/c4o/>
PREFIX cito: <http://purl.org/spar/cito/>
PREFIX datacite: <http://purl.org/spar/datacite/>
PREFIX dcterms: <http://purl.org/dc/terms/>
PREFIX fabio: <http://purl.org/spar/fabio/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX frapo: <http://purl.org/cerif/frapo/>
PREFIX frbr: <http://purl.org/vocab/frbr/core#>
PREFIX literal: <http://purl.org/spar/literal/>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX pro: <http://purl.org/spar/pro/>
PREFIX prov: <http://www.w3.org/ns/prov#>
PREFIX scoro: <http://purl.org/spar/scoro/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX tvc: <http://purl.org/spar/tvc/>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

SELECT DISTINCT ?measure ?value ?subject
WHERE {

    ?researcher foaf:name ?name ;
        bido:holdsBibliometricDataInTime ?bibliometric_data_in_time .
    ?bibliometric_data_in_time bido:withBibliometricData ?bibliometric_data .
    ?bibliometric_data bido:hasMeasure ?measure ;
        bido:hasNumericValue ?value .

    OPTIONAL {
        ?bibliometric_data_in_time tvc:withinContext ?subject_term .
        ?subject_term a fabio:SubjectTerm ;
            skos:prefLabel ?subject .
    }

    FILTER (?name = "Yoyota Vuvuli")
}
```