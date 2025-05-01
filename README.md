# DDD (Domain Driven Design)

# Library Management System

This is a layered architecture diagram for a library management system, showing the flow of a book checkout process.

## Architecture Overview

```mermaid
graph TD
    A[Клиент] -->|HTTP-запрос POST /api/books/take| B[Interfaces]
    B --> C[Application]
    C --> D[Domain]
    D --> E[Infrastructure]
    
    A -->|JSON: {bookId, readerId, issueDate}| B
    B -->|server.ts| B
    B -->|routes.ts| B
    B -->|libraryController.ts| C
    C -->|takeBookUseCase.ts| C
    C -->|takeBookCommand.ts| C
    C -->|takeBookValidator.ts| C
    C -->|bookDto.ts| D
    D -->|libraryService.ts| D
    D -->|book.ts| D
    D -->|loanPolicy.ts| D
    D -->|bookTakenEvent.ts| E
    E -->|inMemoryBookRepository.ts| E
    E -->|emailNotificationService.ts| E
    
    E --> D
    D --> C
    C --> B
    B --> A
    
    A -->|HTTP-ответ| B
    B -->|JSON: {id, title, available}| A