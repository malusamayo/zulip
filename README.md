# Individual Assignment 1: Building an ML-enabled Product

(17-445/17-645/17-745 Machine Learning in Production; 11-695 AI Engineering)

## Overview

In this assignment, you will enhance an existing product with a new feature powered by machine learning. Building a system with an ML component requires more than training a model. While sometimes central to the system, the ML component is typically just one part among many in a larger system. 

Learning goals:
* Demonstrate familiarity with programming skills necessary for this course
* Understand the scope of software engineering challenges when building a production system with ML components
* Identify technical and nontechnical challenges 
* Discuss user interface design decisions and risks introduced with the ML component

**A word on scope and difficulty.** In this assignment, you will work with an existing nontrivial code base of a web application. We do not expect that you know all the technologies involved, but we expect some basic programming skills as a prerequisite for this course and assume that you can quickly learn the necessary skills to make changes with documentation, tutorials, StackOverflow, or various AI tools. Incrementally modifying and maintaining existing systems is far more common than developing new things from scratch. Learning new technologies, libraries and tools and troubleshooting problems are important skills and a prerequisite to be successful in this class, especially in the team project. Beyond that, this assignment is intentionally *open ended*. We provide some recommendations for technologies to use but you are free to use others. 

## Research in this Course
_For this class, we’re conducting research on student outcomes. This research will involve your work in this course. You will not be asked to do anything above and beyond the normal learning activities and assignments that are part of this course. You are free not to participate in this research, and your participation will have no influence on your grade for this course or your academic career at CMU. If you do not wish to participate or if you are under 18 years of age, please fill in the form: https://forms.gle/zn7PQgXA12bn3phM7. Participants will not receive any compensation. The data collected as part of this research may include student grades and homework solutions. All analyses of data from participants’ coursework will be conducted after the course is over and final grades are submitted. To minimize the risk of breach of confidentiality, the data used for analysis will not contain any personal identifiers, all data will be analyzed in de-identified and presented in aggregated form. Again, this research will not affect your grades, and the professor will not know who is participating in this research study until the grades are submitted. If you have questions pertaining to your rights as a research participant, or to report concerns to this study, please contact Christina Ma (qianouma@cmu.edu)._

## Tasks
Seemingly every software project now needs to integrate LLMs or agents, so of course you are going to introduce LLM features to your web project too. Specifically, you are going to extend [zulip](https://github.com/zulip/zulip), an open-source team collaboration tool created as a Slack replacement. 

**Introduce ML-powered features.** Consider what LLM-powered features would be interesting to users for a project like this. Implement two LLM-powered features:

* *Messages recap feature:* Zulip organizes conversations into streams and topics – it might be easy to miss important updates when you’re away. Implement a feature that uses an LLM to generate concise recaps of unread messages from selected streams. The system should offer a simple “View recap” action that gathers relevant messages, sends them to an LLM, and returns a compact, human-readable summary to be displayed to the user. The summary should come with clickable references that jump directly to the original messages, which are visually highlighted for context.
* *Topic Title Improver feature:* Zulip topics can drift as conversations evolve, leaving titles stale, vague, or misleading. Implement a feature that uses an LLM to propose improved topic titles when the system detects drift (e.g., sustained off-title discussion, new sub-thread emerging). This should be triggered automatically with new messages and suggest new topic title in the UI. When implementing this feature, you will want to consider the associated cost and latency, and choose appropriate models and time to trigger this feature. 

You can use any existing LLM models as part of your implementation. We explicitly allow using AI coding assistants (e.g., Copilot Chat, Cursor) to help you complete the assignment. However, we expect you to understand the code changes made and explain them in your report and during recitation verbally. If you decide to use any forms of AI coding assistants, you will need to install a [usage monitoring extension](). This is purely for research purposes and will not affect your grades. With the extension installed, you will receive a report on your AI usage at the end of the semester, with recommendations on how to improve in the future.

**Discuss the feature in the product.** Machine learning contributes a part to a larger application with many non-ML parts and system-level concerns. When designing the features, think about how you introduce the features into the existing open source application, whether they change the user interface, when and how to call the ML models, and what risks they introduce. Finally, anticipate engineering issues that might occur if you wanted to scale the system to support millions of users and daily image uploads. Make sure you are discussing this in the context of the overall application, not just the model. 

Your discussions may reveal limitations and risks in your implementation and make suggestions for improvements. Even if you point out serious flaws in your own implementation, you are not required to implement the improvements if your implementation already meets our minimal requirements.


## Deliverables

See Canvas for instructions of how to create a private repository with GitHub classroom that contains the existing *zulip* implementation.

**Code:** Commit all your code changes to your GitHub repository, but *do not commit private credentials*. Update instructions to install and run the system in the `README.md` file as necessary. For example, explain how to get an API token if needed or add additional libraries to `pyproject.toml`. 

**Report:** Additionally, upload a short report to Gradescope by [date see Canvas] with the following content: 

* **GitHub link:** Start the document with a link *to your last commit* on GitHub: On the GitHub webpage, click on the last commit message and copy the URL. The URL must be in the format `https://github.com/cmu-seai/[repo]/commit/[commitid]`. Make sure that the link includes the long ID of the last commit.
* **Technical description (1 page max):** In one sentence, describe what you selected as the second feature. Then briefly describe how you implemented the two features. Provide pointers to the relevant parts of the code, ideally as direct links to files or even to specific lines on GitHub. We prefer readable links in the PDF rather than hyperlinks behind text (e.g., https://github.com/mlip-cmu/f2025/blob/main/assignments/I1_mlproduct.md?plain=1#L46 rather than [this](https://github.com/mlip-cmu/f2025/blob/main/assignments/I1_mlproduct.md?plain=1#L46)).
* **User interface design approach (1 page max):** Using the vocabulary of the lecture and readings, recommend for each of the two features how the feature should interact with users (automate, prompt, organize, annotate, hybrid) and why. Justify your recommendation, considering forcefulness, frequency, value, and cost. If your implementation differs from the recommended approach, briefly explain how you would change your implementation if you had more time.
* **Risks (1 page max):** Discuss what risks you can anticipate for users of your application from using machine learning for the features in the applications (e.g., safety, fairness). Identify at least two risks for users of your application, estimate likelihood and severity, and discuss how you could reduce or fully mitigate the risk. (You do not need to implement the mitigations.)
* **Production challenges (1 page max):** Discuss any technical challenges you anticipate if you want to deploy this feature in production (e.g., scalability, operating costs) and how you would change your implementation if you expected millions of users. Identify at least two technical production challenges you can anticipate and discuss corresponding potential solutions. (You do not need to implement the solutions.)

Make sure your document is clearly structured, such that it is recognizable which answer belongs to which question. Ideally, you answer each question on a separate page, which makes our lives easier for grading. In Gradescope map each question to the corresponding page (see “Assign” in the [Gradescope documentation](https://gradescope-static-assets.s3.amazonaws.com/help/submitting_hw_guide.pdf)).

In this and all future assignments, page limits are recommendations and not strictly enforced. You can exceed the page limit if there is a good reason. We prefer precise and concise answers over AI slop and long and rambling ones.


## Grading

**Important:** Please read the grading specifications carefully. As explained in the syllabus, we grade each specification below pass/fail. That is, there is no partial credit when not fully meeting all parts of the specification and no extra credit for going beyond the specification. For example, if the document is clearly structured but you do not map questions to the relevant pages in Gradescope, you will lose the full 10 points for the first specification. You can make up for lost points by resubmitting the assignment later, using some of your tokens, as described in the syllabus. 

The grading specifications should be clear enough that you should be able to evaluate yourself with high confidence whether your solution meets the specification. If you are not sure what is expected of you, please ask. In this, as in all future assignments, we are happy to answer clarification questions about the grading specifications. 

The assignment is worth 100 points. We will assign credit as follows:

* 10p: The report is clearly structured, such that it is clear which text belongs to which question. The document includes a link to a specific *commit* in your GitHub repository *created with GitHub classroom*. When uploading the solution to Gradescope, questions are mapped to the relevant pages.
* 10p: We can install and run your implementation based on the descriptions in the `README.md` file (including instructions for dependencies and API creditials if needed).
* 5p: No private credentials are committed to the GitHub repository, including its history.
* 15p: The report describes how message recap is implemented and we can find the corresponding implementation. An LLM was used in the implementation. The application is functional in that it generates a summary every time a user requests recap. A video is recorded showing how a user will use the feature in the user interface.
* 15p: The report describes how topic title improver is implemented and we can find the corresponding implementation. An LLM was used in the implementation. The application is functional in that it suggests improved topic titles based on recent messages when topic drift is detected. A video is recorded showing how a user will use the feature in the user interface.
* 10p: In the recitation, the student is able to walk through their code changes and explains why they make the changes and how the changes map to the user experience.
* 5p: If you use any forms of AI coding assistance, an AI usage history should be provided. This should include (a) history that is automatically logged using the provided extension, and (b) any AI conversations that happen outside of the development environment.
* 10p: The report makes plausible recommendations of how to design the user interaction for the two new features, using the concepts automate, prompt, organize, annotate and hybrid introduced in class/readings. The recommendation is justified and the justification explicitly considers forcefulness, frequency, value, and cost. The answer makes clear whether the implementation corresponds to the recommendation and explains needed changes if it does not.
* 10p: The report makes a good faith attempt at discussing at least two possible risks of the application, as currently implemented. The discussion focuses on application-level concerns and risks to the users. It makes an attempt at estimating severity and likelihood of each risk. At least one potential solution is discussed for each risk. All discussed risks and solutions are plausible in the context of the application.
* 10p: The document makes a good faith attempt at discussing production challenges. The discussion focuses on production issues such as scalability or operation costs. At least two potential problem with the current implementation is identified. At least one potential solution is discussed for each identified problem. All discussed problems and solutions are plausible in the context of the application.


## Technical hints

#### Setting up the project

To set up the environment, follow the official [documentation](https://zulip.readthedocs.io/en/latest/development/setup-recommended.html). You will need to set up Git, GitHub, Docker and Vagrant. We recommend you develop with VScode using Remote development over SSH.

For development, you can directly edit files, and changes will be automatically reflected. For changes to the frontend, you might need to reload the page. Occasionally, you might need to restart the server (`./tools/run-dev`) to see changes implemented. For more details, please refer to the [development guide](https://zulip.readthedocs.io/en/latest/development/using.html).

#### Implementing new features

There are many web APIs that provide access to LLMs. You will typically have to sign up for an account. Some offer the API for free for a certain number of requests or at certain low request rates, some provide free credits for students -- this is sufficient to complete the assignment. We do not recommend to try to use an LLM locally, unless that's something you want to try anyway. When we tested the assignment, we had good experiences with the [Gemini API](https://ai.google.dev) (free, no credit card required).

Never commit private credentials (such as API keys) to a public Git repository. A common strategy is to write credentials into a file (e.g., `api.key`), read the key from the file at runtime, add that file to the `.gitignore` file to avoid committing it accidentally, and add instructions to the README of how to obtain a key and how write it into a file. Alternatively it is common to pass API keys as environment variables. If you accidentally commit a key and push this to a public repository, you will need to revoke the key and create a new one; if you have not yet pushed the changes you can go the nontrivial route of [rewriting the git history](https://stackoverflow.com/questions/872565/remove-sensitive-files-and-their-commits-from-git-history). When we evaluate your submission, we will use our own API keys.

#### AI-assisted development
This [tutorial](https://github.com/skills/getting-started-with-github-copilot) might be useful for getting yourself familiar with AI-assisted development if you have not used GitHub Copilot before.


