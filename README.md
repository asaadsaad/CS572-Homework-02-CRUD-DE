# CS572-Homework-02-CRUD

#### Coding Question
Given the following Schema:
```typescript
import { Schema, model, InferSchemaType } from 'mongoose';

const BookSchema = new Schema({
    title: { type: String, required: true, unique: true },
    author: { type: String, required: true },
    details: {
        genre: { 
            type: String, 
            enum: ['fiction', 'non-fiction', 'science', 'history'], 
            required: true 
        },
        shelf: { type: String, required: true }
    },
    publishedYear: { type: Number, required: true },
    copiesAvailable: { type: Number, required: true },
    rentalPrice: { type: Number, required: true }
}, { timestamps: true });

type BookWithTimestamps = InferSchemaType<typeof BookSchema>;
export type Book = Partial<BookWithTimestamps>;

export const BookModel = model<Book>('book', BookSchema);
```
Complete the following tasks:
1. Write a function to add a new book.
2. Write a function to delete a book by `_id`.
3. Write a function to update book properties by `_id`.
4. Write a function to apply a 15% discount to all fiction books.
5. Write a function to increase the rental price of all science books by $1.
6. Write a function to find all books published between a minimum and maximum year, with pagination.
7. Write a function to find all books in a specific genre, with pagination.
8. Write a function to find all books with fewer than 5 copies available, with pagination.
  
Tip: Store the connection string in an environment variable. Run with:
```
npx tsx watch --env-file=.env ./code.ts
```
