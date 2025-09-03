# FileIndexService

**FileIndexService** is a small Kotlin application and library that builds and maintains a reverse index of words contained in text files.  
It supports concurrent queries and can optionally **watch the filesystem** for changes, updating the index in real time.

---

## 🚀 Running the service

The project uses Gradle. You can run it directly from the root of the project:

```bash
./gradlew run --args="/path/to/dir"
```


Examples:
# Index all files under /test
./gradlew run --args="/test"

# Index multiple paths and enable watch mode
./gradlew run --args="--watch /some/dir README.md"


Arguments

— Without arguments, the service defaults to indexing a bundled example directory:

`dummyDir/`

so you can try it out immediately after cloning.

— `--watch`

If the first argument is --watch, the service will both index the provided paths and monitor them for changes.

When you create, edit, or delete files, the inverted index is automatically updated.

While in watch mode, the program drops you into a tiny REPL:

```
Watching /some/dir, README.md.
Type a word to search (Ctrl+D to exit).
> hello
- /some/dir/greetings.txt
> world
- /some/dir/greetings.txt
```

You can type words and see which files currently contain them.

— Without --watch

The service will index the given paths once and print the entire inverted index to the console.


## 📦 Installing as a standalone executable

You can package the service into a standalone folder with:

`./gradlew :app:installDist`

This will create a distribution under:

`build/install/fileindexservice/`

You can copy this entire folder anywhere you like, add the bin/ folder to your PATH, and then run:

`fileindexservice/bin/fileindexservice --watch /some/dir`

or

`fileindexservice/bin/fileindexservice test/`

This makes the tool usable from any directory, not just inside the Gradle project.