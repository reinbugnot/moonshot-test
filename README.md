<div align="center">

![Moonshot Logo](https://github.com/moonshot-admin/moonshot/raw/new_dev_main/misc/aiverify-moonshot-logo.png)

**Version 0.1.7**

A simple and modular tool to evaluate any LLM application.

[![Python 3.11](https://img.shields.io/badge/python-3.11-green)](https://www.python.org/downloads/release/python-3111/)


</div>

<b>Motivation </b>

Developed by the [AI Verify Foundation](https://aiverifyfoundation.sg/), Project Moonshot is one of the first tools to bring [Benchmarking](#benchmarking-with-moonshot) and [Red-Teaming](#red-teaming-with-moonshot) together to help AI developers, compliance teams and AI system owners <b>evaluate LLMs and LLM applications</b>.

In this initial version, Moonshot can be used through several interfaces:
- User-friendly Web UI - [Web UI User Guide]()
- Interactive Command Line Interface - [CLI User Guide]()
- Seamless Integration into your MLOps workflow via Moonshot Library APIs or Moonshot Web APIs - [Notebook Examples](), [Web API Docs]()

</br>

## Getting Started
</br>

### ✅ Prerequisites
1. [Python 3.11](https://www.python.org/downloads/) (We have yet to test on later releases)

2. [Git](https://github.com/git-guides/install-git)

3. Virtual Environment (This is optional but we recommend you to separate your dependencies)

    ```
    # Create a virtual environment
    python -m venv venv

    # Activate the virtual environment
    source venv/bin/activate
    ```
4. If you plan to install our Web UI, you will also need [Node.js verion 20.11.1 LTS](https://nodejs.org/en/blog/release/v20.11.1) and above
</br>

### ⬇️ Installation

To install Project Moonshot's full functionalities:

```
# Install Project Moonshot's Python Library
pip install "aiverify-moonshot[all]"

# Clone and install test assets and Web UI
python -m moonshot -i moonshot-data -i moonshot-ui
```
Check out our [Installation Guide]() for a more details.

If you are having installation issues, see the [Troubleshooting Guide]().
<details>
<summary><b>Other installation options</b></summary>
Here's a summary of other installation commands available:

```
# To install Moonshot library APIs only
pip install aiverify-moonshot

# To install Moonshot's full functionalities (Library APIs, CLI and Web APIs)
pip install "aiverify-moonshot[all]"

# To install Moonshot library APIs and Web APIs only
pip install "aiverify-moonshot[web-api]"

# To install Moonshot library APIs and CLI only
pip install "aiverify-moonshot[cli]"

# To install from source code (Full functionalities)
git clone git@github.com:aiverify-foundation/moonshot.git
cd moonshot
pip install -r requirements.txt
```
⚠️ You will need to have test assets from [moonshot-data](https://github.com/aiverify-foundation/moonshot-data) before you can run any tests.

🖼️ If you plan to install our Web UI, you will also need [moonshot-ui](https://github.com/aiverify-foundation/moonshot-ui)

Check out our [Installation Guide]() for a more details.
</details>
</br>

### 🏃‍♀️ Run Moonshot

#### Web UI
To run Moonshot Web UI:
```
python -m moonshot web
```
Open [http://localhost:3000/](http://localhost:3000/) in a browser and you should see:
![Moonshot UI Home](./misc/aiverify-moonshot-UI.png)


#### Interactive CLI
To run Moonshot CLI:
```
python -m moonshot cli interactive
```
![Moonshot cli](./misc/aiverify-moonshot-CLI.png)


</br></br>

## User Guides
Check out our user guides for step-by-step walkthrough of each interface type.

[Getting Started with Moonshot Web UI]()

[Getting Started with Moonshot Interactive CLI]()

[Moonshot Library Python Notebook Examples]()

[Using Moonshot Web APIs]()


</br></br>

## Key Features

To get started with Moonshot, we recommend reading the following section, which provides a high-level overview of Moonshot's key features. For more detailed information, a comprehensive documentation can be found [here]().

</br>

### 🔗 Accessing the AI system to be tested

Moonshot provides ready access to test LLMs from popular model providers E.g., OpenAI, Anthropic, Together, HuggingFace. You will just need to provide your API Key. [See Model Connectors Available](). 

If you are testing other models or your own LLM Application hosted on a custom server, you will need to create your own Model Connector. Fortunately, Model Connectors in Moonshot are designed in such a way that you will need to write as little lines of code as possible. [How to create a custom model connector](). 

</br>

### 📊 Benchmarking with Moonshot

Benchmarks are “Exam questions” to test the model across a variety of competencies, e.g., language and context understanding. 

Project Moonshot offers a range of benchmarks to measure your LLM application's performance in Capability, Quality, and Trust & Safety. These include benchmarks widely used by the community like Google's BigBench and HuggingFace's leaderboards, and more domain/task specific tests like Tamil Language and Medical LLM benchmarks. 

The AI Verify Foundation is also partnering [MLCommons](https://mlcommons.org/) to develop globally aligned safety benchmarks for LLMs. Currently, you will be able to run v0.5 of the Safety Baseline Benchmark using Project Moonshot.

Check out the full list of tests [here](https://github.com/aiverify-foundation/moonshot-data).

* ✨ <b>Run only the most relevant tests</b>

Moonshot helps you identify and run only the most relevant tests, optimizing the testing process. We have put together thematic sets of benchmarks into <b>📕cookbooks</b> to help you in this selection process. Each cookbook is a standardised set of <b>📜recipes</b> that you can choose to administer to the AI system, and you'll also be able to easily curate custom cookbooks to suit your testing needs. See [How to create a custom cookbook]().


* ✨ <b>Adding custom tests</b>

You can also tailor your evaluation process with custom datasets, to evaluate AI Systems for unique use cases. To do so, you can easily create your own <b>📜recipes</b> in Moonshot. See [How to create a custom recipe]().

![Recipe Example](./misc/recipe-example.png)

<details><summary>📜More about Recipes</summary>

A Recipe consists of 2 essential components:
1. <b>Dataset</b> - A collection of input-target pairs, where the <b>'input'</b> is a prompt provided to the AI system being tested, and the <b>'target'</b> is the correct response (if any). 
2. <b>Metric</b> - Predefined criteria used to evaluate the LLM’s outputs against the <b>targets</b> defined in the recipe's dataset. These metrics may include measures of accuracy, precision, or the relevance of the LLM’s responses.
3. <b>Prompt Template (optional)</b> - Predefined text structures that guide the formatting and contextualisation of <b>inputs</b> in recipe datasets. </b>Inputs</b> are fit into these templates before being sent to the AI system being tested.
4. <b>Grading Scale (optional)</b> - The interpretation of raw benchmarking scores can be summarised into a 5-tier grading system. Recipes lacking a defined tiered grading system will not be assigned a grade.

[More about recipes]().

</details>
<br/>

* ✨ <b>Interpreting test results</b>

Using Moonshot's Web UI, you can produce a [HTML report]() that visualises your test results in easy-to-read charts. You can also conduct a deeper analysis of the raw test results through the [JSON Results]() or the [Database]() that logs the full prompt-response pairs.

![Report Example Chart](./misc/report-example-chart.png)

</br>

### ☠️ Red Teaming with Moonshot

Red-Teaming is the adversarial prompting of LLM applications to induce them to behave in a manner incongruent with their design. This process is crucial to identify vulnerabilities in AI systems.

Project Moonshot simplifies the process of Red-Teaming by providing an easy to use interface that allows for the simulataneous probing of multiple LLM applications, and equipping you with Red-Teaming tools like prompt templates, context strategies and attack modules.

![Red Teaming UI](./misc/redteaming-ui.png)

* ✨ <b>Automated Red Teaming</b>

As Red-Teaming conventionally relies on human ingenuity, it is hard to scale. Project Moonshot has developed some attack modules based on research-backed techniques that will enable you to automatically generate adversarial prompts.

[View attack modules available]().


</br></br>

## License
Licensed under [Apache Software License 2.0](https://www.apache.org/licenses/LICENSE-2.0.txt)
