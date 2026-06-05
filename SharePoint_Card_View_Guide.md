# 📚 SharePoint Prompt Library — Card View Setup Guide
### Complete Step-by-Step Guide for First-Time Users
> **Who this is for:** Someone who has never done SharePoint formatting before.
> **What you'll achieve:** Your boring table list → beautiful card view like the website in your screenshot.
> **Time needed:** About 20–30 minutes.

---

## 🗺️ TABLE OF CONTENTS

1. [What Are We Actually Doing? (Read This First)](#1-what-are-we-actually-doing)
2. [Before You Start — Checklist](#2-before-you-start)
3. [PART A — Create a Gallery (Card) View](#part-a--create-a-gallery-card-view)
4. [PART B — Paste the Card Design JSON](#part-b--paste-the-card-design-json)
5. [PART C — Make Your Grid View Look Pretty Too](#part-c--make-your-grid-view-look-pretty-too)
6. [PART D — Fix Your SharePoint Form](#part-d--fix-your-sharepoint-form)
7. [Troubleshooting — When Things Go Wrong](#troubleshooting)
8. [Cheat Sheet — All JSONs in One Place](#cheat-sheet)

---

## 1. What Are We Actually Doing?

**Think of it like this:**

Your SharePoint list is like a **plain Excel table** right now. It shows rows and columns — boring, hard to scan, not user-friendly.

What we want is to make it look like a **website with cards** — like the screenshot you showed, where each prompt appears as a nice box with buttons, colour-coded labels, and a clean layout.

**How does SharePoint do this?**

SharePoint lets you paste a special code called **JSON** into a formatting box. JSON is just a set of instructions that tells SharePoint *"make this look like a card"* or *"make this column green when it says Beginner."*

**You do NOT need to understand the code.** You just need to:
1. Copy the JSON from this guide
2. Paste it in the right place in SharePoint
3. Click Save

That's literally it. ✅

---

## 2. Before You Start

Check these things before you begin:

- [ ] You can **open your SharePoint Prompt Library list** in a browser (Chrome or Edge recommended)
- [ ] You have **Edit or Owner permissions** on the list (if you can add items, you're fine)
- [ ] Your list has these **column names** (check by looking at your column headers):
  - `Title` (or "Prompt Title")
  - `Category`
  - `Prompt ID`
  - `Purpose`
  - `Full Prompt Text`
  - `Variables`
  - `Skill Level`
  - `Engagement Type`
  - `Related IIA Standard`

> ⚠️ **If your column names are slightly different** — don't worry, I'll show you how to fix that in the Troubleshooting section.

---

## PART A — Create a Gallery (Card) View

> A "View" in SharePoint is just a way of displaying the same data differently. You can have multiple views and switch between them. We're creating a new "Gallery" view which is designed to show cards.

### Step A1 — Open Your List

1. Go to your SharePoint site in your browser
2. Click on **"Prompt Library"** in the left navigation (or wherever you access it)
3. You should see your list in table/grid format

### Step A2 — Find the View Options

Look at the **top-right area** of your list. You'll see something like this:

```
[All Items ▾]   [Filter ▾]   [≡ Grid view]
```

Click on **"All Items ▾"** (or whatever your current view is called). A dropdown menu appears.

### Step A3 — Create a New View

In that dropdown, click **"Create new view"**.

A panel or popup will open. You'll see options like:
- Standard view
- **Gallery** ← Click this one
- Calendar view
- etc.

### Step A4 — Set Up the Gallery View

Fill in the form like this:

| Field | What to type/select |
|---|---|
| **View name** | `Card View` |
| **View type** | Gallery (already selected) |
| **Make this the default view** | Leave this unchecked for now |

Click **"Create"** or **"Save"**.

✅ You now have a Gallery view! It will look a bit plain right now — just some boxes. That's fine. We'll design it in Part B.

---

## PART B — Paste the Card Design JSON

> This is where the magic happens. We paste design instructions (JSON) that tells SharePoint exactly how each card should look.

### Step B1 — Make Sure You're in Gallery/Card View

At the top right of your list, the view selector should now say **"Card View"** (the one you just created). If not, click the dropdown and select "Card View".

### Step B2 — Open the Formatting Panel

1. Look at the **top right** of your list for a **settings/gear icon ⚙️** OR click the **View options** button (it looks like sliders or three lines)
2. In the dropdown that appears, look for **"Format current view"**
3. Click it

A panel will slide out on the **right side** of your screen.

### Step B3 — Switch to Advanced Mode

In the formatting panel, you'll see some basic options. Look for a link or button that says **"Advanced mode"** and click it.

You'll now see a text box with some existing JSON code in it (probably just `{}` or some basic code).

### Step B4 — Delete Everything and Paste

1. Click inside the text box in the panel
2. Press **Ctrl + A** (selects everything)
3. Press **Delete** (clears it all)
4. Now copy the JSON below (click from the first `{` to the last `}`)
5. Paste it into the now-empty text box

---

### 📋 CARD VIEW JSON — Copy Everything Below This Line:

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/sp/v2/tile-formatting.schema.json",
  "height": 320,
  "width": 360,
  "hideSelection": false,
  "formatter": {
    "elmType": "div",
    "style": {
      "font-family": "'Segoe UI', sans-serif",
      "box-sizing": "border-box",
      "border-radius": "12px",
      "border": "1px solid #e0e0e0",
      "background-color": "#ffffff",
      "padding": "20px",
      "display": "flex",
      "flex-direction": "column",
      "gap": "10px",
      "box-shadow": "0 2px 8px rgba(0,0,0,0.08)",
      "height": "100%",
      "cursor": "pointer"
    },
    "children": [
      {
        "elmType": "div",
        "style": {
          "display": "flex",
          "justify-content": "space-between",
          "align-items": "center"
        },
        "children": [
          {
            "elmType": "div",
            "style": {
              "background-color": "=if([$Category] == 'Planning Phase', '#003946', if([$Category] == 'Fieldwork Phase', '#005F75', if([$Category] == 'Reporting Phase', '#28A745', if([$Category] == 'Follow-up Phase', '#E63946', '#6c757d'))))",
              "color": "#ffffff",
              "font-size": "11px",
              "font-weight": "600",
              "padding": "3px 10px",
              "border-radius": "20px"
            },
            "txtContent": "[$Category]"
          },
          {
            "elmType": "div",
            "style": {
              "background-color": "#F0F4F5",
              "color": "#005F75",
              "font-size": "11px",
              "font-weight": "700",
              "padding": "3px 10px",
              "border-radius": "20px",
              "font-family": "'Courier New', monospace"
            },
            "txtContent": "[$Prompt_x0020_ID]"
          }
        ]
      },
      {
        "elmType": "div",
        "style": {
          "font-size": "15px",
          "font-weight": "700",
          "color": "#003946",
          "line-height": "1.3"
        },
        "txtContent": "[$Title]"
      },
      {
        "elmType": "div",
        "style": {
          "font-size": "12px",
          "color": "#4a6572",
          "line-height": "1.5",
          "flex-grow": "1"
        },
        "txtContent": "=if(length([$Purpose]) > 120, substring([$Purpose], 0, 120) + '...', [$Purpose])"
      },
      {
        "elmType": "div",
        "style": {
          "display": "flex",
          "flex-wrap": "wrap",
          "gap": "6px"
        },
        "children": [
          {
            "elmType": "div",
            "style": {
              "background-color": "=if([$Skill_x0020_Level] == 'Beginner', '#e8f5e9', if([$Skill_x0020_Level] == 'Intermediate', '#e3f2fd', '#fff8e1'))",
              "color": "=if([$Skill_x0020_Level] == 'Beginner', '#28A745', if([$Skill_x0020_Level] == 'Intermediate', '#005F75', '#B8860B'))",
              "font-size": "11px",
              "font-weight": "600",
              "padding": "3px 10px",
              "border-radius": "16px"
            },
            "txtContent": "=if([$Skill_x0020_Level] == 'Beginner', '🌱 Beginner', if([$Skill_x0020_Level] == 'Intermediate', '⚡ Intermediate', '🔥 Advanced'))"
          },
          {
            "elmType": "div",
            "style": {
              "background-color": "#F0F4F5",
              "color": "#003946",
              "font-size": "11px",
              "font-weight": "600",
              "padding": "3px 10px",
              "border-radius": "16px"
            },
            "txtContent": "=if([$Engagement_x0020_Type] == 'Assurance', '🛡️ Assurance', if([$Engagement_x0020_Type] == 'Advisory', '💡 Advisory', '🔀 Both'))"
          }
        ]
      },
      {
        "elmType": "div",
        "style": {
          "background-color": "#F0F4F5",
          "border-radius": "6px",
          "padding": "8px 10px",
          "font-size": "11px",
          "color": "#005F75",
          "font-family": "'Courier New', monospace",
          "overflow": "hidden",
          "white-space": "nowrap",
          "text-overflow": "ellipsis",
          "border-left": "3px solid #FEBE10"
        },
        "txtContent": "=if(length([$Variables]) > 55, substring([$Variables], 0, 55) + '...', [$Variables])"
      },
      {
        "elmType": "div",
        "style": {
          "display": "flex",
          "gap": "8px",
          "border-top": "1px solid #f0f0f0",
          "padding-top": "12px"
        },
        "children": [
          {
            "elmType": "div",
            "style": {
              "flex": "1",
              "background-color": "#FEBE10",
              "color": "#003946",
              "font-size": "12px",
              "font-weight": "700",
              "padding": "8px 0",
              "border-radius": "8px",
              "text-align": "center",
              "cursor": "pointer"
            },
            "txtContent": "👁 Quick View",
            "defaultHoverField": "[$Title]"
          },
          {
            "elmType": "div",
            "style": {
              "flex": "1",
              "background-color": "#003946",
              "color": "#ffffff",
              "font-size": "12px",
              "font-weight": "700",
              "padding": "8px 0",
              "border-radius": "8px",
              "text-align": "center",
              "cursor": "pointer"
            },
            "txtContent": "📋 Copy Prompt",
            "customCardProps": {
              "openOnEvent": "click",
              "directionalHint": "bottomCenter",
              "isBeakVisible": false,
              "formatter": {
                "elmType": "div",
                "style": {
                  "padding": "16px",
                  "max-width": "420px",
                  "font-family": "'Segoe UI', sans-serif",
                  "background": "#ffffff"
                },
                "children": [
                  {
                    "elmType": "div",
                    "style": {
                      "font-size": "14px",
                      "font-weight": "700",
                      "color": "#003946",
                      "margin-bottom": "10px",
                      "border-bottom": "2px solid #FEBE10",
                      "padding-bottom": "8px"
                    },
                    "txtContent": "[$Title]"
                  },
                  {
                    "elmType": "div",
                    "style": {
                      "font-size": "12px",
                      "font-weight": "600",
                      "color": "#005F75",
                      "margin-bottom": "6px"
                    },
                    "txtContent": "Full Prompt Text:"
                  },
                  {
                    "elmType": "div",
                    "style": {
                      "font-size": "12px",
                      "color": "#333",
                      "line-height": "1.6",
                      "background": "#F0F4F5",
                      "padding": "10px",
                      "border-radius": "6px",
                      "max-height": "200px",
                      "overflow": "auto",
                      "white-space": "pre-wrap"
                    },
                    "txtContent": "[$Full_x0020_Prompt_x0020_Text]"
                  },
                  {
                    "elmType": "div",
                    "style": {
                      "font-size": "11px",
                      "color": "#888",
                      "margin-top": "10px",
                      "font-style": "italic"
                    },
                    "txtContent": "Tip: Click the item title above to open and copy the full prompt."
                  }
                ]
              }
            }
          }
        ]
      },
      {
        "elmType": "div",
        "style": {
          "font-size": "10px",
          "color": "#aaa",
          "text-align": "right"
        },
        "txtContent": "=[$Related_x0020_IIA_x0020_Standard]"
      }
    ]
  }
}
```

### Step B5 — Preview and Save

1. After pasting, click the **"Preview"** button (if available) to see how it looks
2. If it looks good, click **"Save"**
3. If you see an error — go to the [Troubleshooting section](#troubleshooting)

✅ Your cards should now appear! Each one will show the category badge, prompt ID, title, purpose snippet, skill level, and buttons.

---

## PART C — Make Your Grid View Look Pretty Too

> Even when users switch to the regular table/grid view, you can make individual columns look beautiful with colour-coded badges. This is called **Column Formatting** and it's even simpler than Part B.

We'll format 4 columns: **Category**, **Prompt ID**, **Skill Level**, and **Engagement Type**.

### How to Format Any Column (Same Steps for All 4):

1. Go to your list in **"All Items"** view (the normal table view)
2. Click on the **column header name** you want to format (e.g., click "Category")
3. A small dropdown appears — click **"Column settings"**
4. Click **"Format this column"**
5. A panel opens on the right — click **"Advanced mode"**
6. **Select all (Ctrl+A)** and **delete** the existing code
7. **Paste** the JSON for that specific column (see below)
8. Click **"Save"**

Repeat these 8 steps for each of the 4 columns below. 👇

---

### Column 1 of 4 — CATEGORY Column JSON

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/sp/v2/column-formatting.schema.json",
  "elmType": "div",
  "style": {
    "display": "inline-block",
    "background-color": "=if(@currentField == 'Planning Phase', '#003946', if(@currentField == 'Fieldwork Phase', '#005F75', if(@currentField == 'Reporting Phase', '#28A745', if(@currentField == 'Follow-up Phase', '#E63946', '#6c757d'))))",
    "color": "#ffffff",
    "font-size": "11px",
    "font-weight": "600",
    "padding": "4px 12px",
    "border-radius": "20px",
    "font-family": "'Segoe UI', sans-serif"
  },
  "txtContent": "@currentField"
}
```

**Result:** Each category gets its own colour badge:
- Planning Phase → Dark Teal
- Fieldwork Phase → Medium Teal
- Reporting Phase → Green
- Follow-up Phase → Red

---

### Column 2 of 4 — PROMPT ID Column JSON

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/sp/v2/column-formatting.schema.json",
  "elmType": "div",
  "style": {
    "display": "inline-block",
    "background-color": "#003946",
    "color": "#FEBE10",
    "font-family": "'Courier New', monospace",
    "font-size": "11px",
    "font-weight": "700",
    "padding": "4px 12px",
    "border-radius": "20px",
    "letter-spacing": "0.04em"
  },
  "txtContent": "@currentField"
}
```

**Result:** Prompt IDs look like dark teal pills with gold text (PLAN-001, FIELD-003, etc.)

---

### Column 3 of 4 — SKILL LEVEL Column JSON

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/sp/v2/column-formatting.schema.json",
  "elmType": "div",
  "style": {
    "display": "inline-block",
    "background-color": "=if(@currentField == 'Beginner', '#e8f5e9', if(@currentField == 'Intermediate', '#e3f2fd', '#fff8e1'))",
    "color": "=if(@currentField == 'Beginner', '#28A745', if(@currentField == 'Intermediate', '#005F75', '#B8860B'))",
    "font-size": "12px",
    "font-weight": "700",
    "padding": "4px 12px",
    "border-radius": "20px",
    "font-family": "'Segoe UI', sans-serif"
  },
  "txtContent": "=if(@currentField == 'Beginner', '🌱 Beginner', if(@currentField == 'Intermediate', '⚡ Intermediate', '🔥 Advanced'))"
}
```

**Result:** Skill levels get colour-coded with emoji:
- 🌱 Beginner → light green
- ⚡ Intermediate → light blue
- 🔥 Advanced → light yellow

---

### Column 4 of 4 — ENGAGEMENT TYPE Column JSON

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/sp/v2/column-formatting.schema.json",
  "elmType": "div",
  "style": {
    "display": "inline-block",
    "background-color": "=if(@currentField == 'Assurance', '#e3f2fd', if(@currentField == 'Advisory', '#e8f5e9', '#fff8e1'))",
    "color": "=if(@currentField == 'Assurance', '#005F75', if(@currentField == 'Advisory', '#28A745', '#B8860B'))",
    "font-size": "12px",
    "font-weight": "700",
    "padding": "4px 12px",
    "border-radius": "20px",
    "font-family": "'Segoe UI', sans-serif"
  },
  "txtContent": "=if(@currentField == 'Assurance', '🛡️ Assurance', if(@currentField == 'Advisory', '💡 Advisory', '🔀 Both'))"
}
```

**Result:** Engagement type gets colour-coded with emoji:
- 🛡️ Assurance → blue
- 💡 Advisory → green
- 🔀 Both → yellow

---

## PART D — Fix Your SharePoint Form

> When someone clicks a card to **add or edit** a prompt, the form that opens can also be made cleaner. From your Screenshot 1, you already have a nice form setup — here's how to make sure it shows the right fields in the right order.

### Step D1 — Open the Form Editor

1. In your list, click **"+ New"** to open the new item form
2. In the form that opens, click the **pencil/edit icon** at the top (usually top right of the form)
3. Or go to: **Settings ⚙️ → List settings → Form settings → Customize form using Power Apps** (for advanced editing)

### Step D2 — Use "Edit Columns" for Quick Field Ordering

The simpler way (no Power Apps needed):
1. When the form is open, look for **"Edit form"** button at the top
2. Click **"Edit columns"** from that menu
3. You'll see a list of all your columns with toggles
4. Drag them into the order below and turn off ones you don't need on the form:

**Recommended field order for your form:**
1. ✅ Prompt Title
2. ✅ Category
3. ✅ Prompt ID
4. ✅ Full Prompt Text
5. ✅ Variables
6. ✅ Purpose
7. ✅ Methodology Notes
8. ✅ Skill Level
9. ✅ Engagement Type
10. ✅ Tips for Customization
11. ✅ Example Input
12. ✅ Example Output
13. ✅ Related IIA Standard
14. ❌ Published on (can hide from form, it auto-fills)

4. Click **"Save"** when done

---

## Troubleshooting

### ❌ Problem: "I get a red error when I paste the JSON"

**Most common cause:** Your column names don't match what the JSON expects.

**How to fix it:**

The JSON uses internal SharePoint column names. When a column name has a space (like "Prompt ID"), SharePoint converts it to `Prompt_x0020_ID` internally.

Here's the conversion rule:
- Space → `_x0020_`
- So "Full Prompt Text" → `Full_x0020_Prompt_x0020_Text`
- "Skill Level" → `Skill_x0020_Level`
- "Engagement Type" → `Engagement_x0020_Type`

**How to find the actual internal name of your column:**
1. Go to **List Settings** (Settings ⚙️ → List settings)
2. Scroll down to **"Columns"** section
3. Click on the column you're checking
4. Look at the URL in your browser — at the end you'll see `Field=XXXXXXXX`
5. That `XXXXXXXX` part is the internal name

Then in the JSON, replace `[$Skill_x0020_Level]` with `[$YourActualInternalName]`.

---

### ❌ Problem: "Cards show up but some fields are blank"

**Cause:** The column name in the JSON doesn't match your actual column name.

**Fix:** Follow the internal name check above (Troubleshooting item 1) and update the JSON references.

The most commonly affected fields are:
- `[$Prompt_x0020_ID]` — make sure you have a column called "Prompt ID"
- `[$Full_x0020_Prompt_x0020_Text]` — make sure your column is "Full Prompt Text"
- `[$Related_x0020_IIA_x0020_Standard]` — make sure it's "Related IIA Standard"

---

### ❌ Problem: "I can't find 'Format current view' anywhere"

**This happens when:** You're in the default All Items view which sometimes restricts formatting.

**Fix:**
1. Make sure you're in your **Gallery/Card View** (not All Items)
2. Try clicking the **three dots (...)** at the top of the list
3. Or try: **View options (the filter icon)** → **Format current view**

---

### ❌ Problem: "The 'Copy Prompt' button doesn't actually copy to clipboard"

**Why:** SharePoint's built-in JSON formatting doesn't have direct clipboard access for security reasons.

**What it does instead:** Clicking "Copy Prompt" opens a popup showing the full prompt text. Users can then manually select and copy it.

**Workaround:** Tell your users to **click the card title** to open the full item, then copy from there — or add a note in your team channel explaining this.

---

### ❌ Problem: "My category values are different (e.g., 'AML Planning' instead of 'Planning Phase')"

**Fix:** In the JSON, find all the `== 'Planning Phase'` parts and replace the text inside the quotes with your exact category names.

For example, if your categories are `AML Planning`, `AML Fieldwork`, etc., change:
```
== 'Planning Phase'
```
to:
```
== 'AML Planning'
```

Do this for every place the category name appears in the JSON.

---

## Cheat Sheet

> Quick reference — bookmark this section!

### How to Get to Column Formatting:
```
Click column header → Column settings → Format this column → Advanced mode
```

### How to Get to View Formatting:
```
Be in the Gallery view → View options / ⚙️ → Format current view → Advanced mode
```

### Column Internal Name Rule:
```
"Skill Level"  →  Skill_x0020_Level
"Prompt ID"    →  Prompt_x0020_ID
"Full Prompt Text"  →  Full_x0020_Prompt_x0020_Text
```

### Colour Reference (Your Brand Colours):
| Colour | Code | Used For |
|---|---|---|
| Dark Teal | `#003946` | Planning Phase, card titles |
| Medium Teal | `#005F75` | Fieldwork Phase, Prompt ID text |
| Gold/Yellow | `#FEBE10` | Quick View button, accents |
| Green | `#28A745` | Reporting Phase, Beginner |
| Red | `#E63946` | Follow-up Phase, alerts |
| Light Grey BG | `#F0F4F5` | Card backgrounds, variable box |

### JSON Validator (use when you get errors):
Go to **https://jsonlint.com** → paste your JSON → click "Validate JSON" → it will highlight any errors in red.

---

## ✅ Final Checklist — Did You Do Everything?

- [ ] Created a new **Gallery** view named "Card View"
- [ ] Pasted the Card View JSON in **Part B**
- [ ] Formatted the **Category** column (Part C — Column 1)
- [ ] Formatted the **Prompt ID** column (Part C — Column 2)
- [ ] Formatted the **Skill Level** column (Part C — Column 3)
- [ ] Formatted the **Engagement Type** column (Part C — Column 4)
- [ ] Checked the form fields order (Part D)

---

*Guide created for Internal Audit Prompt Library • SharePoint Online*
*All JSON is designed to work without any coding knowledge — just copy, paste, and save.*
