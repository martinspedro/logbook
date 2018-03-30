# Logbook

A command line tool to create and manage a digital logbook using **vim**, **git**, **markdown** and **pandoc**.


## Motivation

After writing a _(very incomplete, full of typos and still on alpha version)_ Operating Systems book from class notes 
I took on vim, I decided to automate and simplify both the note-taking and the note-curating process.

The _alpha version_ of the book on Operating Systems can be download [here.](https://k3rn3l-pan1c.github.io/SO-notes/pdf/Theoretical_SO_Book.pdf)

The repository is available [here.](https://github.com/k3rn3l-pan1c/SO-notes)


## Objective
The primary purpose of this tool is to ease the taking, managing and note curating process from classes. 

To be effective, this tool must:

- Allow to take notes fast, from anywhere in the terminal and operative system
- Use a simple syntax to organize my notes
- Keep track of all the notes taken in a clean and organized way
- Enable the generation of eye-candy pdfs for printing and studying

## Features

### Courses notes
**Create**, **organize**, **manage** and **keep track** of all the notes. 


It is possible to:

- Initialize a course: `logbook --init-course <course-name>`
- Add a new raw note to an existent course: `logbook -c|--course -<note type> <course-name>`
  - The note type indicates the type of raw note:
    - `-t`: Theoretical class
    - `-p`: Pratical class
    - `-o`: Ordinary note
- Publish raw, curated notes or book chapters `logbook p|--publish <note name>`
- List all existent courses `logbook -lc|--list-courses`

Some additional features consist on:

- Raw notes being named using the type of note and the date
- Every raw note added/saved is automatically committed to the course repo
- Statistics related to number of lines, words and characters of the note are presented upon saving
- Supporting todo list in the note. 
  - Just write `__TODO__` in any place on the task sentence.
  - Upon saving, the line and the task are printed in a list for easy copy-past

### Documents
The document module allows the continuous editing of one file documents. Documents such as wish lists, reports, minutes, records or even formal emails.

 
It is possible to:

- Create/Open a document: `logbook --doc "<doc name>"`
- Creat a symbolic link in the current directory to the document: `logbook -s|--symbolic-link  "<doc name>"`
- List the name and the first 3 lines of all existing documents: `logbook -ld|--list-documents`

Note: the option `--new-doc`is deprecated. Use `--doc` instead

### Journaling
Later on, I merged my journaling cli-tool with the logbook tool. 

The journaling features allow to:

- Keep a digital journal
- Save quotes
  - Using markdown quote syntax, `>`
- Tag sentences/documents and search later
  - A tag is used as `__TAG__`

The journal is organized using directories and plain-text files, for preventing problems of compability as the years roll by. 

The directory structure is as follows:

```bash
├── 2017                      # A directory for each year
│   └── ...
└── 2018
    ├── February              # A subdirectory for each month
    │   ├── 01-Feb-2018.md    # A file for each day
    │   ├── ...
    │   └── 28-Feb-2018.md
    ├── January
    │   ├── 01-Jan-2018.md
    │   ├── 02-Jan-2018.md
    │   └── ...
    └── March
        ├── 02-Mar-2018.md
        ├── ...
        └── 30-Mar-2018.md
```

Each file is organized as follows:

```
# Friday, 30  March of 2018   # First line of the file indicates the day of the week and the date

## 15:09:25                   # Date when each entry started
This is a entry

## 16:29:04
This is another
```

## Help menu
```bash
USAGE: logbook <options> <args>\n
options
   -j|--journal:         Creates a new journal entry.        
   -t|--tag <tag_name>:  Fetch all journal entries by <tag_name>
   -q|--quote:           Fetch all quotes in journal entries

   --init-course:        Initializates a new course in the current directory.
   -c|--course:          Adds a new raw note to a previously created course unit.
   -p|--publish:         Publish raw/curated note, or any given markdown file
   -lc|--list-courses:   Lists all courses
   
   --new-doc:            Initializes a new document # Deprecated. Use --doc instead
   --doc:                Creates and/or edits an document
   -s|--symbolic-link:   Creates a symbolic link in the current directory to a document
   -ld|--list-documents: Lists all created documents

   -h|--help:            Shows this menu.\n"
```

## Licensing
The code is licensed under MIT License.

