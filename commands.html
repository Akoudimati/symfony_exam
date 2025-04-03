# Essential Symfony Commands

## Entity & Database Commands

### Create Entity
```bash
# Create a new entity
php bin/console make:entity

# Create a new entity with specific fields
php bin/console make:entity EntityName --fields="name:string(255) email:string(255) createdAt:datetime"
```

### Database Management
```bash
# Create database
php bin/console doctrine:database:create

# Create schema update migration
php bin/console doctrine:migrations:diff

# Execute migrations
php bin/console doctrine:migrations:migrate

# Execute specific migration version
php bin/console doctrine:migrations:execute --up 'DoctrineMigrations\Version20230101120000'

# Revert specific migration version
php bin/console doctrine:migrations:execute --down 'DoctrineMigrations\Version20230101120000'

# Create database schema directly (no migrations)
php bin/console doctrine:schema:create

# Update database schema directly (no migrations)
php bin/console doctrine:schema:update --force

# Validate schema
php bin/console doctrine:schema:validate

# Drop database
php bin/console doctrine:database:drop --force

# Load fixtures (sample data)
php bin/console doctrine:fixtures:load
```

## CRUD & Controller Commands

### Generate CRUD
```bash
# Create full CRUD for an entity
php bin/console make:crud EntityName

# This generates:
# - Controller with actions (index, new, show, edit, delete)
# - Forms
# - Templates
```

### Create Controller
```bash
# Create a new controller
php bin/console make:controller ControllerName

# Creates a controller class and template
```

### Create Form
```bash
# Create a form for an entity
php bin/console make:form EntityNameType EntityName
```

## Relationship Commands

### Create Entity Relation
```bash
# Create entities with relationships using the make:entity command
# Example workflow for One-to-Many relationship:

# 1. Create first entity
php bin/console make:entity User

# 2. Create second entity with relation
php bin/console make:entity Post

# During Post creation, add a relation field:
# Field name: author
# Field type: relation
# Related class: User
# Relation type: ManyToOne
```

## Data Fixtures and Validation

### Creating Fixtures
```bash
# Install Doctrine fixtures bundle
composer require --dev doctrine/doctrine-fixtures-bundle

# Generate fixture class
php bin/console make:fixtures UserFixtures

# Load fixtures
php bin/console doctrine:fixtures:load
```

### Validation Commands
```bash
# Add validation constraints (manually in entity)
# Example:
#[Assert\NotBlank(message: 'The name should not be blank')]
#[Assert\Length(min: 2, max: 50)]
private ?string $name = null;

# The class import needed:
use Symfony\Component\Validator\Constraints as Assert;
```

## Other Useful Commands

### Cache Commands
```bash
# Clear cache
php bin/console cache:clear

# Warm up cache
php bin/console cache:warmup
```

### Server Command
```bash
# Start development server
symfony serve
# or
php -S localhost:8000 -t public/

# Stop development server
symfony server:stop
```

### Debug Commands
```bash
# List all routes
php bin/console debug:router

# Show details of specific route
php bin/console debug:router route_name

# List all services
php bin/console debug:container

# Show details of specific service
php bin/console debug:container service_name

# List all event listeners
php bin/console debug:event-dispatcher

# List all Doctrine entities
php bin/console debug:doctrine

# Show entity details
php bin/console doctrine:mapping:info
```

### Security Commands
```bash
# Create user for authentication
php bin/console make:user

# Create login form
php bin/console make:auth

# Create registration form
php bin/console make:registration-form

# Create voter
php bin/console make:voter

# Encode a password (useful for fixtures)
php bin/console security:hash-password
```

### Config and Environment
```bash
# Display current environment
php bin/console about

# Display system requirements
php bin/console check:requirements
```

## Quick Reference for Entity Relationships

### One-to-Many / Many-to-One Relationship
Example: One User can have many Posts

1. In User entity:
```php
#[ORM\OneToMany(mappedBy: 'author', targetEntity: Post::class)]
private Collection $posts;

public function __construct()
{
    $this->posts = new ArrayCollection();
}

// Add and remove methods
public function addPost(Post $post): self
{
    if (!$this->posts->contains($post)) {
        $this->posts->add($post);
        $post->setAuthor($this);
    }
    
    return $this;
}

public function removePost(Post $post): self
{
    if ($this->posts->removeElement($post)) {
        // set the owning side to null (unless already changed)
        if ($post->getAuthor() === $this) {
            $post->setAuthor(null);
        }
    }
    
    return $this;
}
```

2. In Post entity:
```php
#[ORM\ManyToOne(inversedBy: 'posts')]
#[ORM\JoinColumn(nullable: false)]
private ?User $author = null;

// Getter and setter
public function getAuthor(): ?User
{
    return $this->author;
}

public function setAuthor(?User $author): self
{
    $this->author = $author;
    
    return $this;
}
```

### Many-to-Many Relationship
Example: Many Posts can have many Categories

1. In Post entity:
```php
#[ORM\ManyToMany(targetEntity: Category::class, inversedBy: 'posts')]
private Collection $categories;

public function __construct()
{
    $this->categories = new ArrayCollection();
}

// Add and remove methods
public function addCategory(Category $category): self
{
    if (!$this->categories->contains($category)) {
        $this->categories->add($category);
    }
    
    return $this;
}

public function removeCategory(Category $category): self
{
    $this->categories->removeElement($category);
    
    return $this;
}
```

2. In Category entity:
```php
#[ORM\ManyToMany(targetEntity: Post::class, mappedBy: 'categories')]
private Collection $posts;

public function __construct()
{
    $this->posts = new ArrayCollection();
}

// Add and remove methods
public function addPost(Post $post): self
{
    if (!$this->posts->contains($post)) {
        $this->posts->add($post);
        $post->addCategory($this);
    }
    
    return $this;
}

public function removePost(Post $post): self
{
    if ($this->posts->removeElement($post)) {
        $post->removeCategory($this);
    }
    
    return $this;
}
```

### One-to-One Relationship
Example: One User has one Profile

1. In User entity:
```php
#[ORM\OneToOne(mappedBy: 'user', cascade: ['persist', 'remove'])]
private ?Profile $profile = null;

public function getProfile(): ?Profile
{
    return $this->profile;
}

public function setProfile(Profile $profile): self
{
    // set the owning side of the relation if necessary
    if ($profile->getUser() !== $this) {
        $profile->setUser($this);
    }
    
    $this->profile = $profile;
    
    return $this;
}
```

2. In Profile entity:
```php
#[ORM\OneToOne(inversedBy: 'profile')]
#[ORM\JoinColumn(nullable: false)]
private ?User $user = null;

public function getUser(): ?User
{
    return $this->user;
}

public function setUser(User $user): self
{
    $this->user = $user;
    
    return $this;
}
```

## Form Type Examples

### Basic Form Type
```php
// src/Form/PostType.php
namespace App\Form;

use App\Entity\Post;
use App\Entity\Category;
use Symfony\Component\Form\AbstractType;
use Symfony\Component\Form\Extension\Core\Type\TextType;
use Symfony\Component\Form\Extension\Core\Type\TextareaType;
use Symfony\Bridge\Doctrine\Form\Type\EntityType;
use Symfony\Component\Form\FormBuilderInterface;
use Symfony\Component\OptionsResolver\OptionsResolver;
use Symfony\Component\Validator\Constraints\NotBlank;
use Symfony\Component\Validator\Constraints\Length;

class PostType extends AbstractType
{
    public function buildForm(FormBuilderInterface $builder, array $options): void
    {
        $builder
            ->add('title', TextType::class, [
                'constraints' => [
                    new NotBlank(['message' => 'Please enter a title']),
                    new Length(['min' => 3, 'max' => 255]),
                ],
                'attr' => ['class' => 'form-control'],
                'label_attr' => ['class' => 'form-label'],
            ])
            ->add('content', TextareaType::class, [
                'attr' => ['rows' => 10, 'class' => 'form-control'],
                'label_attr' => ['class' => 'form-label'],
            ])
            ->add('categories', EntityType::class, [
                'class' => Category::class,
                'choice_label' => 'name',
                'multiple' => true,
                'expanded' => false, // dropdown (false) or checkboxes (true)
                'attr' => ['class' => 'form-select'],
                'label_attr' => ['class' => 'form-label'],
            ]);
    }

    public function configureOptions(OptionsResolver $resolver): void
    {
        $resolver->setDefaults([
            'data_class' => Post::class,
        ]);
    }
} 