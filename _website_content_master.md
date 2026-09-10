# Benoit Seguin — Personal Website Content Master Draft

> **Structure**: Single-Page High-Impact Flow (Proposal A)  
> **Target Audience**: Technical leaders, AI researchers, collaborators, engineers, and broader tech community.  
> **Design Philosophy**: Clear separation between problem, architectural solution, scale/metrics, and public links. Cleanly positions Benoit as a Staff ML Systems Architect & Co-Lead.

---

## 1. Hero & Navigation

### Navigation Menu
* [About](#about)
* [Featured Systems](#featured-systems)
  * [Simula (2024–)](#simula)
  * [LLM Inference & Prompting Engine (2023–)](#llm-engine)
  * [Leap AI (2022–)](#leap-ai)
  * [Model Factory (2023)](#model-factory)
* [Entrepreneurship & Heritage](#heritage-and-ventures)
* [Experience](#experience)
* [Honors & Awards](#honors-and-awards)
* [Publications](#publications)

---

## 2. About Me

**Benoit Seguin**  
*Staff Software Engineer at Google*  
Tokyo, Japan (relocating to Zurich in December)  
[LinkedIn](https://www.linkedin.com/in/benoit-seguin-04a04828) | [Google Scholar](https://scholar.google.com/citations?user=-jJ4MXIAAAAJ) | [Email](mailto:contact@benoitseguin.net) | [X / Twitter](https://x.com/Seguin_Be)

I am a Staff Software Engineer at Google, where I co-lead Simula, Google's core synthetic data framework. Recently, I’ve focused on building agentic, self-improving pipelines for data and RL environment synthesis. I specialize in conceptualizing and engineering the composable abstractions that turn frontier research ideas into robust, high-performance systems at scale.

Before my work on generative AI and agentic systems at Google, I was the CTO and co-founder of **ArtBeat.ai** (building multimodal machine learning valuation models for the fine art market), an independent ML consultant for world-renowned cultural heritage institutions (including the **Getty Research Institute** and the **ETH Library**), and a lecturer at **ETH Zurich**. 

I earned my PhD in Computer Science at **EPFL**, where I led the computer vision architecture for the **Replica Project** at the Venice Time Machine, developing deep learning visual search engines over massive historical photo archives. I am an alumnus of **École Polytechnique** (Paris) and **EPFL** (Lausanne).

---

## 3. Featured Systems & Projects

### Simula (2024–Present)
**Co-Founder & Co-Lead | Google’s Core Synthetic Data Framework**

Teaching AI models requires massive amounts of high-quality data, but generating it manually is impossible.

Simple automated prompting causes AI to create repetitive, low-quality data. I co-founded **Simula** with Hamza Harkous to solve this. We designed a programmable framework that independently controls data diversity, complexity, and quality without human intervention.

Our team scaled Simula into Google's primary internal multimodal data synthesis engine. It is now used by over 2,500 Googlers, was used to generate trillions of tokens, and achieved a 93% user satisfaction score, the highest among all data tools at Google. Used by hundreds of teams, today it is a key enabler for the Gemma ecosystem, provides the primary synthetic data backbone for Gemini safety classifiers, powers production user protection features like AI-powered scam detection, and extends much further across frontier AI applications and data use cases.

#### Highlights & Applications
* One of the core synthetic data generation engines for Google's open-weights **Gemma 4** model family [[Technical Report]](https://arxiv.org/pdf/2607.02770)
* Enabler for **ShieldGemma 1** [[Paper]](https://arxiv.org/abs/2407.21772) and **ShieldGemma 2** [[Overview]](https://deepmind.google/models/gemma/shieldgemma-2/)
* Powers production features: **Android Call Scam Detection** [[Pixel Drop]](https://support.google.com/pixelphone/thread/328747602/march-2025-pixel-drop) & **Android Messages Spam Detection** [[Google Blog]](https://blog.google/products-and-platforms/platforms/android/new-android-features-march-2025/)
* Applications across **FunctionGemma**, **Workspace Prompt Injection Defense**, and **Enterprise Security ML**
* [Research Paper (TMLR)](https://arxiv.org/abs/2603.29791) | [Google Research Blog Overview](https://research.google/blog/designing-synthetic-datasets-for-the-real-world-mechanism-design-and-reasoning-from-first-principles/)

---

### Internal LLM Prompting & Agentic Bulk Inference Engine (2023–Present)
**Creator & Lead Architect | Prompt Templating & Distributed Batch Inference**

As LLM workflows evolved beyond simple chat prompts into complex agentic graphs and bulk synthetic generation, research teams needed a flexible way to manage prompt composition and run large-scale inference efficiently.

I created a lightweight, expressive prompt management toolkit and bulk inference engine that became popular among researchers across Google for rapid prototyping and large-scale batch generation.

#### Architecture & Highlights
* **Expressive Prompt Templating**: Extends modern templating engines with composable primitives for structured schema enforcement, multimodal context assembly, dynamic few-shot injection, and modular partials.
* **Distributed Bulk Inference**: Built horizontally scalable inference pipelines on top of Jax-on-beam, allowing complex multi-step and agentic generation workflows to execute across distributed accelerator clusters.
* **Off-Peak Compute Efficiency**: Leveraged opportunistic, off-peak datacenter capacity to run high-throughput batch inference workloads with significant infrastructure savings.
* **Foundational Layer for Simula**: Provided the core prompt rendering and batch inference substrate underlying Simula's data generation pipelines.

#### Scale & Impact
* Reached **10,000+ monthly active users**, becoming a go-to toolkit across Google for structured prompt templating and bulk inference.
* Used to generate **multi-trillion tokens** across diverse research workflows and data generation pipelines.

---

### Leap AI (2022–Present)
**System Lead & Architect | Scaling User Feedback Intelligence across 22 ML Models**

> *Users generate millions of reviews, bug reports, and feedback messages daily. Finding critical product bugs, emerging privacy issues, and user trust signals in this torrent of noisy text is like searching for needles in a hurricane.*

Leap AI represents the production evolution and enterprise scaling of the research introduced in **Hark** ([IEEE S&P 2022](https://research.google/pubs/hark-a-deep-learning-system-for-navigating-privacy-feedback-at-scale/)). While Hark established the deep learning methodology for classifying unstructured user complaints, I designed and led the global system architecture for **Leap AI** ("Trust Insights at Scale"), turning that research into a 24/7 continuous enterprise intelligence platform.

#### Architecture & Key Innovations
* **22-Model Orchestrated Pipeline**: Architected a fault-tolerant, streaming pipeline built on Google's Dreampipe framework that coordinates 22 specialized, distilled machine learning models executing multi-stage classification, named entity recognition, topic routing, and sentiment analysis.
* **High-Efficiency Model Distillation**: Oversaw the distillation of heavy LLMs into compact, sub-millisecond on-device and server models capable of meeting strict latency and high-QPS service-level objectives.
* **Interactive AI Intelligence Dashboard**: Designed an interactive exploration interface combining vector-based thematic clustering with real-time Gemini-powered qualitative synthesis, allowing privacy engineers and product leads to converse with user feedback trends.

#### Scale & Impact
* **2 Million+ user feedback items processed daily** in production with 99.9% pipeline reliability.
* **Powers feedback intelligence** across major Google product dashboards, directly surfacing critical privacy vulnerabilities and usability flaws to product engineering leads.
* Reduced feedback triaging cycle times by more than 2x.

---

### Model Factory & LabelWand (2023)
**Primary Contributor | Human-in-the-Loop Active Learning & Data Curation Platform**

> *Building accurate domain-specific models requires high-quality labeled datasets. Purely manual labeling is prohibitively slow, while ungrounded automated labeling introduces dangerous label drift.*

I served as a primary contributor to **LabelWand**, an internal web platform for accelerated data curation combining diversified retrieval, active learning, and LLM-assisted labeling, which subsequently graduated into Google's **Model Factory**.

#### Architecture & Key Innovations
* **LLM Interaction Layer**: Architected the core abstractions and asynchronous task backend handling all LLM completions, prompt transformations, and active labeling suggestions.
* **Distributed Bulk Inference**: Engineered the initial distributed bulk inference pipeline (Sax-based) for rapid pre-annotation.
* **Spanner-Based Nearest-Neighbor Retrieval**: Designed and implemented a vector nearest-neighbor retrieval engine directly on top of Google Spanner, enabling real-time semantic similarity searches across large user-uploaded datasets without dedicated external vector database clusters.

#### Scale & Impact
* **Winner of the Google Core Tech Impact Award** (awarded to the top 5% of engineering projects).
* Accelerated dataset curation timelines by over 5x across dozens of participating research and product teams.

---

## 4. Entrepreneurship & Cultural Heritage AI (2014–2022)

Before joining Google, my research and engineering focused on building large-scale computer vision systems for complex, real-world data collections, spanning startup entrepreneurship, academic research, and world-class cultural institutions.

### ArtBeat.ai (2021–2022)
**CTO & Co-Founder | AI-Powered Art Market Intelligence**
* Co-founded and led the engineering team (3 engineers) to construct an end-to-end intelligence and valuation engine for the global art market.
* **Data Ingestion Pipeline**: Architected a scalable data crawling and normalization pipeline collecting millions of historical auction transactions, catalog raisonnés, gallery records, and high-resolution artwork images.
* **Multimodal Valuation Models**: Developed an explainable multimodal valuation model that integrated visual image embeddings, historical price dynamics, artist network graphs, and auction house metadata—outperforming expert human estimates 45% of the time.
* **Production Architecture**: Built and deployed the full cloud infrastructure, microservices backend, and customer-facing exploration application.

### High-Impact Cultural Heritage Consulting & Academic Leadership (2019–2022)
**Independent ML Consultant & Lecturer at ETH Zurich**
* **Getty Research Institute (Los Angeles)**: Formulated the technical strategy and computer vision architecture to automate the digitization, document layout analysis, and catalog organization of the Getty's massive Photo Archive.
* **ETH Library (Zurich)**: Designed and implemented a full-stack text-reuse and cross-correlation platform (`e-rara`) analyzing 500,000+ digitized pages of architectural history to track intellectual influence across centuries.
* **The Impresso Project (EPFL & Luxembourg)**: Built a high-performance visual search engine and recommendation system indexing millions of historical newspaper photographs and media archives.
* **Lecturer at ETH Zurich**: Taught advanced applied machine learning and data science courses.

### EPFL PhD: The Replica Project & dhSegment (2014–2018)
**PhD Researcher | Digital Humanities Laboratory (DHLAB), EPFL**  
*Advisor: Prof. Frédéric Kaplan*
* **The Replica Project**: Spearheaded the computer vision architecture for a flagship initiative with the Cini Foundation in Venice, developing deep-learning visual similarity algorithms to discover composition borrowing, student copies, and visual citations across hundreds of thousands of Renaissance artworks.
* **dhSegment**: Co-created and open-sourced **dhSegment**, a versatile pixel-level deep learning framework for historical document segmentation and layout analysis, widely adopted across digital humanities laboratories globally.
* **Best Demonstration Award**: Research Days of the Computer Science Faculty, EPFL (2017).

---

## 5. Career Experience

* **Google** | Staff Software Engineer (2025 – Present), Senior Software Engineer (Sept 2022 – 2025)  
  *Co-founder & Co-lead of Simula; Creator of Google's internal LLM Prompting & Bulk Inference Engine; Architect of Leap AI; Core Tech Impact Award Winner; Top-2 Code Author (2024).*
* **ArtBeat.ai** | CTO & Co-Founder (Mar 2021 – Apr 2022)  
  *Led engineering for an AI-driven art market valuation startup; architected multimodal valuation models and multi-source ETL pipelines.*
* **Benoit Seguin Consulting & Software Development** | Principal Consultant (Jan 2019 – Apr 2022)  
  *Machine learning consulting for world-class cultural heritage institutions: Getty Research Institute, ETH Library, and the Impresso Project.*
* **ETH Zurich** | Lecturer (2019 – 2021)  
  *Taught practical machine learning and scalable data processing.*
* **EPFL (DHLAB)** | PhD Candidate & Researcher (Sept 2014 – Nov 2018)  
  *Conducted research on deep learning for large iconographic archives; authored Replica and dhSegment.*
* **EPFL (CVLAB)** | Scientific Assistant (Aug 2013 – Sept 2014)  
  *Implemented high-speed multithreaded segmentation algorithms for biological SEM microscopy images.*
* **IBM Research Zurich** | Master Thesis Researcher (Feb 2013 – Aug 2013)  
  *Investigated VLSI pattern variability in optical lithography printing via automated SEM image analysis.*
* **Carnegie Mellon University** | Research Intern (Apr 2011 – Sept 2011)  
  *Researched unsupervised object detection leveraging gaze-tracking data with Prof. Martial Hebert.*

---

## 6. Honors & Awards

* **Outstanding Impact Rating (Google, 2024)**: Google's highest performance tier (top 4%), awarded for the cross-organizational impact of Simula and foundational LLM inference infrastructure.
* **Top-2 Code Author (Google PSS, 2024)**: Ranked #2 by code contributions across 116 FTEs in Applied Research and Security.
* **Two-time Core Tech Impact Award (Google)**: Awarded to the top 5% of projects across Google Core for *Simula* and *Model Factory*.
* **25 Peer & Spot Bonuses (Google, 2022–Present)**: Recognizing cross-team technical leadership and execution.
* **Google Hash Code Finalist (2016)**: Qualified for the global final round (top 50 out of 1,000+ international engineering teams).
* **Best Demonstration Award (EPFL, 2017)**: Computer Science Faculty Research Days.

---

## 7. Education

* **Ph.D. in Computer Science** — **EPFL (Swiss Federal Institute of Technology, Lausanne)** (2014–2018)  
  *Thesis: Making large-scale art historical photo archives searchable: A deep learning approach.*
* **M.Sc. in Computer Science** — **EPFL** (2011–2013)  
  *Specialization in Computer Vision, Machine Learning, and Distributed Systems.*
* **Diplôme d’Ingénieur** — **École Polytechnique (Paris)** (2008–2012)  
  *France's premier engineering Grande École; intensive curriculum in Applied Mathematics and Computer Science.*

---

## 8. Selected Publications & Technical Reports

[View full publication list on Google Scholar](https://scholar.google.com/citations?user=-jJ4MXIAAAAJ)

1. **Reasoning-Driven Synthetic Data Generation and Evaluation**  
   *Transactions on Machine Learning Research (TMLR) / arXiv:2603.29791 (2026)*  
   Davidson, T. R., **Seguin, B.**, Bacis, E., Ilharco, C., Harkous, H.  
   Introduces Simula, reframing synthetic data generation as structured mechanism design and first-principles reasoning rather than heuristic prompt hacking, providing programmable control over diversity, complexity, and dataset fidelity.  
   [[Paper]](https://arxiv.org/abs/2603.29791) [[Google Research Blog]](https://research.google/blog/designing-synthetic-datasets-for-the-real-world-mechanism-design-and-reasoning-from-first-principles/)

2. **Gemma 4 Technical Report**  
   *Google DeepMind (2026)*  
   Gemma Team (incl. **Seguin, B.**)  
   Technical report detailing Google's next-generation open-weights model family. Contributor to the high-throughput synthetic data generation pipelines powered by Simula.  
   [[Technical Report (PDF)]](https://arxiv.org/pdf/2607.02770)

3. **dhSegment: A Generic Deep-Learning Approach for Document Segmentation**  
   *16th International Conference on Frontiers in Handwriting Recognition (ICFHR) (2018)*  
   Oliveira, S.\*, **Seguin, B.\***, Kaplan, F.  
   Presents a general-purpose, convolutional neural network architecture for historical document layout analysis, page extraction, and text line segmentation.  
   [[Paper]](https://arxiv.org/abs/1804.10371) [[Code & Project]](https://dhlab-epfl.github.io/dhSegment/)

4. **The Replica Project: Building a Visual Search Engine for Art Historians**  
   *XRDS: Crossroads, The ACM Magazine for Students (2018)*  
   **Seguin, B.**  
   Invited overview of the computer vision architecture, reverse image indexing, and visual link retrieval mechanisms developed for the Cini Foundation's iconographic collections in Venice.  
   [[Paper (ACM)]](https://dl.acm.org/authorize?N658957)

5. **New Techniques for the Digitization of Art Historical Photographic Archives**  
   *Archiving Conference, IS&T (2018)*  
   **Seguin, B.**, Costiner, L., di Lenardo, I., Kaplan, F.  
   Describes the automatic image processing and computer vision pipeline deployed for the digitization and enrichment of the Giorgio Cini Foundation's photo collection in Venice.  
   [[Paper (PDF)]](https://profile.benoitseguin.net/uploads/publications/Archiving2018.pdf)

6. **Visual Link Retrieval in a Database of Paintings**  
   *ECCV Visart Workshop (2016)*  
   **Seguin, B.**, Striolo, C., di Lenardo, I., Kaplan, F.  
   Formulates the metric learning framework for visual similarity search and visual citation discovery across large collections of fine art.  
   [[Paper]](https://infoscience.epfl.ch/record/223771)

7. **Deep Learning for Logic Optimization Algorithms**  
   *IEEE International Symposium on Circuits and Systems (ISCAS) (2018)*  
   Haaswijk, W.\*, Collins, E.\*, **Seguin, B.\***, Soeken, M., Süsstrunk, S., Kaplan, F., De Micheli, G.  
   Explores the application of deep reinforcement learning for logic synthesis and combinatorial Boolean network optimization.  
   [[Paper]](https://msoeken.github.io/papers/2018_iscas.pdf)
