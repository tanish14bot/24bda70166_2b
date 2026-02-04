# 2b Project

## Starting the Project

Students should first follow the experiment guide to proceed with the project

- [Experiment 2 Guide](https://github.com/cu-fs1#experiment-2)

## Installation

1. **Install Dependencies**

```bash
pnpm install
```

2. **Install Shadcn Components** (if not already installed)

```bash
pnpm dlx shadcn@latest add card button select badge
```

## Project Structure

```
2b/
├── app/
│   ├── globals.css          # Global styles
│   ├── layout.tsx           # Root layout component
│   └── page.tsx             # Main homepage with product filtering
├── components/
│   ├── ui/                  # Shadcn UI components
│   │   ├── badge.tsx
│   │   ├── card.tsx
│   │   └── select.tsx
│   ├── product-card.tsx     # Product display card component
│   └── select-control.tsx   # Reusable select dropdown component
├── lib/
│   └── utils.ts             # Utility functions
├── public/                  # Static assets
├── types/
│   └── index.ts             # TypeScript type definitions
├── components.json          # Shadcn UI configuration
├── eslint.config.mjs        # ESLint configuration
├── next.config.ts           # Next.js configuration
├── package.json             # Project dependencies
├── pnpm-lock.yaml           # Lock file
├── pnpm-workspace.yaml      # pnpm workspace config
├── postcss.config.mjs       # PostCSS configuration
├── tsconfig.json            # TypeScript configuration
└── README.md                # Project documentation
```

## Running the Project

To start the development server:

```bash
pnpm dev
```

The application will be available at [http://localhost:3000](http://localhost:3000)


## Code Explanation

### 1. `types/index.ts`

This file defines TypeScript types used throughout the application:

- **`SelectOption`**: A type definition for select dropdown options
  - `value`: string - The underlying value used for the option
  - `label`: string - The display text shown to users

### 2. `components/select-control.tsx`

A reusable select dropdown component built with Shadcn UI:

- **Purpose**: Provides a customizable select dropdown with label and grouped options
- **Props**:
  - `selectLabel`: Text label displayed before the select
  - `value`: Current selected value (controlled)
  - `onValueChange`: Callback function when selection changes
  - `options`: Array of SelectOption objects
  - `groupLabel`: Label for the option group
  - `placeholder`: Placeholder text when no value selected
- **Features**:
  - Uses Shadcn's Select components for a consistent UI
  - Styled with Tailwind CSS (white background, large text, custom height)
  - Displays label and select in a horizontal flex layout

### 3. `components/product-card.tsx`

A card component for displaying product information:

- **Purpose**: Renders individual product details in a card format
- **Props**:
  - `name`: Product name (string)
  - `price`: Product price (number)
  - `category`: Product category ("electronics" | "clothing" | string)
- **Features**:
  - Uses Shadcn's Card components (Card, CardHeader, CardTitle, CardContent)
  - Displays product name as a large title (3xl)
  - Shows price formatted to 2 decimal places ($XX.XX)
  - Renders category as a colored badge:
    - "electronics" → default variant
    - "clothing" → secondary variant
  - Styled with white background and gray border

### 4. `app/page.tsx`

The main application page with product filtering and sorting:

- **Purpose**: Homepage that displays a filterable and sortable product list
- **State Management**:
  - `filterCategory`: Controls product filtering by category
  - `sortBy`: Controls product sorting order
- **Data**:
  - Contains 4 sample products (2 electronics, 2 clothing items)
  - Each product has: id, name, price, category
- **Features**:
  - **Category Filter**: Select between "All Products", "Electronics", or "Clothing"
  - **Sort Options**: Default, Price Low to High, or Price High to Low
  - **Dynamic Filtering**: Products filter based on selected category
  - **Dynamic Sorting**: Products sort by price (ascending/descending)
  - **Responsive Grid**: 1 column on mobile, 2 columns on medium+ screens
  - **Clean UI**: Gray background with centered content container

### Application Flow

1. User selects a category filter (defaults to "All Products")
2. User selects a sort option (defaults to "Default")
3. Products are filtered by category (if not "all")
4. Filtered products are sorted by price (if not "default")
5. Results display in a responsive grid using ProductCard components

### Technology Stack

- **Framework**: Next.js 14+ (App Router with "use client")
- **UI Library**: Shadcn UI
- **Styling**: Tailwind CSS
- **Language**: TypeScript
- **State Management**: React useState hooks
