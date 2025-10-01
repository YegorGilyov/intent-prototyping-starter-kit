# Intent Prototyping Starter Kit

Welcome to the official starter kit for the **Intent Prototyping** method. This repository provides everything you need to go from a rough sketch to a live, interactive, and structurally sound React prototype using the power of modern AI tools.

## What is Intent Prototyping?

Intent Prototyping is a method for AI-assisted prototyping that bridges the gap between a design idea and a live, interactive prototype. It rejects the ambiguity of "vibe coding" and the limitations of static mockups by centering the development process on a clear, explicit, and holistic expression of the designer's **intent**.

This *intent* is captured in a set of documents that typically includes:
1.  **Conceptual Model**: Defines the objects, attributes, and relationships within the system.
2.  **Visualization**: Low-fidelity sketches of the user interface.
3.  **Flow**: Descriptions of user journeys and interactions.

By providing this complete blueprint to an AI coding agent, we can rapidly generate a robust, functional prototype that is built on a solid foundation. This approach is particularly effective for complex, data-heavy applications where structural integrity is the biggest risk.

The key benefits are:
-   **Learn Faster**: Go from an idea to a testable, interactive prototype in days, not weeks.
-   **Gain Confidence**: Validate the core logic and user flows with real interactions, not just clicks on static pictures.
-   **Enforce Clarity**: A live prototype cannot hide a flawed or ambiguous conceptual model.
-   **Improve Handoff**: The documented intent serves as a clear and durable source of truth for the engineering team.

For more materials, updates, and discussions on the method, please visit the central hub on my personal website:
-   **[yegorgilyov.name/intent-prototyping](https://yegorgilyov.name/intent-prototyping/)**

## What's Inside This Kit?

This repository is a complete toolkit to get you started:

*   **`/boilerplate`**: A minimal, pre-configured React project built with Vite, TypeScript, Ant Design, and Zustand. It's the clean slate for your next prototype.
*   **`/prompts`**: A "cookbook" of reusable, high-quality prompts for each step of the workflow, designed to work with multimodal AI models like Gemini, Claude, or GPT-4.
*   **`/example-reality-check`**: A complete, working example project (the "Reality Check" app from the article) included as a Git submodule. Use it as a reference to see how all the pieces fit together.

## Getting Started

### Prerequisites

1.  **Node.js**: Make sure you have Node.js (v18 or higher) installed.
2.  **Git**: This one's a given!
3.  **AI Tooling**: Access to a multimodal AI model and an agentic coding tool. The article uses Google AI Studio and Gemini CLI, but tools like Claude Code or Cursor will also work.

### 1. Clone the Starter Kit

Clone this repository to your local machine. Use the `--recurse-submodules` flag to ensure the `example-reality-check` project is cloned as well.

```bash
git clone --recurse-submodules https://github.com/YourGitHubUsername/intent-prototyping-starter-kit.git
cd intent-prototyping-starter-kit
```
> **Note:** If you forgot the flag, you can run `git submodule update --init --recursive` inside the repository to fetch the example project.

### 2. Set Up Your Project

Copy the `/boilerplate` directory to create your new project.

```bash
# For macOS / Linux
cp -r boilerplate/ my-new-prototype/

# For Windows
xcopy boilerplate my-new-prototype /E /I
```

Navigate into your new project folder and install the dependencies.

```bash
cd my-new-prototype
npm install
```

### 3. Run the Development Server

You now have a running React application!

```bash
npm run dev
```

You're all set! Now you can start the Intent Prototyping workflow.

---

## Stay in Touch

[**➡️ Subscribe to updates on my website**](https://yegorgilyov.name/)
