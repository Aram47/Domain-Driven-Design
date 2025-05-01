# DDD (Domain Driven Design)

# Library Management System — Clean Architecture Overview

Этот проект реализует систему управления библиотекой на основе принципов **Чистой Архитектуры**, разделяя код на слои: Interfaces, Application, Domain, Infrastructure.

## 📐 Архитектура

```plaintext
[Клиент] ----> [Interfaces] ----> [Application] ----> [Domain] ----> [Infrastructure]
  |                |                   |                  |                |
  | HTTP-запрос    |                   |                  |                |
  | POST /api/books/take              |                  |                |
  | JSON: {bookId, readerId, issueDate}                  |                |
  v                v                   |                  |                |
                   | server.ts        |                  |                |
                   | routes.ts        |                  |                |
                   | libraryController.ts                |                |
                   v                   v                  |                |
                                       | takeBookUseCase.ts                |
                                       | takeBookCommand.ts               |
                                       | takeBookValidator.ts             |
                                       | bookDto.ts                      |
                                       v                  v                |
                                                          | libraryService.ts |
                                                          | book.ts          |
                                                          | loanPolicy.ts    |
                                                          | bookTakenEvent.ts|
                                                          v                v
                                                                           | inMemoryBookRepository.ts
                                                                           | emailNotificationService.ts
                                                                           v
[Клиент] <---- [Interfaces] <---- [Application] <---- [Domain] <---- [Infrastructure]
  |                |                   |                  |                |
  | HTTP-ответ     |                   |                  |                |
  | JSON: {id, title, available}       |                  |                |
  v                v                   v                  v                v
