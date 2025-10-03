# Complete Manual of the Meta‑Language for Interaction with AI Models

## Introduction

The **meta‑language for interacting with AI models** is a collection of **standardized commands** designed to structure and clarify communication with artificial intelligence systems. Its purpose is to reduce ambiguity in requests, facilitate task reuse, allow the composition of complex processes and ensure more coherent results. Unlike a traditional programming language, this meta‑language **does not execute code**, but **orchestrates the model’s behaviour** by describing the user's intent precisely.

This document comprehensively covers all **commands available to date** (preliminary version 0.2), together with a detailed explanation, a guide to permitted modifiers and complete usage examples.

## Principles and Benefits

The meta‑language is based on the following principles:

1. **Clarity and transparency:** the intention is expressed explicitly using a main verb (the command) and optional parameters.
2. **Modularity and reusability:** commands can be combined or chained to build more complex processes that can then be reused in different contexts.
3. **Standardization:** a uniform syntax makes it easier to understand requests between different models and users.
4. **Flexibility:** modifiers can be added to adjust the level of depth, the output format or specific analysis parameters.

Adopting this meta‑language provides benefits such as:

- **Greater consistency** in AI responses.
- **Ease of debugging and optimizing** long or complex prompts.
- **Unified communication** between different models and people.

## General Syntax

Each command follows a common structure:

```text
COMMAND: "input or prompt" --modifier1=value --modifier2=value
```

Where:

- **COMMAND** is an uppercase keyword indicating the desired action.
- **Input** (prompt) is the text, question or description to be processed. It is usually written in quotes to delimit spaces or complex strings. If the input is very long, it may be placed on multiple lines immediately after the command.
- **Modifiers** (optional) are prefaced with `--` and allow fine‑tuning of how the command is executed. Their syntax is `--key=value`. If the key repeats or the modifier accepts multiple values, it can be repeated or separated by commas.

The meta‑language **does not distinguish** between uppercase and lowercase in modifiers, but **does distinguish** the command name. Modifiers are preferably written in lowercase for readability.

### Chaining Commands

To perform multiple operations in sequence, use the special command `CHAIN`. Inside a `CHAIN` block, list other commands on separate lines, respecting indentation to improve readability. The result of each step is used as input to the next unless otherwise specified.

Example:

```text
CHAIN:
    SEARCH: "impact of remote work on productivity Spain 2024" --sources=news,scholar
    ANALYZE: search results
    COMPARE: business models according to profitability
    GENERATE: report with conclusions in Markdown format
```

## Commands of the Meta‑Language

Below, each of the available commands is detailed. Each section includes a description, general syntax, common modifiers and practical usage examples.

### 1. `ANALYZE`

**Description:** This command asks the model to examine text, data or information with a specific goal: identify patterns, extract metrics, evaluate sentiment, decompose arguments, etc. Useful for reports, sentiment analysis, trend identification or error detection.

**General syntax:**

```text
ANALYZE: "text or data to analyze" --focus=type_of_analysis --method=methodology --output=format
```

**Common modifiers:**

- `--focus`: defines the focus of the analysis (e.g. `sentiment`, `structural`, `thematic`, `statistical`).
- `--method`: allows you to specify the desired methodology (e.g. `deterministic`, `heuristic`, `comparative`).
- `--output`: indicates the output format of the analysis (`summary`, `table`, `list`).

**Examples:**

1. *Sentiment analysis of a comment.*

    ```text
    ANALYZE: "This product does not meet my expectations. The quality leaves a lot to be desired and the delivery was slow." --focus=sentiment --output=summary
    ```

    *Expected result:* the model returns a brief sentiment analysis identifying negative emotions (frustration with the quality and delay in shipping), as well as possible suggestions for improvement.

2. *Structural analysis of a scientific article.*

    ```text
    ANALYZE: "[Insert a paragraph from the scientific article here]" --focus=structural --method=descriptive --output=table
    ```

    *Expected result:* a table identifying sections of the article (introduction, methods, results, discussion) with a brief synthesis of each part and word count.

3. *Statistical analysis of a set of tabular data.*

    ```text
    ANALYZE:
        """
        Year, Sales
        2021, 12000
        2022, 15500
        2023, 17800
        """
    --focus=statistical --method=mean,variance --output=list
    ```

    *Expected result:* the model calculates metrics such as mean, annual growth and standard deviation, delivering the list of values with interpretation.

### 2. `COMPARE`

**Description:** Evaluates similarities and differences between two or more elements (texts, products, policies, ideas). It can be used to make decisions, assess advantages and disadvantages or identify the best alternative according to certain criteria.

**General syntax:**

```text
COMPARE: "element1" "element2" --criteria=list_of_criteria --output=format
```

**Common modifiers:**

- `--criteria`: list of comparison criteria (e.g. `price,efficiency,sustainability`).
- `--output`: specifies the output format (`table`, `summary`, `list`).
- `--weight`: relative weights can be added to the criteria (e.g. `price:0.5,efficiency:0.3,environment:0.2`).

**Examples:**

1. *Compare two programming languages by popularity and ease of learning.*

    ```text
    COMPARE: "Python" "Rust" --criteria=popularity,ease_of_learning --output=table
    ```

    *Expected result:* a table showing the popularity (for example, usage indexes) and ease of learning (learning curve) of each language. The table could include a qualitative score (high, medium, low) and a brief comment.

2. *Compare cloud service providers.*

    ```text
    COMPARE: "AWS" "Azure" "Google Cloud" --criteria=price,services,support --weight=price:0.5,services:0.3,support:0.2
    ```

    *Expected result:* a weighted comparison where price has greater influence. The system may suggest which provider best fits the established priorities.

### 3. `SUMMARIZE`

**Description:** Generates a concise and structured summary of text, highlighting the key points. It is useful to get an overview of long documents, reports or news.

**General syntax:**

```text
SUMMARIZE: "text to summarize" --length=short|medium|long --style=formal|informal --output=format
```

**Common modifiers:**

- `--length`: determines the desired length of the summary (short, medium, long).
- `--style`: adjusts the tone (formal, informal, technical, popular_science).
- `--output`: output format (`paragraph`, `bullets`).

**Examples:**

1. *Brief summary of a news article.*

    ```text
    SUMMARIZE: "The article describes the evolution of remote work in Spain since 2019, analyzing how companies and workers have adapted to this mode and the changes in legislation..." --length=short --style=popular_science --output=bullets
    ```

    *Expected result:* three or four key points presented as bullet points, including adoption figures, main advantages and challenges, and regulatory changes.

2. *Detailed summary of a novel.*

    ```text
    SUMMARIZE: "[Synopsis or chapter of the novel]" --length=long --style=informal --output=paragraph
    ```

    *Expected result:* a summary of several lines that relates the main events, characters and endings, maintaining an engaging tone.

### 4. `EVALUATE`

**Description:** Assesses the quality, feasibility or impact of text, a proposal or a project. It may consider criteria such as accuracy, credibility, ethics, risk or cost.

**General syntax:**

```text
EVALUATE: "proposal or text" --criteria=list_of_criteria --scale=scoring_scale --output=format
```

**Common modifiers:**

- `--criteria`: evaluation criteria (`feasibility`, `sustainability`, `cost`, `benefit`).
- `--scale`: defines the scoring scale (`1-5`, `low-medium-high`).
- `--output`: indicates whether a `table`, `commentary` or `list` is desired.

**Examples:**

1. *Evaluate the feasibility of a new product.*

    ```text
    EVALUATE: "Proposal: design an app for users to exchange clothes in a medium‑sized city" --criteria=market,competition,cost --scale=1-10 --output=table
    ```

    *Expected result:* a table assigning a score from 1 to 10 to each criterion and briefly justifying each valuation.

2. *Evaluate the credibility of a viral news story.*

    ```text
    EVALUATE: "It has been rumored that a famous restaurant chain has been acquired by an unknown fund" --criteria=reliability,sources --scale=low-medium-high --output=commentary
    ```

    *Expected result:* an analytical comment on the credibility of the news, citing whether there are verifiable sources and pointing out red flags (clickbait, lack of evidence).

### 5. `REFINE`

**Description:** Improves or rewrites a text while preserving its meaning but enhancing its clarity, style, tone or precision. It is used to polish drafts, correct grammar or adapt the voice to a specific audience.

**General syntax:**

```text
REFINE: "text to improve" --style=desired_style --clarity=degree --length=short|medium|long
```

**Common modifiers:**

- `--style`: desired style (`professional`, `friendly`, `academic`, `informal`).
- `--clarity`: intensity of the improvement (`high`, `medium`, `low`). A high value implies deeper rewriting.
- `--length`: adjustment of relative length compared to the original.

**Examples:**

1. *Refine an informal email to give it a professional tone.*

    ```text
    REFINE: "Hi, just wanted to say the report is a bit slow, but anyway, have a look whenever you can" --style=professional --clarity=high
    ```

    *Expected result:* a text with a more formal tone, clarity on deadlines and without colloquial expressions.

2. *Rewrite an academic paragraph more concisely.*

    ```text
    REFINE: "In the present research, we evaluate different machine learning methodologies applied to anomaly detection" --style=academic --clarity=medium --length=short
    ```

    *Expected result:* a more concise text, maintaining the academic register.

### 6. `CHAIN`

**Description:** Allows you to execute a sequence of commands where the output of one step is used as input to the next. It is useful for complex workflows such as searching for information, analyzing it and then generating a report.

**General syntax:**

```text
CHAIN:
    COMMAND1: "input1" --modifiers
    COMMAND2: "input2" --modifiers
    ...
```

**Modifiers:** `CHAIN` does not accept its own modifiers, but each subcommand may have its own.

**Examples:**

1. *Find information, analyze it and summarize it.*

    ```text
    CHAIN:
        SEARCH: "impact of artificial intelligence on employment" --sources=news --limit=10
        ANALYZE: search results --focus=thematic --output=summary
        SUMMARIZE: analysis --length=short --output=bullets
    ```

    *Expected result:* The first command searches current news; the second analyzes the main themes of the results; the third summarizes the analysis into key points.

2. *Compare products after searching for them on the internet.*

    ```text
    CHAIN:
        SEARCH: "best robot vacuums 2025" --sources=reviews,news
        SUMMARIZE: search results --length=medium
        COMPARE: "RobotA" "RobotB" --criteria=price,autonomy,power --output=table
    ```

    *Expected result:* a comparative table generated after identifying relevant models through the search and summary.

### 7. `GENERATE`

**Description:** Creates new content from a description, instructions or data. It can be used to write articles, generate code, design curricula, create stories or offer creative solutions.

**General syntax:**

```text
GENERATE: "instructions or description" --type=type_of_content --style=tone --length=short|medium|long --format=format
```

**Common modifiers:**

- `--type`: specifies the type of content (`article`, `report`, `code`, `story`, `plan`).
- `--style`: defines the tone (`formal`, `informal`, `academic`, `creative`).
- `--length`: controls the desired length.
- `--format`: output format (`paragraph`, `bullets`, `markdown`, `json`).

**Examples:**

1. *Generate a curriculum plan for web programming.*

    ```text
    GENERATE: "curriculum plan to learn web development from scratch" --type=plan --style=professional --length=long --format=markdown
    ```

    *Expected result:* a detailed plan in Markdown format that includes modules, weeks, recommended resources and exercises, with an educational tone.

2. *Create a short science fiction story.*

    ```text
    GENERATE: "a short story about a robot that discovers emotions" --type=story --style=creative --length=medium --format=paragraph
    ```

    *Expected result:* a story of several lines that narrates the experiences of a robot with an emotional and creative touch.

### 8. `EXPAND`

**Description:** Expands a short text by adding details, context or development of ideas. It is useful to extend descriptions, enrich reports or complete arguments.

**General syntax:**

```text
EXPAND: "short text" --depth=depth --style=tone --length=target
```

**Common modifiers:**

- `--depth`: level of depth to add (`low`, `medium`, `high`).
- `--style`: tone of writing.
- `--length`: desired length after expansion.

**Examples:**

1. *Expand a simple definition.*

    ```text
    EXPAND: "Artificial intelligence is a branch of computer science that..." --depth=high --style=academic --length=long
    ```

    *Expected result:* a more extensive text that includes historical background, application areas and challenges.

2. *Develop a short argument.*

    ```text
    EXPAND: "Remote work has advantages for work-life balance" --depth=medium --style=popular_science --length=medium
    ```

    *Expected result:* a paragraph that explains why remote work facilitates work-life balance, with examples and data.

### 9. `TRANSLATE`

**Description:** Translates a text from one language to another. Modifiers can adjust the tone or indicate the type of translation (literal, free). It also serves to detect the original language if not specified.

**General syntax:**

```text
TRANSLATE: "text to translate" --from=source_language --to=target_language --tone=tone
```

**Common modifiers:**

- `--from`: source language (optional if the model can detect it automatically). Example: `es` for Spanish, `en` for English.
- `--to`: target language. This must be specified if a language other than the default is desired.
- `--tone`: desired register (`formal`, `neutral`, `colloquial`).

**Examples:**

1. *Translate from English to Spanish.*

    ```text
    TRANSLATE: "Artificial intelligence is transforming the way companies operate" --from=en --to=es --tone=neutral
    ```

    *Expected result:* a translation into Spanish maintaining a neutral tone and fidelity to the original content.

2. *Translate a text into German with a formal tone.*

    ```text
    TRANSLATE: "Thank you for your attention to this matter" --to=de --tone=formal
    ```

    *Expected result:* the same message in German with a formal register appropriate for letters or professional emails.

### 10. `SIMPLIFY`

**Description:** Rewrites a complex or technical text in simpler terms without losing meaning. Suitable for explaining scientific concepts to general audiences or adapting documents for children.

**General syntax:**

```text
SIMPLIFY: "complex text" --audience=audience --tone=friendly|neutral --length=short|medium|long
```

**Common modifiers:**

- `--audience`: defines the target audience (children, students, general public).
- `--tone`: can be `friendly`, `neutral`, etc.
- `--length`: adjusts the length of the simplified text.

**Examples:**

1. *Explain quantum mechanics to high school students.*

    ```text
    SIMPLIFY: "Quantum mechanics describes the behavior of matter and energy at very small scales..." --audience=students --tone=friendly
    ```

    *Expected result:* an explanation with simple analogies and avoiding technical jargon.

2. *Simplify a technical manual for inexperienced users.*

    ```text
    SIMPLIFY: "To configure the router, access the administration interface using the default IP address..." --audience=general_public --tone=neutral
    ```

    *Expected result:* step‑by‑step instructions simplified with everyday language.

### 11. `STRUCTURE`

**Description:** Organizes information into clear structures such as tables, lists, hierarchical schemes or comparative charts. It facilitates reading and data analysis.

**General syntax:**

```text
STRUCTURE: "content to structure" --output=structure_type --columns=col1,col2,... --sort=key
```

**Common modifiers:**

- `--output`: can be `table`, `list`, `tree`, `hierarchy`.
- `--columns`: in case of a table, defines the columns to display.
- `--sort`: sorts the structure by a specific key.

**Examples:**

1. *Create a table of the main capitals of Europe.*

    ```text
    STRUCTURE: "List of the capitals of Europe with their countries and approximate population" --output=table --columns=Country,Capital,Population
    ```

    *Expected result:* a table with columns for country, capital and population, sorted alphabetically.

2. *Generate a hierarchical list of course topics.*

    ```text
    STRUCTURE: "Topics: Introduction, Fundamentals, Advanced; each with subtopics" --output=tree
    ```

    *Expected result:* a tree diagram where each main topic contains its subtopics at different levels.

### 12. `FORMAT`

**Description:** Adapts the output of text or information to the desired format. It can be used to convert content to Markdown, JSON, CSV, HTML, PDF (when the environment allows) or other specific formats.

**General syntax:**

```text
FORMAT: "content" --to=target_format --style=options
```

**Common modifiers:**

- `--to`: target format (`markdown`, `json`, `html`, `csv`).
- `--style`: specifies styles or particular templates (for HTML or Markdown, predefined templates can be indicated).

**Examples:**

1. *Format a list into JSON.*

    ```text
    FORMAT: "Item1, Item2, Item3" --to=json
    ```

    *Expected result:* a JSON structure with a list of items: `["Item1", "Item2", "Item3"]`.

2. *Convert a report to Markdown with headings.*

    ```text
    FORMAT: "Annual performance report: Sales increase by 15%, expenses decrease..." --to=markdown --style=headings
    ```

    *Expected result:* a Markdown document with structured titles and subtitles.

### 13. `OPTIMIZE`

**Description:** Improves the efficiency, clarity or effectiveness of an existing prompt, code or plan. It is used to refine instructions, remove redundancies, simplify algorithms or increase the performance of a text (without changing its general purpose).

**General syntax:**

```text
OPTIMIZE: "prompt or code" --target=efficiency|clarity --constraints=constraints
```

**Common modifiers:**

- `--target`: optimization goal (`efficiency`, `clarity`, `brevity`).
- `--constraints`: constraints to respect (for example, maintain the same functionality or maximum length).

**Examples:**

1. *Optimize an extensive prompt to make it more concise.*

    ```text
    OPTIMIZE: "Generate a detailed summary, with examples and conclusions, of this 20‑page document..." --target=brevity
    ```

    *Expected result:* a shorter prompt that maintains clarity of objective and avoids ambiguities.

2. *Optimize a piece of pseudocode.*

    ```text
    OPTIMIZE:
        """
        for each number in the list:
            if the number is even:
                add to even_list
        sort even_list
        return even_list
        """
        --target=efficiency
    ```

    *Expected result:* revised code that combines identifying even numbers with sorting more efficiently or uses an appropriate data structure.

### 14. `CONNECT`

**Description:** Establishes relationships between concepts, ideas, sources or topics, showing how they are linked and what implications they have. It is useful for mapping knowledge, detecting influences or discovering shared contexts.

**General syntax:**

```text
CONNECT: "concept1" "concept2" ... --type=connection_type --depth=depth
```

**Common modifiers:**

- `--type`: type of connection (`causal`, `thematic`, `temporal`, `geographical`).
- `--depth`: level of detail of the link (`superficial`, `intermediate`, `deep`).

**Examples:**

1. *Connect the theory of relativity with quantum mechanics.*

    ```text
    CONNECT: "Theory of Relativity" "Quantum Mechanics" --type=thematic --depth=intermediate
    ```

    *Expected result:* an explanation of the differences and points of convergence between both theories, indicating where they collide and how they have been attempted to be unified.

2. *Relate two literary works.*

    ```text
    CONNECT: "1984" "Brave New World" --type=thematic --depth=deep
    ```

    *Expected result:* an analysis exploring how both science fiction novels deal with topics of social control, individual freedom and dystopian futures.

### 15. `VISUALIZE`

**Description:** Requests graphic representations, diagrams, concept maps or data visualizations. Depending on the environment, it may generate charts (bar, line, pie), flowcharts, mind maps or infographics.

**General syntax:**

```text
VISUALIZE: "data or description" --type=visualization_type --title=title --labels=labels
```

**Common modifiers:**

- `--type`: type of visualization (`bar`, `line`, `pie`, `flowchart`, `concept_map`).
- `--title`: title of the graph or diagram.
- `--labels`: labels for axes or categories, separated by commas.

**Examples:**

1. *Generate a bar chart of monthly sales.*

    ```text
    VISUALIZE:
        """
        Month, Sales
        January, 120
        February, 140
        March, 160
        April, 180
        """
        --type=bar --title="Monthly Sales" --labels=Month,Sales
    ```

    *Expected result:* a bar chart showing the evolution of sales from January to April.

2. *Create a flowchart of a purchase process.*

    ```text
    VISUALIZE: "Online purchase process: product selection → add to cart → payment → confirmation" --type=flowchart --title="Purchase Flow"
    ```

    *Expected result:* a flowchart with the stages of the process and arrows connecting them.

### 16. `VALIDATE`

**Description:** Checks the accuracy, consistency or truthfulness of information. It can be used to see if data complies with certain rules, if an argument is logically sound or if a statement matches reliable sources.

**General syntax:**

```text
VALIDATE: "statement or data" --rules=rules --sources=sources
```

**Common modifiers:**

- `--rules`: rules or conditions to verify (e.g. `greater_than_0`, `no_duplicates`).
- `--sources`: reliable sources to cross‑reference the information (`news`, `papers`, `studies`).
- `--output`: output format (`valid/invalid + explanation`, `score`).

**Examples:**

1. *Validate that a list of numbers contains no duplicates.*

    ```text
    VALIDATE: "1, 2, 3, 4, 2" --rules=no_duplicates --output=explanation
    ```

    *Expected result:* duplicates are detected and the rule is flagged as not met, explaining which elements are repeated.

2. *Verify the truth of a historical fact.*

    ```text
    VALIDATE: "The first person to travel into space was Neil Armstrong" --sources=papers,news --output=result
    ```

    *Expected result:* a result indicating the statement is false (the first person was Yuri Gagarin) and citing the sources consulted.

### 17. `DEBUG`

**Description:** Detects errors or inconsistencies in code, text, a plan or any content that may contain faults. It suggests concrete solutions or corrections for each issue found.

**General syntax:**

```text
DEBUG: "code or text" --context=language_or_environment --output=format
```

**Common modifiers:**

- `--context`: specifies the programming language or type of document (`python`, `javascript`, `writing`, `project_plan`).
- `--output`: output format (`list`, `inline_comments`).

**Examples:**

1. *Find errors in a Python code snippet.*

    ```text
    DEBUG:
        """
        def sum_numbers(lst):
            total = 0
            for number in lst:
                total += number
            return total
        print(sum_numbers([1,2,3]))
        print(sum_numbers("123"))
        """
        --context=python --output=list
    ```

    *Expected result:* a list pointing out that the second `print` will raise an error because the function expects a list of numbers, not a string.

2. *Review a project plan for inconsistencies.*

    ```text
    DEBUG: "Plan: Start in June, delivery in May" --context=project_plan --output=inline_comments
    ```

    *Expected result:* a comment pointing out the inconsistency of dates and suggestions to correct them.

### 18. `EXPLAIN`

**Description:** Breaks down the operation of a concept, algorithm or process step by step, providing clarity and depth. It is useful for teaching, documentation and understanding complex systems.

**General syntax:**

```text
EXPLAIN: "concept or algorithm" --detail=detail_level --audience=audience_type
```

**Common modifiers:**

- `--detail`: level of detail (`basic`, `intermediate`, `advanced`).
- `--audience`: target audience (`students`, `professionals`, `general_public`).

**Examples:**

1. *Explain the quicksort algorithm.*

    ```text
    EXPLAIN: "Quicksort" --detail=intermediate --audience=students
    ```

    *Expected result:* an explanation of how Quicksort works, including pivot selection, partitioning and recursion, with simple examples.

2. *Describe the process of photosynthesis.*

    ```text
    EXPLAIN: "Photosynthesis" --detail=basic --audience=general_public
    ```

    *Expected result:* a text explaining how plants convert sunlight into energy, suitable for people without advanced scientific knowledge.

### 19. `SEARCH`

**Description:** Performs searches for information on the internet or external sources. It allows you to specify sources (news, academic articles, blogs, official sites), dates, languages and number of results. It is useful when updated data or verified information is needed.

**General syntax:**

```text
SEARCH: "query" --sources=sources --since=start_date --until=end_date --limit=number
```

**Common modifiers:**

- `--sources`: list of sources (`news`, `scholar`, `blogs`, `official`).
- `--since` / `--until`: date ranges for the search (`2024-01-01` to `2024-12-31`).
- `--limit`: maximum number of results.
- `--lang`: search language (`es`, `en`, `fr`).

**Examples:**

1. *Search for recent academic articles on artificial intelligence.*

    ```text
    SEARCH: "applications of artificial intelligence in medicine" --sources=scholar --since=2023-01-01 --limit=5 --lang=en
    ```

    *Expected result:* a list of the five most relevant articles published since January 2023 in English, with links and summaries.

2. *Track blog opinions about a new gadget.*

    ```text
    SEARCH: "review of gadget X" --sources=blogs --limit=10 --lang=en
    ```

    *Expected result:* links to blogs and highlighted reviews about the gadget, with a brief analysis of overall opinion.

### 20. `DESIGN`

**Description:** Designs or plans complex structures such as courses, projects, systems or strategies. It can internally combine several commands and allows specifying constraints and specific requirements.

**General syntax:**

```text
DESIGN: "description of the plan" --objective=objective --constraints=constraints --modules=modules --timeline=timeline
```

**Common modifiers:**

- `--objective`: defines the main objective of the design (for example, `create_course`, `business_plan`).
- `--constraints`: list of constraints (budget, time, limited resources).
- `--modules`: breaks the plan down into modules or phases.
- `--timeline`: indicates an approximate schedule or key dates.

**Examples:**

1. *Design an introductory cybersecurity course.*

    ```text
    DESIGN: "Introductory cybersecurity course" --objective=create_course --constraints=duration:8_weeks,budget:minimal --modules=basic_concepts,threats,defenses --timeline=8_weeks
    ```

    *Expected result:* an outline of the course with weekly modules, learning objectives, activities and evaluation criteria.

2. *Plan data migration to the cloud.*

    ```text
    DESIGN: "Plan to migrate all data to the cloud" --objective=migration_plan --constraints=budget:limited,time:3_months --modules=assessment,preparation,migration,validation --timeline=3_months
    ```

    *Expected result:* a plan with clear phases, required resources, timeline and potential associated risks.

## General Best Practices

1. **Define intent clearly:** choose the appropriate command and draft the input precisely. Avoid ambiguous instructions.
2. **Apply modifiers judiciously:** it is not necessary to use them all; select only those that improve the desired outcome.
3. **Chain only when necessary:** use `CHAIN` when several operations are required in a workflow. If the task is simple, a single command will suffice.
4. **Use `VALIDATE` and `EVALUATE` to check critical results:** when accuracy is key, validate or evaluate information before making decisions.
5. **Adjust tone and style with `STYLE` and other modifiers:** adapt the output to your audience (professional, informal, academic) to maximize the usefulness of the content.
6. **Review and optimize complex prompts:** if a command does not produce the expected result, use `OPTIMIZE` or `REFINE` to improve it.

## Conclusion

The meta‑language for interacting with AI models offers an **ordered and powerful** way to structure requests, facilitating more precise and coherent responses. By mastering these commands and their modifiers, you can design complex workflows, produce concise summaries, compare alternatives, generate creative content and much more.

This guide aims to be a complete reference for beginners and advanced users. Over time, new commands or modifiers may be added; therefore, it is advisable to version projects and review updated documentation.