# ساختار دیتابیس شاهنامه

## ساختار جداول

### 1. `chapter`

- **id**: ای دی
- **title**: عنوان
- **parent_id**: ای دی والد در صورت وجود. اگر هیچ والدی نباشد یعنی یک بخش اصلی است و والد آن خود کتاب است
- **order_in_parent**: ترتیب در والد

یک بخش که حاوی ابیات باشد به عنوان شعر تلقی می شود

### 2. `chapter_metadata`

- **id**: ای دی
- **chapter_id**: ای دی بخش
- **meter**: وزن شعر
- **poetic_form**: قالب شعری (مثنوی یا غزل و یا ...)
- **verse_count**: تعداد ابیات

### 3. `verse`

- **id**: ای دی
- **chapter_id**: ای دی بخش/شعر
- **order_in_chapter**: ترتیب در شعر
- **m1**: مصرع اول
- **m2**: مصرع دوم

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
