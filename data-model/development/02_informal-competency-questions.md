# Informal Competency Questions

## CQ_01

### Identifier
C1

### Question
Provide a list of all articles authored by Yoyota Vuvuli over the last two years, ranked in a descending order by their citation counts.

### Outcome
List of articles from Yoyota Vuvuli that meets the determined criteria, including a selection of bibliographic metadata.

### Example
articles_metadata = [
    {
        "title": "Enhancing Sustainable Agriculture through AI-Driven Soil Monitoring",
        "year": 2024,
        "venue": "Journal of Environmental Informatics",
        "authors": ["Yoyota Vuvuli", "Ahmed El-Zein", "Clara Green"],
        "affiliations": ["University of Narnia", "University of Narnia", "University of Narnia"],
        "fields_topics": ["Environmental Science", "Machine Learning", "Precision Agriculture"],
        "doi": "10.1234/envinf.2022.001",
        "contribution_roles": {
            "Yoyota Vuvuli": ["Conceptualization", "Methodology", "Writing (Lead Author)"],
            "Ahmed El-Zein": ["Data Analysis", "Software Development"],
            "Clara Green": ["Fieldwork", "Writing (Review & Editing)"]
        },
        "indicators": {
            "citations": 34,
            "downloads": 1200,
            "reproducibility_badge": "Data Open",
            "reproducibility_doi": "10.1234/agri2022data"
        }
    },
    {
        "title": "Towards a Comprehensive Ontology for Climate Data Sharing",
        "year": 2023,
        "venue": "Data Science for Climate Change",
        "authors": ["Yoyota Vuvuli", "Marie Dupont", "Hiroshi Nakamura"],
        "affiliations": ["University of Narnia", "University of Narnia", "University of Narnia"],
        "fields_topics": ["Environmental Science", "Data Science"],
        "doi": "10.9101/dscc.2021.002",
        "contribution_roles": {
            "Yoyota Vuvuli": ["Conceptualization", "Ontology Design", "Writing (Lead Author)"],
            "Marie Dupont": ["Data Integration", "Writing (Review)"],
            "Hiroshi Nakamura": ["Technical Infrastructure", "Validation"]
        },
        "indicators": {
            "citations": 18,
            "downloads": 950,
            "reproducibility_badge": "FAIR Data",
            "reproducibility_score": "85%"
        }
    }
]

### Depends on
Example 1

---

## CQ_02

### Identifier
C2

### Question
Provide all narratives included in John Doe's narrative CV.

### Outcome
List of narrative descriptions and John Doe's answers formated in JSON. 

### Example
narratives_from_cv = {
    "personal_statement": "I am a passionate and driven materials scientist dedicated to advancing sustainable solutions to global environmental challenges. My research focuses on the development of biodegradable polymers, aiming to reduce plastic waste and its impact on ecosystems. With over a decade of experience in academic and collaborative industry projects, I have cultivated a multidisciplinary approach, integrating chemistry, materials science, and environmental studies to drive innovation in sustainable materials. Throughout my career, I have been committed to fostering an inclusive and collaborative research environment. By mentoring early-career researchers, supervising diverse teams, and organizing training programs, I have supported others in achieving their potential while ensuring knowledge transfer across generations of scientists. Beyond my research contributions, I actively engage with the wider scientific and public communities to amplify the impact of my work. Whether through advising policymakers on sustainable packaging legislation or participating in outreach programs to inspire young minds, I strive to bridge the gap between science and society.",
    "Contributions to General Knowledge": "I have dedicated my career to advancing the understanding of sustainable materials science, focusing on the development of biodegradable polymers for packaging applications. My work has led to the publication of 25 peer-reviewed journal articles, including high-impact papers in Nature Materials and Advanced Functional Materials. I led the “Sustainable Polymers Initiative,” a collaborative research project funded by the European Research Council, which developed a novel polymer blend with 50% lower environmental impact compared to traditional plastics. This research has been widely cited and has attracted industrial interest, leading to a joint patent with GreenPack Ltd. Supervising a diverse group of PhD students and postdoctoral researchers, I have fostered innovation and collaboration, resulting in four students winning national awards for their research excellence.",
    "Contributions to the Development of Individuals": "I am deeply committed to mentoring and supporting the next generation of researchers. Over the past five years, I have served as a mentor for the Royal Society’s “Future Leaders Program,” guiding early-career scientists in grant writing, career development, and balancing academic and personal responsibilities. I have organized annual training workshops on advanced polymer synthesis techniques, attracting participants from academic and industrial backgrounds. These workshops have been instrumental in equipping attendees with practical skills and fostering industry-academia collaborations. Additionally, I co-developed an undergraduate internship program within my department, which has provided hands-on research opportunities to over 30 students, many of whom have progressed to postgraduate studies.",
    "Contributions to the Wider Research Community": "As an advocate for open science, I have chaired the University of Narnia’s Open Access Committee, increasing departmental compliance with open data policies from 60% to 90% over three years. I have been an active member of the editorial boards of Green Chemistry and Journal of Polymer Science, ensuring rigorous peer review standards while promoting the dissemination of innovative research. To strengthen international collaboration, I co-founded the “Global Polymer Network,” a forum connecting over 300 researchers worldwide to share best practices and emerging trends in sustainable materials science.",
    "Contributions to Society": "My research has directly contributed to addressing global environmental challenges. The biodegradable polymer developed in the Sustainable Polymers Initiative is now being scaled up by GreenPack Ltd., with the potential to replace traditional plastics in 20% of European food packaging markets by 2030. To raise public awareness, I have participated in science communication initiatives such as the BBC series Future Materials, explaining the role of sustainable materials in tackling climate change. I also contribute regularly to outreach programs in local schools, inspiring young students to pursue careers in STEM fields. In 2022, I collaborated with policymakers to draft recommendations for sustainable packaging legislation, which influenced the European Union’s “Green Materials Directive."
}

### Depends on
Example 2

---

## CQ_03

### Identifier
C3

### Question
Provide information about the article-level indicator called "Citations".

### Outcome
A JSON including all metadata kept by the academic profile platform for this indicator.

### Example
indicator_description = {
    "Citations": {
        "intuition": "The total number of citations received by the article of interest.",
        "data_used": "Citations and article metadata required to calculate the particular indicator are gathered by the OpenAIRE Graph v9.0.0.",
        "methodology": "All citations from other articles pointing to the article of interest were counted.",
        "related_literature": "N/A",
        "code": "https://github.com/athenarc/Bip-Ranker"
    }
}

### Depends on
Example 1

---

## CQ_04

### Identifier
C4

### Question
Provide the values of all researcher-level indicators for Yoyota Vuvuli.

### Outcome
A JSON including all researcher-level indicators provided by the academic profile platform along with the respective values for the respective researcher.

### Example
researcher_indicators = {
    "total_articles_published": 4,
    "articles_in_environmental_science": 2,
    "articles_in_machine_learning": 2,
    "total_citations": 124,
    "citations_in_environmental_science": 52,
    "citations_in_machine_learning": 106,
    "total_downloads": 5600
}

### Depends on
Example 1