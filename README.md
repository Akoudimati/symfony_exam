# Symfony Blog - Entity Relationships Example

This is a simple Symfony Blog application that demonstrates CRUD operations and entity relationships (one-to-many and many-to-one).

## Features

- User Management: Create, Read, Update, Delete users
- Post Management: Create, Read, Update, Delete posts
- Entity Relationships: One-to-many relationship between User and Post

## Entity Relationships

- **User**: Has a one-to-many relationship with Post entities
- **Post**: Has a many-to-one relationship with User entity

## Installation

1. Clone the repository
```bash
git clone https://github.com/your-username/symfony-blog.git
cd symfony-blog
```

2. Install dependencies:
```bash
composer install
```

3. Database setup:
   - The project is configured to use SQLite (file-based database)
   - No need for database server installation
   - Visit `/setup-db` route in your browser to initialize the database with test data

4. Start the Symfony development server:
```bash
symfony serve
```

## Project Structure

- `src/Entity/`: Contains the entity classes (User, Post)
- `src/Repository/`: Contains repository classes for data access
- `src/Controller/`: Contains controllers for handling HTTP requests
- `src/Form/`: Contains form types for User and Post
- `templates/`: Contains Twig templates for views

## Entity Classes

### User Entity

```php
// src/Entity/User.php
class User
{
    // ...
    
    #[ORM\OneToMany(mappedBy: 'author', targetEntity: Post::class, orphanRemoval: true)]
    private Collection $posts;
    
    // ...
}
```

### Post Entity

```php
// src/Entity/Post.php
class Post
{
    // ...
    
    #[ORM\ManyToOne(inversedBy: 'posts')]
    #[ORM\JoinColumn(nullable: false)]
    private ?User $author = null;
    
    // ...
}
```

## Usage

1. After installation, start by visiting `/setup-db` to initialize the database with test data
2. Then visit `/` to see the home page
3. Navigate to `/user` to manage users
4. Navigate to `/post` to manage posts

## Exam Preparation

This project was created as a learning resource for a Symfony CRUD exam. The `commands.md` file contains useful Symfony commands for reference.

## Key Concepts

1. **Entity Relationships**: 
   - One-to-Many: A User can have many Posts
   - Many-to-One: Many Posts can belong to one User

2. **Form Types**:
   - User form with name and email fields
   - Post form with title, content and author fields

3. **CRUD Operations**:
   - Create: Adding new entities
   - Read: Viewing entities
   - Update: Editing entities
   - Delete: Removing entities 