---
layout: home
---

<section id="about">
  <div class="bio-header">
    <img class="bio-photo" src="{{ site.baseurl }}/uploads/profile_picture2_corrected.jpg" alt="Benoit Seguin, PhD">
    <div class="bio-details">
      <h1 style="font-size: 1.75rem; margin: 0 0 4px 0;">Benoit Seguin, PhD</h1>
      <div class="bio-role">Staff Software Engineer at Google</div>
      <div class="bio-location">Tokyo, Japan (relocating to Zurich in December)</div>
      <div class="bio-links">
        <a href="https://www.linkedin.com/in/benoit-seguin-04a04828" target="_blank" rel="noopener">LinkedIn</a> &bull;
        <a href="https://scholar.google.com/citations?user=-jJ4MXIAAAAJ" target="_blank" rel="noopener">Google Scholar</a> &bull;
        <a href="mailto:contact@benoitseguin.net">Email</a> &bull;
        <a href="https://x.com/Seguin_Be" target="_blank" rel="noopener">X / Twitter</a>
      </div>
    </div>
  </div>

  <p>
    I am a Staff Software Engineer at Google, where I co-lead the core synthetic data framework (<strong>Simula</strong>). Recently, I’ve focused on building agentic, self-improving pipelines for data and RL environment synthesis. I specialize in conceptualizing and engineering the composable abstractions that turn frontier research ideas into robust, high-performance systems at scale.
  </p>
</section>

---

<section id="projects">
  <a id="featured-systems"></a>
  <h2>Featured Systems &amp; Projects</h2>

  <div id="simula" class="project-card">
    <h3 style="margin-top: 0;">Simula (2024–Present)</h3>
    <div class="project-role">Co-Founder &amp; Co-Lead | Google’s Core Synthetic Data Framework</div>

    <p>Teaching AI models requires massive amounts of high-quality data, but generating it manually is impossible.</p>

    <p>Simple automated prompting causes AI to create repetitive, low-quality data. I co-founded <strong>Simula</strong> with Hamza Harkous to solve this. We designed a programmable framework that independently controls data diversity, complexity, and quality without human intervention.</p>

    <p>Our team scaled Simula into Google's primary internal multimodal data synthesis engine. It is now used by over 2,500 Googlers, was used to generate trillions of tokens, and achieved a 93% user satisfaction score, the highest among all data tools at Google. Used by hundreds of teams, today it is a key enabler for the Gemma ecosystem, provides the primary synthetic data backbone for Gemini safety classifiers, powers production user protection features like AI-powered scam detection, and extends much further across frontier AI applications and data use cases.</p>

    <h4 style="margin-bottom: 6px;">Highlights &amp; Applications</h4>
    <ul>
      <li>One of the core synthetic data generation engines for Google's open-weights <strong>Gemma 4</strong> model family [<a href="https://arxiv.org/pdf/2607.02770" target="_blank" rel="noopener">Technical Report</a>]</li>
      <li>Enabler for <strong>ShieldGemma 1</strong> [<a href="https://arxiv.org/abs/2407.21772" target="_blank" rel="noopener">Paper</a>] and <strong>ShieldGemma 2</strong> [<a href="https://deepmind.google/models/gemma/shieldgemma-2/" target="_blank" rel="noopener">Overview</a>]</li>
      <li>Powers production features: <strong>Android Call Scam Detection</strong> [<a href="https://support.google.com/pixelphone/thread/328747602/march-2025-pixel-drop" target="_blank" rel="noopener">Pixel Drop</a>] &amp; <strong>Android Messages Spam Detection</strong> [<a href="https://blog.google/products-and-platforms/platforms/android/new-android-features-march-2025/" target="_blank" rel="noopener">Google Blog</a>]</li>
      <li>Applications across <strong>FunctionGemma</strong>, <strong>Workspace Prompt Injection Defense</strong>, and <strong>Enterprise Security ML</strong></li>
      <li><a href="https://arxiv.org/abs/2603.29791" target="_blank" rel="noopener">Research Paper (TMLR)</a> &bull; <a href="https://research.google/blog/designing-synthetic-datasets-for-the-real-world-mechanism-design-and-reasoning-from-first-principles/" target="_blank" rel="noopener">Google Research Blog Overview</a></li>
    </ul>
  </div>

  <div id="llm-engine" class="project-card">
    <h3 style="margin-top: 0;">Internal LLM Prompting &amp; Agentic Bulk Inference Engine (2023–Present)</h3>
    <div class="project-role">Creator &amp; Lead Architect | Prompt Templating &amp; Distributed Batch Inference</div>

    <p>As LLM workflows evolved beyond simple chat prompts into complex agentic graphs and bulk synthetic generation, research teams needed a flexible way to manage prompt composition and run large-scale inference efficiently.</p>

    <p>I created a lightweight, expressive prompt management toolkit and bulk inference engine that became popular among researchers across Google for rapid prototyping and large-scale batch generation.</p>

    <h4 style="margin-bottom: 6px;">Architecture &amp; Highlights</h4>
    <ul>
      <li><strong>Expressive Prompt Templating</strong>: Extends modern templating engines with composable primitives for structured schema enforcement, multimodal context assembly, dynamic few-shot injection, and modular partials.</li>
      <li><strong>Distributed Bulk Inference</strong>: Built horizontally scalable inference pipelines on top of Jax-on-beam, allowing complex multi-step and agentic generation workflows to execute across distributed accelerator clusters.</li>
      <li><strong>Off-Peak Compute Efficiency</strong>: Leveraged opportunistic, off-peak datacenter capacity to run high-throughput batch inference workloads with significant infrastructure savings.</li>
      <li><strong>Foundational Layer for Simula</strong>: Provided the core prompt rendering and batch inference substrate underlying Simula's data generation pipelines.</li>
    </ul>

    <h4 style="margin-bottom: 6px;">Scale &amp; Impact</h4>
    <ul>
      <li>Reached <strong>10,000+ monthly active users</strong>, becoming a go-to toolkit across Google for structured prompt templating and bulk inference.</li>
      <li>Used to generate <strong>multi-trillion tokens</strong> across diverse research workflows and data generation pipelines.</li>
    </ul>
  </div>
</section>

---

<section id="heritage-and-ventures">
  <details class="collapsible-section">
    <summary>
      <h2 style="display: inline;">Entrepreneurship &amp; Cultural Heritage AI (2014–2022)</h2>
    </summary>
    <div style="margin-top: 1.2rem;">
      <p>Before joining Google, my research and engineering focused on building large-scale computer vision systems for complex, real-world data collections, spanning startup entrepreneurship, academic research, and world-class cultural institutions.</p>

      <h3>ArtBeat.ai (2021–2022)</h3>
      <p><strong>CTO &amp; Co-Founder | AI-Powered Art Market Intelligence</strong></p>
      <ul>
        <li>Co-founded and led the engineering team (3 engineers) to construct an end-to-end intelligence and valuation engine for the global art market.</li>
        <li><strong>Data Ingestion Pipeline</strong>: Architected a scalable data crawling and normalization pipeline collecting millions of historical auction transactions, catalog raisonn&eacute;s, gallery records, and high-resolution artwork images.</li>
        <li><strong>Multimodal Valuation Models</strong>: Developed an explainable multimodal valuation model that integrated visual image embeddings, historical price dynamics, artist network graphs, and auction house metadata&mdash;outperforming expert human estimates 45% of the time.</li>
        <li><strong>Production Architecture</strong>: Built and deployed the full cloud infrastructure, microservices backend, and customer-facing exploration application.</li>
      </ul>

      <h3>High-Impact Cultural Heritage Consulting &amp; Academic Leadership (2019–2022)</h3>
      <p><strong>Independent ML Consultant &amp; Lecturer at ETH Zurich</strong></p>
      <ul>
        <li><strong>Getty Research Institute (Los Angeles)</strong>: Formulated the technical strategy and computer vision architecture to automate the digitization, document layout analysis, and catalog organization of the Getty's massive Photo Archive.</li>
        <li><strong>ETH Library (Zurich)</strong>: Designed and implemented a full-stack text-reuse and cross-correlation platform (<code>e-rara</code>) analyzing 500,000+ digitized pages of architectural history to track intellectual influence across centuries.</li>
        <li><strong>The Impresso Project (EPFL &amp; Luxembourg)</strong>: Built a high-performance visual search engine and recommendation system indexing millions of historical newspaper photographs and media archives.</li>
        <li><strong>Lecturer at ETH Zurich</strong>: Taught advanced applied machine learning and data science courses.</li>
      </ul>

      <h3>EPFL PhD: The Replica Project &amp; dhSegment (2014–2018)</h3>
      <p><strong>PhD Researcher | Digital Humanities Laboratory (DHLAB), EPFL</strong><br>
      <em>Advisor: Prof. Fr&eacute;d&eacute;ric Kaplan</em></p>
      <ul>
        <li><strong>The Replica Project</strong>: Spearheaded the computer vision architecture for a flagship initiative with the Cini Foundation in Venice, developing deep-learning visual similarity algorithms to discover composition borrowing, student copies, and visual citations across hundreds of thousands of Renaissance artworks.</li>
        <li><strong>dhSegment</strong>: Co-created and open-sourced <strong>dhSegment</strong>, a versatile pixel-level deep learning framework for historical document segmentation and layout analysis, widely adopted across digital humanities laboratories globally.</li>
        <li><strong>Best Demonstration Award</strong>: Research Days of the Computer Science Faculty, EPFL (2017).</li>
      </ul>
    </div>
  </details>
</section>

---

<section id="experience">
  <h2>Career Experience</h2>

  <ul>
    <li><strong>Google</strong> | Staff Software Engineer <em>(Sept 2022 &ndash; Present)</em><br>
    Co-founder &amp; Co-lead of Simula; Creator of Google's internal LLM Prompting &amp; Bulk Inference Engine; Architect of Leap AI; Core Tech Impact Award Winner; Top-2 Code Author (2024).</li>
    <li><strong>ArtBeat.ai</strong> | CTO &amp; Co-Founder <em>(Mar 2021 &ndash; Apr 2022)</em><br>
    Led engineering for an AI-driven art market valuation startup; architected multimodal valuation models and multi-source ETL pipelines.</li>
    <li><strong>Benoit Seguin Consulting &amp; Software Development</strong> | Principal Consultant <em>(Jan 2019 &ndash; Apr 2022)</em><br>
    Machine learning consulting for world-class cultural heritage institutions: Getty Research Institute, ETH Library, and the Impresso Project.</li>
    <li><strong>ETH Zurich</strong> | Lecturer <em>(2019 &ndash; 2021)</em><br>
    Taught practical machine learning and scalable data processing.</li>
    <li><strong>EPFL (DHLAB)</strong> | PhD Candidate &amp; Researcher <em>(Sept 2014 &ndash; Nov 2018)</em><br>
    Conducted research on deep learning for large iconographic archives; authored Replica and dhSegment.</li>
  </ul>
</section>

---

<section id="education">
  <h2>Education</h2>

  <ul>
    <li><strong>Ph.D. in Computer Science</strong> &mdash; <strong>EPFL (Swiss Federal Institute of Technology, Lausanne)</strong> <em>(2014&ndash;2018)</em><br>
    Thesis: <em>Making large-scale art historical photo archives searchable: A deep learning approach.</em></li>
    <li><strong>M.Sc. in Computer Science</strong> &mdash; <strong>EPFL</strong> <em>(2011&ndash;2013)</em><br>
    Specialization in Computer Vision, Machine Learning, and Distributed Systems.</li>
    <li><strong>Dipl&ocirc;me d&rsquo;Ing&eacute;nieur</strong> &mdash; <strong>&Eacute;cole Polytechnique (Paris)</strong> <em>(2008&ndash;2012)</em><br>
    France's premier engineering Grande &Eacute;cole; intensive curriculum in Applied Mathematics and Computer Science.</li>
  </ul>
</section>

---

<section id="publications">
  <h2>Selected Publications &amp; Technical Reports</h2>

  <p><a href="https://scholar.google.com/citations?user=-jJ4MXIAAAAJ" target="_blank" rel="noopener">View full publication list on Google Scholar</a></p>

  <div class="pub-item">
    <div class="pub-title">Reasoning-Driven Synthetic Data Generation and Evaluation</div>
    <div class="pub-venue">Transactions on Machine Learning Research (TMLR) / arXiv:2603.29791 (2026)</div>
    <div class="pub-authors">Davidson, T. R., <strong>Seguin, B.</strong>, Bacis, E., Ilharco, C., Harkous, H.</div>
    <p style="margin-bottom: 4px;">Introduces Simula, reframing synthetic data generation as structured mechanism design and first-principles reasoning rather than heuristic prompt hacking, providing programmable control over diversity, complexity, and dataset fidelity.</p>
    <div class="pub-links">
      [<a href="https://arxiv.org/abs/2603.29791" target="_blank" rel="noopener">Paper</a>]
      [<a href="https://research.google/blog/designing-synthetic-datasets-for-the-real-world-mechanism-design-and-reasoning-from-first-principles/" target="_blank" rel="noopener">Google Research Blog</a>]
    </div>
  </div>

  <div class="pub-item">
    <div class="pub-title">Gemma 4 Technical Report</div>
    <div class="pub-venue">Google DeepMind (2026)</div>
    <div class="pub-authors">Gemma Team (incl. <strong>Seguin, B.</strong>)</div>
    <p style="margin-bottom: 4px;">Technical report detailing Google's next-generation open-weights model family. Contributor to the high-throughput synthetic data generation pipelines powered by Simula.</p>
    <div class="pub-links">
      [<a href="https://arxiv.org/pdf/2607.02770" target="_blank" rel="noopener">Technical Report (PDF)</a>]
    </div>
  </div>

  <div class="pub-item">
    <div class="pub-title">dhSegment: A Generic Deep-Learning Approach for Document Segmentation</div>
    <div class="pub-venue">16th International Conference on Frontiers in Handwriting Recognition (ICFHR) (2018)</div>
    <div class="pub-authors">Oliveira, S.*, <strong>Seguin, B.*</strong>, Kaplan, F.</div>
    <p style="margin-bottom: 4px;">Presents a general-purpose, convolutional neural network architecture for historical document layout analysis, page extraction, and text line segmentation.</p>
    <div class="pub-links">
      [<a href="https://arxiv.org/abs/1804.10371" target="_blank" rel="noopener">Paper</a>]
      [<a href="https://dhlab-epfl.github.io/dhSegment/" target="_blank" rel="noopener">Code &amp; Project</a>]
    </div>
  </div>

  <div class="pub-item">
    <div class="pub-title">The Replica Project: Building a Visual Search Engine for Art Historians</div>
    <div class="pub-venue">XRDS: Crossroads, The ACM Magazine for Students (2018)</div>
    <div class="pub-authors"><strong>Seguin, B.</strong></div>
    <p style="margin-bottom: 4px;">Invited overview of the computer vision architecture, reverse image indexing, and visual link retrieval mechanisms developed for the Cini Foundation's iconographic collections in Venice.</p>
    <div class="pub-links">
      [<a href="https://dl.acm.org/authorize?N658957" target="_blank" rel="noopener">Paper (ACM)</a>]
    </div>
  </div>

  <div class="pub-item">
    <div class="pub-title">New Techniques for the Digitization of Art Historical Photographic Archives</div>
    <div class="pub-venue">Archiving Conference, IS&amp;T (2018)</div>
    <div class="pub-authors"><strong>Seguin, B.</strong>, Costiner, L., di Lenardo, I., Kaplan, F.</div>
    <p style="margin-bottom: 4px;">Describes the automatic image processing and computer vision pipeline deployed for the digitization and enrichment of the Giorgio Cini Foundation's photo collection in Venice.</p>
    <div class="pub-links">
      [<a href="{{ site.baseurl }}/uploads/publications/Archiving2018.pdf" target="_blank" rel="noopener">Paper (PDF)</a>]
    </div>
  </div>

  <div class="pub-item">
    <div class="pub-title">Visual Link Retrieval in a Database of Paintings</div>
    <div class="pub-venue">ECCV Visart Workshop (2016)</div>
    <div class="pub-authors"><strong>Seguin, B.</strong>, Striolo, C., di Lenardo, I., Kaplan, F.</div>
    <p style="margin-bottom: 4px;">Formulates the metric learning framework for visual similarity search and visual citation discovery across large collections of fine art.</p>
    <div class="pub-links">
      [<a href="https://infoscience.epfl.ch/record/223771" target="_blank" rel="noopener">Paper</a>]
    </div>
  </div>

  <div class="pub-item">
    <div class="pub-title">Deep Learning for Logic Optimization Algorithms</div>
    <div class="pub-venue">IEEE International Symposium on Circuits and Systems (ISCAS) (2018)</div>
    <div class="pub-authors">Haaswijk, W.*, Collins, E.*, <strong>Seguin, B.*</strong>, Soeken, M., S&uuml;sstrunk, S., Kaplan, F., De Micheli, G.</div>
    <p style="margin-bottom: 4px;">Explores the application of deep reinforcement learning for logic synthesis and combinatorial Boolean network optimization.</p>
    <div class="pub-links">
      [<a href="https://msoeken.github.io/papers/2018_iscas.pdf" target="_blank" rel="noopener">Paper</a>]
    </div>
  </div>
</section>
