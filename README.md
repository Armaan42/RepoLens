# RepoLens: AI-Powered Context-Aware Code Review Platform Using Retrieval-Augmented Generation

## Project Overview

The proposed project aims to develop an AI-powered platform that automatically reviews pull requests in software repositories and provides intelligent feedback to developers.

The system integrates Retrieval-Augmented Generation (RAG) and generative AI models to analyze code changes while considering the context of the entire repository. This project falls under the domain of Artificial Intelligence, Cloud-based Software Engineering, and DevOps Automation.

With the rapid growth of collaborative development on platforms such as GitHub, efficient code review has become essential for maintaining code quality and security. The platform will assist developers, engineering teams, and organizations by providing automated, context-aware code review suggestions during the development lifecycle.

## Problem Statement

Modern software development relies heavily on collaborative workflows where developers submit pull requests for integrating code changes. Manual code reviews are time-consuming, inconsistent, and highly dependent on the availability of experienced engineers. As software repositories grow larger and more complex, reviewers often lack full visibility of the entire codebase, leading to missed architectural inconsistencies, hidden bugs, and potential security vulnerabilities.

Existing automated code review tools typically analyze only the modified files within a pull request, without understanding the broader repository context. This limitation results in shallow or incomplete feedback that may not accurately reflect the impact of the code changes. Consequently, development teams experience delays, reduced productivity, and inconsistent code quality.

Therefore, there is a need for a scalable, intelligent system that can analyze pull requests with full repository context and generate structured, automated code reviews using advanced AI techniques.

## How the Problem Was Identified

The problem was identified through observation of common challenges faced by developers during collaborative software development. In many teams, pull requests remain open for long periods due to delays in manual code reviews. Developers often depend on senior engineers for review feedback, creating bottlenecks in the development workflow.

Further investigation revealed that existing automated tools provide limited contextual analysis because they evaluate only the changed files rather than the entire repository. Discussions within developer communities, technical blogs, and open-source forums also highlight the growing demand for intelligent developer tools that can assist with automated code analysis and review.

These observations indicated the need for a more advanced system capable of providing context-aware insights during the code review process.

## Objectives

- Design a web-based platform that integrates with GitHub repositories to automatically monitor and analyze pull requests.
- Develop a context-aware code review system using Retrieval-Augmented Generation (RAG) to analyze code changes in relation to the entire repository.
- Implement generative AI models to generate structured review feedback including summaries, issue detection, and improvement suggestions.
- Build a repository indexing and semantic search mechanism using vector embeddings to enable contextual understanding of the codebase.
- Evaluate the effectiveness of the system in improving code review efficiency and supporting development teams.

## Tech Stack

### Frontend & UI
- **Framework**: Next.js 16, React 19
- **Language**: TypeScript
- **Styling**: Tailwind CSS 4
- **Components**: shadcn/ui, Radix UI
- **Forms & Validation**: React Hook Form, Zod
- **Data Visualization**: Recharts

### Backend & Data
- **Backend Architecture**: Next.js API Routes, Server Actions
- **Primary Database**: PostgreSQL with Prisma ORM
- **Vector Database (RAG)**: Pinecone
- **Data Fetching**: TanStack Query (React Query)
- **Background Jobs**: Inngest

### AI, Integration & Identity
- **AI/ML**: Google Gemini AI (Gemini 2.5 Flash, text-embedding-004)
- **Integrations**: GitHub API (Octokit)
- **Authentication**: Better Auth
- **Payments & Subscriptions**: Polar

## Key Features

1. **AI-Powered Code Reviews**
   - Automatic PR review generation using Google Gemini AI.
   - Context-aware reviews utilizing RAG with the Pinecone vector database.
   - Comprehensive reviews encompassing a walkthrough, sequence diagrams, summary, strengths, issue detection, improvement suggestions, and even creative poems.

2. **GitHub Integration**
   - Connect and manage multiple repositories seamlessly.
   - Automatic webhook handling for PR events (open/update).
   - Real-time review generation and direct comment posting to GitHub PRs.

3. **RAG Implementation**
   - Automatic codebase indexing with vector embeddings.
   - Semantic search across the entire codebase for enhanced context retrieval.

4. **Dashboard & Analytics**
   - Real-time statistics tracking total repos, commits, PRs, and reviews.
   - GitHub contribution graph visualization.
   - Monthly activity breakdown and beautiful data visualization using Recharts.

5. **Review & Repository Management**
   - Complete review history with status tracking (completed, pending, failed) and direct PR links.
   - Browse, search, filter, and connect/disconnect GitHub repositories with infinite scroll pagination.

6. **Subscription & User Management**
   - **Free tier**: 5 repositories, 5 reviews per repo.
   - **Pro tier**: Unlimited repositories and reviews via Polar integration.
   - Complete profile settings, usage tracking, and secure authentication via Better Auth.

## Architecture & Workflow

Here is a simplified breakdown of how RepoLens works behind the scenes:

1. **Onboarding & Connection**: A user signs in (Better Auth) and connects their GitHub account. The system fetches their repositories using the GitHub API (Octokit).
2. **Indexing the Codebase**: Once a repository is connected, an asynchronous background job (Inngest) reads the code, generates vector embeddings using Gemini (text-embedding-004), and stores them in Pinecone (the Vector database).
3. **Listening for Changes**: RepoLens sets up webhooks on the connected GitHub repositories. Whenever a user opens or updates a Pull Request, GitHub alerts the RepoLens backend.
4. **Context Gathering (RAG)**: The system takes the new PR code and queries Pinecone to find the most relevant, related code clusters from the *entire* repository to understand the broader impact.
5. **AI Review Generation**: The PR changes, plus the retrieved repository context, are sent to Google Gemini 2.5 Flash. Gemini returns a highly detailed, structured review (including Sequence Diagrams and suggestions).
6. **Delivering the Review**: The Inngest background job posts the AI-generated review directly as a comment securely on the GitHub PR and saves a copy to the PostgreSQL database for dashboard history.

## Expected Outcomes

The project is expected to deliver a fully functional AI-powered code review platform capable of assisting developers during the pull request process.

Key outcomes include:
- A web-based platform that integrates with GitHub repositories for automated pull request analysis.
- A context-aware AI review system capable of generating structured feedback on code changes.
- A repository indexing system that enables semantic search and contextual understanding of the codebase.
- A dashboard for viewing review results, repository activity, and analytics.
- Improved development workflow efficiency by reducing the time required for manual code reviews.

## Market Research

Software development teams increasingly rely on automated tools to maintain code quality and improve productivity. Several platforms currently provide AI-assisted coding and review features.

For example:

| Platform | Primary Focus | Limitations Regarding Context-Aware Review |
|:---|:---|:---|
| **GitHub Copilot** | Assists developers in writing code | Provides limited automated review functionality. |
| **Amazon CodeGuru** | Focuses mainly on performance and security analysis | Lacks deep contextual repository understanding. |
| **Snyk** | Provides vulnerability scanning | Does not provide comprehensive architecture-aware review feedback. |

While these tools provide valuable assistance, most existing systems focus on individual code snippets or security scanning rather than holistic repository-level review. This creates a gap for a solution that combines semantic repository understanding, automated pull request review, and AI-generated insights in a unified platform.

## Research Work

- Lewis, P. et al. (2020). *Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks*.
- Vaswani, A. et al. (2017). *Attention Is All You Need*.
- Official Documentation – GitHub
- Pinecone Vector Database Documentation
- Google Gemini AI Documentation
- Prisma ORM Documentation
- Next.js Official Documentation
- TanStack Query Documentation
- Octokit GitHub API Documentation
- Research articles on AI-assisted software development tools.
