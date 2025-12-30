# AnkiConnect (voothi/20251110002755) Release Notes

## v1.48.2

This release focuses on optimizing execution speed for tools that search and retrieve card data.

### ✨ New API Action: `findCardsInfo`

Introduces a new API action, `findCardsInfo`, which combines searching and data retrieval into a single operation.

*   **Performance**: Reduces the required HTTP requests from 2 to 1 for "search + read" operations.
*   **Efficiency**: Significant speedup when interacting with large datasets or high-latency connections.

#### API Details: `findCardsInfo`
Finds card IDs matching a query and returns their detailed information (equivalent to calling `findCards` then `cardsInfo`).

**Request:**
```json
{
    "action": "findCardsInfo",
    "version": 6,
    "params": {
        "query": "deck:current"
    }
}
```

### ⚡ Client Optimization: `anki-search.py`
The companion search script has been updated to:
1.  Use `findCardsInfo` by default for faster execution.
2.  Support a new `--fast` flag to skip detailed info retrieval when only existence/ID check is needed.

---

## v1.46.2

This is a custom build of the popular AnkiConnect add-on, extended with a new API action to support enhanced integration with external tools like the [Kardenwort ecosystem](https://github.com/kardenwort/20250913122858-kardenwort).

This version is based on the contemporary official AnkiConnect build but includes one key addition to enable programmatic management of Anki deck descriptions.

### ✨ New API Action: `setDeckDescription`

This release introduces a single but powerful new API action, `setDeckDescription`, which allows an external application to set or update the description text for any specified Anki deck.

This feature is essential for tools that generate not only cards but also rich contextual metadata for the decks they create.

#### API Details: `setDeckDescription`

Sets the description for a given deck. If the deck does not exist, it will return an error. The description supports standard text and Markdown formatting, just like Anki's native editor.

**Request:**

```json
{
    "action": "setDeckDescription",
    "version": 6,
    "params": {
        "deck": "My Awesome Deck::Chapter 1",
        "description": "This is the full text of Chapter 1, which provides context for all the cards within this subdeck."
    }
}
```

**Full Changelog**: https://github.com/voothi/20251110002755-kardenwort-ankiconnect/compare/v1.44.2...v1.46.2

---

## v1.44.2

This is a custom build of the popular AnkiConnect add-on, extended with a new API action to support enhanced integration with external tools like the [Kardenwort ecosystem](https://github.com/kardenwort/20250913122858-kardenwort).

### ✨ New API Action: `setDeckDescription`

This release introduces a single but powerful new API action, `setDeckDescription`, which allows an external application to set or update the description text for any specified Anki deck.
