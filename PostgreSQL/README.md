# Shahnameh PostgreSQL Database Schema

## Table Structures

### 1. `chapter`

- **id**: primary key
- **title**: varchar(255) not null
- **parent_id**: id of the parent chapter if exists. If not, then it's a main chapter and the book itself is its parent!
- **order_in_parent**: order of the chapter in the parent chapter/book

A chapter with verses is considered as a poem.

### 2. `chapter_metadata`

- **id**: primary key
- **chapter_id**: integer references chapter(id)
- **meter**: varchar(255) not null - if a poem, the meter/rhythm of the poem
- **poetic_form**: if it's a poem, the poetic form of it (masnavi, ghazal, etc.)
- **verse_count**: number of the verses (if exist)

### 3. `verse`

- **id**: primary key
- **chapter_id**: integer references chapter(id)
- **order_in_chapter**: integer - order in the poem
- **m1**: text not null - The first hemistich
- **m2**: text not null - The second hemistich
