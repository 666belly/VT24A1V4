# Animal Manager (EcoZoo)

A comprehensive C# Windows Forms application for managing a diverse collection of animals across multiple categories. The application uses object-oriented design patterns including Factory Pattern, Abstract Base Classes, and Polymorphism to create and manage different animal types with their specific characteristics.

## Overview

Animal Manager is a complete zoo/animal management system that allows users to:
- Add animals from multiple categories (mammals, birds, reptiles, insects, and marine life)
- Manage animal properties including name, age, gender, and domestication status
- Track species-specific attributes (e.g., number of teeth for mammals, wingspan for birds)
- View detailed animal information and food schedules
- Save and load animal records in multiple formats
- Generate unique IDs for each animal

## Features

- **Multi-Category Support**: Manage five different animal categories with species-specific properties
- **Animal Categories**:
  - **Mammals**: Dog (with breed tracking and cuteness factor), Cat
  - **Birds**: Eagle, Dove
  - **Reptiles**: Frog, Lizard
  - **Insects**: Bee, Ant
  - **Marine**: Shark, Goldfish

- **Animal Management**:
  - Add new animals with complete information
  - Update existing animal records
  - Delete animals from the system
  - View detailed animal information
  - Display species-specific details

- **Property Tracking**:
  - Basic Properties: Name, Age, Gender, Domestication Status, Unique ID
  - Mammal-Specific: Number of teeth, tail length, breed (for dogs), cuteness factor (for cats)
  - Bird-Specific: Wingspan, beak length
  - Reptile-Specific: Weight, aquatic habitat preference
  - Insect-Specific: Wing presence
  - Marine-Specific: Fish length, danger level

- **Food Management**:
  - Create and manage food items with ingredients
  - Define food schedules for each animal
  - Track dietary requirements per species

- **File Operations**:
  - Save animal records to text files (.txt)
  - Save animal records to JSON files (.json)
  - Load and display saved records
  - Clear all data for a fresh start

## Project Architecture

### Core Classes

#### Animal Hierarchy
- **`IAnimal.cs`** - Interface defining core animal contract with Name, ID, Gender properties and methods for food schedules and extra information
- **`Animal.cs`** - Abstract base class containing common properties (Name, Gender, Category, Age, Domestication Status, ID)
- **Category Classes**: `Mammal`, `Bird`, `Reptile`, `Insect`, `Marine` - Intermediate abstract classes for grouping related species
- **Species Classes**: `Dog`, `Cat`, `Eagle`, `Dove`, `Frog`, `Lizard`, `Bee`, `Ant`, `Shark`, `Goldfish` - Concrete implementations with species-specific properties

#### Management Classes
- **`AnimalManager.cs`** - Extends `ListManager<Animal>` to manage animal collection with automatic ID generation
- **`ListManager.cs`** - Generic list management utility with CRUD operations, serialization to text/JSON formats
- **`IListManager.cs`** - Interface defining list operations contract

#### Factory Pattern Classes
- **`MammalFactory.cs`** - Creates appropriate mammal instances based on species
- **`BirdFactory.cs`** - Creates bird instances (Eagle, Dove)
- **`ReptileFactory.cs`** - Creates reptile instances (Frog, Lizard)
- **`InsectFactory.cs`** - Creates insect instances (Bee, Ant)
- **`MarineFactory.cs`** - Creates marine animal instances (Shark, Goldfish)

#### Enumeration Types
- **`CategoryType.cs`** - Enum for animal categories (Mammal, Bird, Reptile, Insect, Marine)
- **`GenderType.cs`** - Enum for gender values (Male, Female, Unknown)
- **`MammalSpecies.cs`**, **`BirdSpecies.cs`**, **`ReptileSpecies.cs`**, **`InsectSpecies.cs`**, **`MarineSpecies.cs`** - Species enums

#### Food System
- **`FoodItem.cs`** - Represents individual food items with names and ingredients
- **`FoodSchedule.cs`** - Manages daily food schedule for animals
- **`FoodItemForm.cs`** - UI form for creating and managing food items

#### UI Components
- **`MainForm.cs` / `MainForm.Designer.cs`** - Main application window with:
  - Category and species selection
  - Animal data input fields (category-specific group boxes)
  - Animal list display
  - Animal information viewer
  - Food schedule display
  - Add, Update, Delete operations
  - Menu bar for file operations

- **`DisplayFileContentsForm.cs`** - Secondary form for displaying loaded file contents

### Design Patterns Used

1. **Factory Pattern** - Factory classes create appropriate animal instances based on species selection
2. **Abstract Base Class Pattern** - `Animal` class provides template for all species
3. **Interface Implementation** - `IAnimal` interface enforces contract
4. **Polymorphism** - Override methods for species-specific behavior (GetExtraInfo, GetFoodSchedule)
5. **Generic Collections** - `ListManager<T>` provides type-safe collection management

## Getting Started

### Prerequisites

- .NET Framework or .NET Core
- Visual Studio or Visual Studio Code with C# support
- Newtonsoft.Json NuGet package (for JSON serialization)

### Building and Running

1. Clone the repository
2. Open `VT24Assignment1.sln` in Visual Studio
3. Build the solution (Build > Build Solution)
4. Run the application (F5 or Debug > Start Debugging)

### Usage Guide

1. **Adding an Animal**:
   - Select a category from the "Category" list box
   - Select a species from the "Species" list box
   - Fill in animal details (name, age, gender)
   - Enter species-specific information (varies by type)
   - Check "Domesticated" if applicable
   - Click "Add" button

2. **Viewing Animal Details**:
   - Select an animal from the "All Animals" list
   - View complete information and food schedule in the info panels

3. **Updating an Animal**:
   - Select an animal from the list
   - Modify the information in the input fields
   - Click "Change" button

4. **Deleting an Animal**:
   - Select an animal from the list
   - Click "Delete" button

5. **Managing Food**:
   - Click "Food Items" button
   - Create food items with ingredients
   - Foods are associated with animal food schedules

6. **Saving Records**:
   - File > Save or Save As
   - Choose between .txt or .json format

7. **Loading Records**:
   - File > Open
   - Select a .txt or .json file
   - View contents in display window

## Class Relationships

```
IAnimal (Interface)
   │
   └─ Animal (Abstract Base)
      ├─ Mammal (Abstract)
      │  ├─ Dog
      │  └─ Cat
      ├─ Bird (Abstract)
      │  ├─ Eagle
      │  └─ Dove
      ├─ Reptile (Abstract)
      │  ├─ Frog
      │  └─ Lizard
      ├─ Insect (Abstract)
      │  ├─ Bee
      │  └─ Ant
      └─ Marine (Abstract)
         ├─ Shark
         └─ Goldfish
```

## Technologies Used

- **Language**: C# (.NET)
- **UI Framework**: Windows Forms
- **Data Serialization**: JSON (Newtonsoft.Json), Text files
- **Design Patterns**: Factory, Abstract Base Class, Polymorphism
- **OOP Principles**: Inheritance, Encapsulation, Abstraction

## Future Enhancements

- Database integration for persistent storage
- Web-based interface
- Animal health tracking and veterinary records
- Breeding and genealogy tracking
- Habitat management
- Nutrition analysis
- Staff and employee management
- Export to PDF reports
- Search and filter functionality
- Animal image support

## File Formats

### Text Format (.txt)
Plain text representation of animal records with one record per line containing basic information.

### JSON Format (.json)
Structured JSON format preserving all animal properties and relationships for programmatic access and compatibility.

## License

This project is provided as-is without a specified license.

## Author

Created by @pixabel

---

*Last Updated: August 2024*
