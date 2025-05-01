# DDD (Domain Driven Design)

## 📐 Architecture

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
