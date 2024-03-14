##### Kentaro Matsuo

## Overview

The Wikipedia Game involves navigating from one Wikipedia article to another using the fewest clicks possible. The current implementation employs a BFS algorithm to find the shortest path between articles. However, due to the vast and densely interconnected nature of Wikipedia, this method often leads to slow performance and inefficient pathfinding, as it does not account for the relevance or semantic relationship between articles.

## Improvement

 propose a Context-Aware Guided Search (CAGS) algorithm that incorporates elements of both depth-first search (DFS) and heuristic-based search strategies. Unlike traditional DFS, which may quickly diverge into less relevant territories, CAGS uses a heuristic function to evaluate the potential relevance of each link within an article to the target article. This relevance is determined through the use of Natural Language Processing (NLP) techniques, specifically leveraging the concept of semantic similarity.
## Pseudocode

    def CAGS(start_article, target_article):
    visited = set()
    stack = [(start_article, heuristic(start_article, target_article))]

    while stack:
        current, _ = min(stack, key=lambda x: x[1])  # Minimize heuristic score
        stack.remove((current, _))

        if current == target_article:
            return True  # Path found

        for neighbor in get_neighbors(current):
            if neighbor not in visited:
                visited.add(neighbor)
                heuristic_score = heuristic(neighbor, target_article)
                stack.append((neighbor, heuristic_score))

    return False  # Path not found

    def heuristic(article_a, article_b):
        # Compute semantic similarity between two articles
        return spaCy_similarity(article_a, article_b)
