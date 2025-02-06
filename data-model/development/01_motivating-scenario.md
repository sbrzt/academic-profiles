# Motivating Scenario

## Name
Academic profiles for researchers

## Description
Academic profiles, often referred to as academic CVs, are comprehensive representations of an individual’s researcher's career detailing related key aspects including their publications, funded projects, research interests, teaching experience, professional affiliations, awards and contributions to the research and academic community. Academic profiles are typically used to showcase expertise, support applications for grants, positions, or collaborations, and facilitate networking within academic and professional circles. These profiles may also include various article-level or researcher-level indicators, like citation counts.

## Examples

### Example 1
Yoyota Vuvuli has created an academic profile on a platform including all her scientific articles along with their basic bibliographic metadata (year, title, venue, author list, etc). Additional article metadata, like the related fields/topics, contribution roles, and affiliation, is also provided for some of the articles. Her profile includes the values for article-level indicators for impact (e.g., citation counts), usage (e.g., downloads), reproducibility (e.g., specially designed badges), and other properties of interest. A couple of researcher level indicators, like the number of articles published in general or in particular domains of interest, are also provided. 

Researcher Profile of Yoyota Vuvuli

Researcher-Level Indicators
- Total Articles Published: 4
- Articles in Environmental Science: 2
- Articles in Machine Learning: 2
- Total Citations: 124
- Citations in Environmental Science: 52
- Citations in Machine Learning: 106
- Total Downloads: 5,600

Article records:
- Article 1: “Enhancing Sustainable Agriculture through AI-Driven Soil Monitoring”
    - DOI: 10.1234/envinf.2022.001
    - Year: 2024
    - Venue: Journal of Environmental Informatics
    - Authors: Yoyota Vuvuli, Ahmed El-Zein, Clara Green
    - Fields/Topics: Environmental Science, Machine Learning, Precision Agriculture
    - Contribution Roles: Yoyota Vuvuli: Conceptualization, Methodology, Writing (Lead Author) | Ahmed El-Zein: Data Analysis, Software Development | Clara Green: Fieldwork, Writing (Review & Editing)
    - Affiliation at Time of Publication: University of Bologna
    - Citations: 34
    - Downloads: 1,200
    - Reproducibility Badge: Data Open (DOI: 10.1234/agri2022data)
- Article 2: “A Novel Framework for Interpretable Deep Learning in Biomedical Imaging”
    - DOI: 10.5678/ieeetmi.2020.045
    - Year: 2021
    - Venue: IEEE Transactions on Medical Imaging
    - Authors: Yoyota Vuvuli, James Patterson, Rina Huang
    - Fields/Topics: Machine Learning, Biomedical Imaging
    - Contribution Roles: Yoyota Vuvuli: Conceptualization, Algorithm Design, Supervision | James Patterson: Software Implementation, Data Curation | Rina Huang: Validation, Experimentation
    - Affiliation at Time of Publication: University of Bologna
    - Citations: 42
    - Downloads: 1,500
    - Reproducibility Badge: Code Open (GitHub: github.com/vuvuli2020-framework)
- Article 3: “Towards a Comprehensive Ontology for Climate Data Sharing”
    - DOI: 10.9101/dscc.2021.002
    - Year: 2023
    - Venue: Data Science for Climate Change
    - Authors: Yoyota Vuvuli, Marie Dupont, Hiroshi Nakamura
    - Fields/Topics: Environmental Science, Data Science
    - Contribution Roles: Yoyota Vuvuli: Conceptualization, Ontology Design, Writing (Lead Author) | Marie Dupont: Data Integration, Writing (Review) | Hiroshi Nakamura: Technical Infrastructure, Validation
    - Affiliation at Time of Publication: University of Bologna
    - Citations: 18
    - Downloads: 950
    - Reproducibility Badge: FAIR Data (FAIRScore: 85%)
- Article 4: “Ethical AI for Equitable Healthcare Diagnostics”
    - DOI: 10.3456/jrai.2019.014
    - Year: 2019
    - Venue: Journal of Responsible AI Applications
    - Authors: Yoyota Vuvuli, Sarah Michaels
    - Fields/Topics: Machine Learning, Ethics in AI
    - Contribution Roles: Yoyota Vuvuli: Framework Design, Case Studies, Writing (Lead Author) | Sarah Michaels: Literature Review, Ethical Analysis
    - Affiliation at Time of Publication: University of Bologna
    - Citations: 30
    - Downloads: 1,950
    - Reproducibility Badge: Transparent Algorithms (DOI: 10.5678/ethicalai2019)

To support transparency, the academic profile platfrom used by Yoyota Vuvuli offers details about the offered article-level and researcher-level indicators.

Researcher-Level Indicators
- Total Articles Published:
    - Intuition: The total number of a researcher's articles, reflecting their productivity.
    - Data used: Article metadata required to calculate the particular indicator are gathered by the OpenAIRE Graph v9.0.0. 
    - Methodology: All publication records of subtype "Article" from the OpenAIRE Graph that are marked as authored by the researcher are counted. 
    - Related literature: N/A
    - Code: https://github.com/athenarc/bip-scholar-indicators
- Articles in Environmental Science:
    - Intuition: The total number of a researcher's articles from the field of Environmental Science, reflecting their productivity.
    - Data used: Article metadata required to calculate the particular indicator are gathered by the OpenAIRE Graph v9.0.0. 
    - Methodology: All publication records of subtype "Article" from the OpenAIRE Graph that are marked as authored by the researcher and are related to the Environmental Science field are counted. 
    - Related literature: N/A
    - Code: https://github.com/athenarc/bip-scholar-indicators
- Articles in Machine Learning: 
    - Intuition: The total number of a researcher's articles from the field of Machine Learning, reflecting their productivity.
    - Data used: Article metadata required to calculate the particular indicator are gathered by the OpenAIRE Graph v9.0.0. 
    - Methodology: All publication records of subtype "Article" from the OpenAIRE Graph that are marked as authored by the researcher and are related to the Machine Learning field are counted. 
    - Related literature: N/A
    - Code: https://github.com/athenarc/bip-scholar-indicators
- Total Citations: 
    - Intuition: The total number of citations received by all articles of the researcher of interest.
    - Data used: Citations and article metadata required to calculate the particular indicator are gathered by the OpenAIRE Graph v9.0.0. 
    - Methodology: All publication records of subtype "Article" from the OpenAIRE Graph that are marked as authored by the researcher were collected and their citations from other articles were counted. 
    - Related literature: N/A
    - Code: https://github.com/athenarc/bip-scholar-indicators
- Citations in Environmental Science:
    - Intuition: The total number of citations received by all articles of the researcher of interest from the field of Environmental Science. 
    - Data used: Citations and article metadata required to calculate the particular indicator are gathered by the OpenAIRE Graph v9.0.0. 
    - Methodology: All publication records of subtype "Article" from the OpenAIRE Graph that are marked as authored by the researcher and are related to the Environmental Science field were collected and their citations from other articles were counted. 
    - Related literature: N/A
    - Code: https://github.com/athenarc/bip-scholar-indicators
- Citations in Machine Learning:
    - Intuition: The total number of citations received by all articles of the researcher of interest from the field of Machine Learning. 
    - Data used: Citations and article metadata required to calculate the particular indicator are gathered by the OpenAIRE Graph v9.0.0. 
    - Methodology: All publication records of subtype "Article" from the OpenAIRE Graph that are marked as authored by the researcher and are related to the Machine Learning field were collected and their citations from other articles were counted. 
    - Related literature: N/A
    - Code: https://github.com/athenarc/bip-scholar-indicators
- Total Downloads: 
    - Intuition: The total number of downloads received by all articles of the researcher of interest. 
    - Data used: Usage data and article metadata required to calculate the particular indicator are gathered by the OpenAIRE Graph v9.0.0. 
    - Methodology: All publication records of subtype "Article" from the OpenAIRE Graph that are marked as authored by the researcher were collected and their downloads were counted. 
    - Related literature: N/A
    - Code: https://github.com/athenarc/bip-scholar-indicators

Article-Level Indicators
- Citations: 
    - Intuition: The total number of citations received by the article of interest.
    - Data used: Citations and article metadata required to calculate the particular indicator are gathered by the OpenAIRE Graph v9.0.0. 
    - Methodology: All citations from other articles pointing to the article of interest were counted. 
    - Related literature: N/A
    - Code: https://github.com/athenarc/Bip-Ranker
- Downloads:
    - Intuition: The total number of downloads received by the article of interest. 
    - Data used: Usage data and article metadata required to calculate the particular indicator are gathered by the OpenAIRE Graph v9.0.0. 
    - Methodology: All publication records of subtype "Article" from the OpenAIRE Graph that are marked as authored by the researcher were collected and their downloads were counted. 
    - Related literature: N/A
    - Code: N/A
- Reproducibility Badges: 
    - Intuition: N/A
    - Data used: N/A
    - Methodology: N/A 
    - Related literature: N/A
    - Code: N/A

### Example 2
John Doe has created an academic profile using the "Resume for Researchers" Narrative CV template by Royal Society. His profile consists of a series of narratives carefully written by the researcher to provide answers to the respective modules. 

- Name: John Doe
- Current position: Principal Researcher at University of Bologna
- Contact information: j.doe@narniauni.edu
- Personal statement: I am a passionate and driven materials scientist dedicated to advancing sustainable solutions to global environmental challenges. My research focuses on the development of biodegradable polymers, aiming to reduce plastic waste and its impact on ecosystems. With over a decade of experience in academic and collaborative industry projects, I have cultivated a multidisciplinary approach, integrating chemistry, materials science, and environmental studies to drive innovation in sustainable materials. Throughout my career, I have been committed to fostering an inclusive and collaborative research environment. By mentoring early-career researchers, supervising diverse teams, and organizing training programs, I have supported others in achieving their potential while ensuring knowledge transfer across generations of scientists. Beyond my research contributions, I actively engage with the wider scientific and public communities to amplify the impact of my work. Whether through advising policymakers on sustainable packaging legislation or participating in outreach programs to inspire young minds, I strive to bridge the gap between science and society. 
- Module 1. Contributions to General Knowledge: I have dedicated my career to advancing the understanding of sustainable materials science, focusing on the development of biodegradable polymers for packaging applications. My work has led to the publication of 25 peer-reviewed journal articles, including high-impact papers in Nature Materials and Advanced Functional Materials. I led the “Sustainable Polymers Initiative,” a collaborative research project funded by the European Research Council, which developed a novel polymer blend with 50% lower environmental impact compared to traditional plastics. This research has been widely cited and has attracted industrial interest, leading to a joint patent with GreenPack Ltd. Supervising a diverse group of PhD students and postdoctoral researchers, I have fostered innovation and collaboration, resulting in four students winning national awards for their research excellence.
- Module 2. Contributions to the Development of Individuals: I am deeply committed to mentoring and supporting the next generation of researchers. Over the past five years, I have served as a mentor for the Royal Society’s “Future Leaders Program,” guiding early-career scientists in grant writing, career development, and balancing academic and personal responsibilities. I have organized annual training workshops on advanced polymer synthesis techniques, attracting participants from academic and industrial backgrounds. These workshops have been instrumental in equipping attendees with practical skills and fostering industry-academia collaborations. Additionally, I co-developed an undergraduate internship program within my department, which has provided hands-on research opportunities to over 30 students, many of whom have progressed to postgraduate studies.
- Module 3. Contributions to the Wider Research Community: As an advocate for open science, I have chaired the University of Bologna’s Open Access Committee, increasing departmental compliance with open data policies from 60% to 90% over three years. I have been an active member of the editorial boards of Green Chemistry and Journal of Polymer Science, ensuring rigorous peer review standards while promoting the dissemination of innovative research. To strengthen international collaboration, I co-founded the “Global Polymer Network,” a forum connecting over 300 researchers worldwide to share best practices and emerging trends in sustainable materials science.
- Module 4. Contributions to Society: My research has directly contributed to addressing global environmental challenges. The biodegradable polymer developed in the Sustainable Polymers Initiative is now being scaled up by GreenPack Ltd., with the potential to replace traditional plastics in 20% of European food packaging markets by 2030. To raise public awareness, I have participated in science communication initiatives such as the BBC series Future Materials, explaining the role of sustainable materials in tackling climate change. I also contribute regularly to outreach programs in local schools, inspiring young students to pursue careers in STEM fields. In 2022, I collaborated with policymakers to draft recommendations for sustainable packaging legislation, which influenced the European Union’s “Green Materials Directive.

### Example 3
Henry Jekyll has created an academic profile that consists of a set of narratives. Each narrative is describing the motivation, subject, outputs, and impact of a particular line of research work. Dr Jekyll provided the list of research products (articles, datasets, software, etc.) that relate to each line of work. 

- Narrative 1: Exploring the Duality of Molecular Systems for Drug Design
    - The complexity of molecular behavior in biological systems presents a significant challenge for drug design. My research aims to understand and leverage the dual nature of certain molecular systems, which can exhibit distinct functional states depending on environmental or structural conditions. This work addresses the need for more precise and adaptable pharmaceutical agents that minimize side effects while maximizing therapeutic efficacy. This line of research focuses on characterizing “switchable” biomolecules—compounds that can toggle between active and inactive states in response to stimuli like pH, light, or enzymatic interactions. By employing computational chemistry, structural biology, and experimental validation, I explore how these molecules interact with cellular pathways to enable targeted and dynamic drug delivery systems. This research has improved the understanding of molecular duality, paving the way for next-generation drugs that respond dynamically to the body’s needs. These findings have influenced early-stage pharmaceutical development and contributed to interdisciplinary collaborations between biophysics and pharmacology.
    - Related Publications:
        1. Jekyll, H., & Hyde, E. (2020). Structural insights into pH-sensitive molecular switches for targeted drug delivery. Journal of Molecular Systems, 45(3), 567–582.
        2. Jekyll, H. et al. (2021). Computational and experimental evaluation of light-activated biomolecules for precision therapeutics. Biophysical Advances, 12(4), 123–138.
    - Related Datasets:
        1. Dataset: “Molecular Switch Simulation Data for pH-Sensitive Systems” (DOI: 10.1234/molswitch2020).
        2. Dataset: “Experimental Data on Light-Responsive Drug Delivery Molecules” (DOI: 10.5678/lightdrugdata2021).

- Narrative 2: Ethical AI Models in Biochemical Research
    - As artificial intelligence (AI) becomes integral to biochemical research, there is a growing need to ensure that these technologies operate transparently and equitably. My research investigates how AI models can be designed to prioritize ethical considerations, such as bias reduction, explainability, and equitable data representation, while maintaining scientific rigor and innovation. This work focuses on creating ethical frameworks for the development and application of AI in biochemical data analysis. It involves training neural networks on curated datasets, developing algorithms that emphasize interpretability, and implementing safeguards to prevent biased or unreliable predictions in drug discovery and diagnostics. This research has enhanced the reliability and trustworthiness of AI in biochemical applications, fostering more widespread adoption of these tools across academia and industry. It has also influenced discussions around the ethical implications of AI, contributing to the formulation of policy recommendations for its use in life sciences.
    - Related Publications
        1. Jekyll, H., & Smith, A. (2022). Ethical AI frameworks for protein-ligand interaction predictions. Computational Chemistry Ethics, 8(1), 45–63.
        2. Jekyll, H., & Patel, R. (2023). Bias reduction in AI-driven biochemical research: A case study on data curation. Journal of Ethical AI in Science, 2(3), 98–112.
    - Related Datasets
        1. Dataset: “Curated Protein-Ligand Interaction Data for AI Training” (DOI: 10.9101/proteinai2022).
        2. Dataset: “Benchmark Data for Evaluating Ethical AI Models in Biochemistry” (DOI: 10.8765/benchmarkbioai2023).
