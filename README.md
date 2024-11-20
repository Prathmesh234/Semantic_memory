# Semantic Memory: Enabling Memory Sharing Across Agents

This project introduces a semantic memory application where two agents share a common "memory" to enhance task efficiency and performance. The concept is inspired by **MetaReflection**, as discussed in Microsoft's research paper, *"METAREFLECTION: Learning Instructions for Language Agents using Past Reflections."* Semantic memory, as defined in the context of this project, mirrors the human ability to unconsciously perform complex tasks such as typing or walking, leveraging quick-access knowledge stored in a brain-like "RAM" for seamless execution. While trivial for humans, these tasks remain challenging for artificial agents, making semantic memory a significant area of exploration.

## Project Overview

### Agents and Semantic Memory
The implementation involves a **ReACT-based agent** designed to generate outputs using **Chain-of-Thought (CoT) reasoning** for web-search-based tasks. User feedback on the outputs is categorized as either "good" or "bad." For responses marked as unsatisfactory, the system stores the question, output, and associated actions in a **NoSQL database (CosmosDB)**. These records are processed during a subsequent "offline self-reflection" phase.

### Self-Reflection and Generalization
During offline self-reflection, the stored data, including user queries, outputs, and actions, is reviewed by a second **ReACT agent**. This agent analyzes the steps taken by the first agent and generates a generalized reasoning process to address similar issues in the future. These learnings are stored in a **vector database (Azure AI Search)**. 

To enable efficient retrieval, questions are converted into vector representations and stored as vector indices. **Scalar Quantization** is applied to these vectors to enhance retrieval speed and reduce the computational cost of vector searches.

### Memory Sharing Across Agents
When a second agent, Agent B, encounters a new query, the system performs a semantic similarity search against the vector database. The query with the highest similarity score is retrieved, and its corresponding generalized reasoning is passed to Agent B as a prompt. This prompt acts as the agent's "semantic memory," allowing it to utilize insights from prior interactions to improve task performance.

## Key Takeaways
1. **Semantic Memory Sharing:** This project highlights the potential for agents to share semantic memory across trillions of interactions with humans, driving continuous learning and improvement.
2. **Efficiency Through Quantization:** The use of scalar quantization significantly reduces the cost and time of vector search, addressing one of the main challenges of retrieving semantic memory.
3. **Future Implications:** The ability for agents to share and apply generalized learnings across interactions has vast implications for the development of collaborative, memory-enabled AI systems.

**Disclaimer:** This implementation is a personal interpretation of the methods described in the MetaReflection paper. The specific techniques used by the Microsoft Research team may differ. Feedback and suggestions are welcome! 

Feel free to explore the repository and contribute to this ongoing exploration of semantic memory and agent collaboration.

**Metareflection publication** - https://www.microsoft.com/en-us/research/publication/metareflection-learning-instructions-for-language-agents-using-past-reflections/
