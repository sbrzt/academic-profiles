# Formal Competency Questions

## C1
Provide a list of all articles authored by Yoyota Vuvuli over the last two years, ranked in a descending order by their citation counts.

```SPARQL
PREFIX tbox: <https://example.org/skg-if/extention/01/schema/>
PREFIX : <https://example.org/skg-if/extention/01/data/>
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

    ?article a tbox:ScholarlyWork ;
        tbox:title ?title ;
        tbox:hasIdentifier [
            tbox:hasLiteralValue ?doi ;
            tbox:usesIdentifierScheme tbox:doi 
        ] ;
        tbox:realization [
            tbox:issued ?issued_date ;
            tbox:partOf [
                tbox:title ?venue 
            ]
        ] ;
        tbox:isRelatedToRoleInTime [
            tbox:withRole tbox:author ;
            tbox:relatesToOrganization [
                tbox:name ?affiliation 
            ] ;
            tbox:isHeldBy [
                tbox:name ?author 
            ] 
        ] ;
        tbox:holdsBibliometricDataInTime [
            tbox:withBibliometricData [
                tbox:hasMeasure tbox:publication-citation-count ;
                tbox:hasNumericValue ?citations 
            ]
        ] ,
        [
            tbox:withBibliometricData [
                tbox:hasMeasure tbox:publication-download-count ;
                tbox:hasNumericValue ?downloads 
            ]
        ] .

    {
        SELECT DISTINCT
            ?article
            (GROUP_CONCAT(DISTINCT ?topic; separator=", ") AS ?topics)
        WHERE
            {
                ?article a tbox:ScholarlyWork ;
                    tbox:holdsBibliometricDataInTime [
                        tbox:withBibliometricData [
                            a tbox:SubjectTerm ;
                            tbox:prefLabel ?topic
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
                        ?article a tbox:ScholarlyWork ;
                            tbox:isRelatedToRoleInTime [
                                tbox:withContribution [
                                    tbox:prefLabel ?contribution_role
                                ] ;
                                tbox:isHeldBy [
                                    tbox:name ?contributor 
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
        ?article tbox:holdsBibliometricDataInTime [
            tbox:withBibliometricData [
                a tbox:CategorialBibliometricData ;
                tbox:prefLabel ?reproducibility_badge
            ]
        ] 
    }

    OPTIONAL {
        ?article tbox:holdsBibliometricDataInTime [
            tbox:withBibliometricData [
                a tbox:CategorialBibliometricData ;
                tbox:withinContext [
                    tbox:hasIdentifier [
                            tbox:hasLiteralValue ?reproducibility_doi ;
                            tbox:usesIdentifierScheme tbox:doi 
                    ] 
                ]
            ]
        ] 
    }

    OPTIONAL {
        ?article tbox:holdsBibliometricDataInTime [
            tbox:withBibliometricData [
                a tbox:CategorialBibliometricData ;
                tbox:withinContext [
                    tbox:hasValue ?reproducibility_score
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
PREFIX tbox: <https://example.org/skg-if/extention/01/schema/>
PREFIX : <https://example.org/skg-if/extention/01/data/>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

SELECT DISTINCT ?narrative_title ?narrative_content
WHERE {
    :john-doe tbox:submits [
        tbox:hasPart [
            tbox:title ?narrative_title ;
            tbox:hasContent ?narrative_content 
        ]
    ]
}

```

***

## C3

Provide information about the article-level indicator called "Citations".

```SPARQL
PREFIX tbox: <https://example.org/skg-if/extention/01/schema/>
PREFIX : <https://example.org/skg-if/extention/01/data/>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

SELECT DISTINCT ?intuition ?data_used ?methodology ?related_literature ?code
WHERE {
    
    ?article a tbox:ScholarlyWork ;
        tbox:holdsBibliometricDataInTime [
            tbox:withBibliometricData [
                tbox:hasMeasure tbox:publication-citation-count 
            ] ;
            tbox:description ?intuition ;
            tbox:wasGeneratedBy [
                tbox:used [
                    tbox:description ?data_used 
                ] ;
                tbox:description ?methodology ;
                tbox:wasAssociatedWith [
                    tbox:hasIdentifier [
                        tbox:hasLiteralValue ?code 
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
PREFIX tbox: <https://example.org/skg-if/extention/01/schema/>
PREFIX : <https://example.org/skg-if/extention/01/data/>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

SELECT DISTINCT ?measure ?value ?subject
WHERE {

    ?researcher tbox:name ?name ;
        tbox:holdsBibliometricDataInTime ?bibliometric_data_in_time .
    ?bibliometric_data_in_time tbox:withBibliometricData ?bibliometric_data .
    ?bibliometric_data tbox:hasMeasure ?measure ;
        tbox:hasNumericValue ?value .

    OPTIONAL {
        ?bibliometric_data_in_time tbox:withinContext ?subject_term .
        ?subject_term a tbox:SubjectTerm ;
            tbox:prefLabel ?subject .
    }

    FILTER (?name = "Yoyota Vuvuli")
}
```