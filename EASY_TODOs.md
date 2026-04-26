# Easy TODOs

Top 10 impactful but concise TODOs ranked by priority.

---

## ✅ DONE - window.rs:479 - Handle extra mouse button types

**File:** `packages/blitz-shell/src/window.rs:479`

```rust
// TODO: handle other button types
```

**Fixed:** Mapped `MouseButton::Back` to `Fourth` and `MouseButton::Forward` to `Fifth`. Unknown buttons fall back to `Auxiliary`.

---

## 2. layout/list.rs:137 - Support CSS `symbols()` in counter styles

**File:** `packages/blitz-dom/src/layout/list.rs:137`

```rust
// TODO: support custom symbol lists. For now fallback to •
```

**Why easy:** `CounterStyle::Symbols { .. }` enum variant already exists, just need to handle the `symbols` field. 5-10 lines.

---

## 3. html_sink.rs:253 - Implement HTML templates

**File:** `packages/blitz-html/src/html_sink.rs:253`

```rust
// TODO: implement templates properly. This should allow to function like regular elements.
```

**Why easy:** Currently just returns `*target` (no-op). Templates are a WPT test feature. Implementation is self-contained with clear scope.

---

## ✅ DONE - stylo.rs:389 - Case-sensitive attribute selectors

**File:** `packages/blitz-dom/src/stylo.rs:389`

```rust
// TODO: case sensitivity
```

**Fixed:** Implemented case-insensitive matching using `Cow<str>` to avoid allocations in the common case. Supports `[attr="value" i]` CSS selector syntax.

---

## ✅ DONE - render.rs:292 - Allow layers with opacity to be unclipped

**File:** `packages/blitz-paint/src/render.rs:292`

```rust
// TODO: allow layers with opacity to be unclipped (overflow: visible)
```

**Fixed:** Added `&& has_opacity` to `should_clip` check. Elements with `opacity < 1.0` now skip the clip layer when `overflow: visible` is set, fixing rendering of partially visible child elements.

---

## 5. text.rs:79 - Descender-aware underline positioning

**File:** `packages/blitz-paint/src/text.rs:79`

```rust
// TODO: intercept line when crossing an descending character like "gqy"
```

**Why easy:** Text metrics already contain descent info. Need to clip/draw segments where descenders cross the underline path. Moderate complexity but visually impactful.

---

## 6. render.rs:218 - Handle overflow-x vs overflow-y separately

**File:** `packages/blitz-paint/src/render.rs:218`

```rust
// TODO: account for overflow_x vs overflow_y
```

**Why easy:** Variables already exist (`overflow_x`, `overflow_y`), just need to use them for clipping instead of a single `is_clipped` flag. 3-5 lines.

---

## 7. inline.rs:180 - RTL-aware scrollbar positioning

**File:** `packages/blitz-dom/src/layout/inline.rs:180`

```rust
// TODO: make side configurable based on the `direction` property
```

**Why easy:** `direction` property exists on style. Need to flip scrollbar from `right` to `left` for RTL. 3-4 lines.

---

## 8. table.rs:266 - Account for padding/border/margin in table column sizing

**File:** `packages/blitz-dom/src/layout/table.rs:266`

```rust
// TODO: account for padding/border/margin
```

**Why easy:** `style` already has padding/border/margin. Need to subtract them from the available width. 5-8 lines.

---

## ✅ DONE - ref_test.rs:133 - Make pixels-per-meter configurable

**File:** `wpt/runner/src/test_runners/ref_test.rs:133`

```rust
// Set pixels-per-meter. TODO: make configurable.
```

**Fixed:** Added optional `ppm` parameter to `write_png` function. Defaults to the original value when `None`.

---

## 10. inline.rs:333 - Cache content width measurements

**File:** `packages/blitz-dom/src/layout/inline.rs:333`

```rust
// TODO: Cache content widths.
```

**Why easy:** `InlineBox::width` gets recalculated on every layout. Add a cache field. Moderate effort, good performance win.