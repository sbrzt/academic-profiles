# Formal Competency Questions

## C1
Provide a list of all articles authored by Yoyota Vuvuli over the last two years, ranked in a descending order by their citation counts.

```SPARQL
PREFIX tbox: <https://example.org/skg-if/extention/01/schema/>
PREFIX : <https://example.org/skg-if/extention/01/data/>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

SELECT ?title (YEAR(?issued_date) AS ?year) ?venue (GROUP_CONCAT(DISTINCT ?author; separator=", ") AS ?authors) (GROUP_CONCAT(DISTINCT ?affiliation; separator=", ") AS ?affiliations) (GROUP_CONCAT(DISTINCT ?topic; separator=", ") AS ?topics) ?doi (GROUP_CONCAT(DISTINCT CONCAT(?contributor, ": ", ?contribution_role); separator=", ") AS ?contribution_roles)
 ?citations ?downloads ?reproducibility_badge ?reproducibility_id ?reproducibility_score
WHERE {
    ?article a tbox:ScholarlyWork ;
        tbox:title ?title ;
        tbox:hasIdentifier [
            tbox:hasLiteralValue ?doi ;
            tbox:usesIdentifierScheme tbox:doi .
        ] ;
        tbox:realization [
            tbox:issued ?issued_date ;
            tbox:partOf [
                tbox:title ?venue .
            ]
        ] ;
        tbox:isRelatedToRoleInTime [
            tbox:withRole tbox:author ;
            tbox:relatesToOrganization [
                tbox:name ?affiliation .
            ] ;
            tbox:isHeldBy [
                tbox:name ?author .
            ] .
        ] ,
        [
            tbox:withContribution ?contribution_role ;
            tbox:isHeldBy [
                tbox:name ?contributor .
            ] .
        ] ;
        tbox:holdsBibliometricDataInTime [
            tbox:withBibliometricData [
                a tbox:SubjectTerm ;
                tbox:prefLabel ?topic .
            ]
        ] ,
        [
            tbox:withBibliometricData [
                tbox:hasMeasure tbox:publication-citation-count ;
                tbox:hasNumericvalue ?citations .
            ]
        ] ,
        [
            tbox:withBibliometricData [
                tbox:hasMeasure tbox:publication-download-count ;
                tbox:hasNumericvalue ?downloads .
            ]
        ] ,
        [
            tbox:withBibliometricData ?reproducibility .
        ] .

    ?reproducibility a tbox:CategorialBibliometricData ;
        tbox:prefLabel ?reproducibility_badge .
    
    OPTIONAL {
        ?reproducibility tbox:withinContext [
            tbox:hasIdentifier [
                tbox:hasLiteralValue ?reproducibility_id .
            ] .
        ] .
    }

    OPTIONAL {
        ?reproducibility tbox:withinContext [
            tbox:hasValue ?reproducibility_score .
        ] .
    }

    FILTER (
        ?issued_date >= "2023-01-01T00:00:00+00:00"^^xsd:dateTime 
        && 
        ?issued_date <= "2024-12-31T23:59:59+00:00"^^xsd:dateTime
    )
}
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
            tbox:hasContent ?narrative_content .
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
                tbox:hasMeasure tbox:publication-citation-count .
            ] ;
            tbox:description ?intuition ;
            tbox:wasGeneratedBy [
                tbox:used [
                    tbox:description ?data_used .
                ] ;
                tbox:description ?methodology ;
                tbox:wasAssociatedWith [
                    tbox:hasIdentifier [
                        tbox:hasLiteralValue ?code .
                    ] .
                ] .
            ] .
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

SELECT DISTINCT ?total_articles_published ?articles_in_environmental_science ?articles_in_machine_learning ?total_citations ?citations_in_environmental_science ?citations_in_machine_learning ?total_downloads
WHERE {

    :yoyota-vululi tbox:holdsBibliometricDataInTime [
        tbox:withBibliometricData [
            tbox:hasMeasure tbox:author-publication-count ;
            tbox:hasNumericValue ?total_articles_published .
        ] .
    ] ,
    [
        tbox:withBibliometricData [
            tbox:hasMeasure tbox:author-publication-count ;
            tbox:hasNumericValue ?articles_in_environmental_science .
        ] ;
        tbox:withinContext :environmental-science .
    ] ,
    [
        tbox:withBibliometricData [
            tbox:hasMeasure tbox:author-publication-count ;
            tbox:hasNumericValue ?articles_in_machine_learning .
        ] ;
        tbox:withinContext :machine-learning .
    ] ,
    [
        tbox:withBibliometricData [
            tbox:hasMeasure tbox:author-citation-count ;
            tbox:hasNumericValue ?total_citations .
        ] .
    ] ,
    [
        tbox:withBibliometricData [
            tbox:hasMeasure tbox:author-citation-count ;
            tbox:hasNumericValue ?citations_in_environmental_science .
        ] ;
        tbox:withinContext :environmental-science .
    ] ,
    [
        tbox:withBibliometricData [
            tbox:hasMeasure tbox:author-citation-count ;
            tbox:hasNumericValue ?citations_in_machine_learning .
        ] ;
        tbox:withinContext :machine-learning .
    ] ,
    [
        tbox:withBibliometricData [
            tbox:hasMeasure tbox:author-download-count ;
            tbox:hasNumericValue ?total_downloads .
        ] 
    ] .
}
```