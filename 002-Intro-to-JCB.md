# Building a “Hello World” Component with Joomla Component Builder v5

*(Complete Beginner Walkthrough)*

### [Tutorial Video](https://www.youtube.com/watch?v=1KBBtQUxMTc)

---

## Introduction

[01:55](https://youtu.be/1KBBtQUxMTc?t=115)

This tutorial teaches you how to build a fully working Joomla component from scratch using **Joomla Component Builder (JCB)**.
You’ll start with the simplest setup – a **“Hello World”** greeting – and end with a dynamic site view where you can list, view, and even edit those greetings from the frontend.

**What you’ll do:**

1. Install JCB
2. Create a new field (`greeting`)
3. Build an admin view (`greetings`)
4. Create and compile a new component (`world`)
5. Add frontend (site) views
6. Link menu items and add edit links

Download the latest JCB release from [VDM GitHub Releases](https://github.com/vdm-io/Joomla-Component-Builder/releases), then install it via **Extensions → Manage → Install**.

---

## 1. Create the Greeting Field

[02:46](https://youtu.be/1KBBtQUxMTc?t=166)

Fields define the data columns your component will use. Here you’ll create a simple text field that stores greetings.

### Steps

1. Go to **JCB → Fields → New**.
2. Under **Set Properties** tab:

   * **Name** → `greeting`
   * **Label** → `Greeting`
   * **Type** → Select **Text**
3. Switch to the **Database** tab:

   * **Data Type** → Select `VARCHAR`
   * **Length** → `255` (typical for short text)
   * **Null Switch** → choose `NOT NULL` (so it can’t be empty)
   * **Modelling Method** → `Default`

     > *This defines how JCB models the field data in generated code.*
4. You may leave **Category** and **Publishing** defaults unchanged.
5. Click **Save & Close**.

> 💡 *Explanation:*
> The **Database tab** tells JCB what SQL column to generate.
>
> * `VARCHAR(255)` stores short text.
> * `NOT NULL` makes it required.
> * `Modelling Method` lets you choose JSON/base64/encryption options, but “Default” is fine here.

---

## 2. Create an Admin View

[03:51](https://youtu.be/1KBBtQUxMTc?t=263)

The **Admin View** connects fields to a database table and creates Joomla’s backend management screens.

### Steps

1. Go to **Admin Views → New**.
2. Configure basic info:

   * **Name (Singular)** → `greeting`
   * **Name (Plural)** → `greetings`
   * **System Name** → `greetings`
3. Select a suitable icon if you want.
4. In the **Fields** tab, click **Add Field** and choose `greeting`.

   * Mark it as:

     * **Show in list**
     * **First column**
     * **Title field**
     * **Sortable**
     * **Searchable**
     * **Linked to edit view**
5. Save & Close.

This admin view will manage records of greetings in the backend.

---

## 3. Create the Component “World”

[04:55](https://youtu.be/1KBBtQUxMTc?t=295)

Now you tie everything together into a real Joomla component.

### Steps

1. Open **Components → New**.
2. **Name** → `World`

   * System name auto-fills as `world`.
3. Optional: choose an icon/image.
4. Under **Admin View Settings**:

   * Link the main admin view to `Greetings`.
5. Enable options (per video):

   * Add to Main Menu
   * Allow Sub-menu
   * Auto-checking
   * History
   * Has Metadata
   * Has Access
   * Allow Import / Export
6. Under **Site View Options**, enable:

   * **Create Site View** → Yes
   * **Linked Admin View** → `Greetings`
   * **Has Edit View** → Yes
   * **Default View** → `Greetings`
7. **Save & Close.**

---

## 4. Compile and Install the Component

[07:25](https://youtu.be/1KBBtQUxMTc?t=445)

1. Go to **Compiler** in JCB.
2. Select your new component (**World**).
3. Deselect any optional build items not needed (as in video).
4. Click **Compile**.

JCB writes the PHP, XML, and SQL files (≈ 8 000 lines, 160 files).
When done, click **Install** to add it directly to Joomla.

### Verify the Admin Area

* Go to **Components → Hello World → Greetings**.
* Click **New**, enter “Hi there James Sable”, then **Save & Close**.
* Re-open, change it to “Hi there Michael”, save, and check **Versions**.
  You’ll see automatic version control and permission handling.
  [09:55](https://youtu.be/1KBBtQUxMTc?t=595)

---

## 5. Add Frontend (Site) Views

[12:15](https://youtu.be/1KBBtQUxMTc?t=737)

JCB lets you quickly build frontend pages (site views) to display data.

---

### 5.1 Create Dynamic Gets

Dynamic Gets define what data each site view retrieves.

[13:34](https://youtu.be/1KBBtQUxMTc?t=814)

**A. List of Items**

1. **Dynamic Gets → New**.
2. Set **Type** → List Query.
3. **Admin View** → `Greetings`.
4. **Pagination** → No.
5. Add a **WHERE filter**:

   ```sql
   published = 1
   ```
6. **Save & Close.**

**B. Single Item**

1. **Dynamic Gets → New**.
2. **Type** → Get Item.
3. **Admin View** → `Greetings`.
4. **WHERE filter**:

   ```sql
   id = {id}
   ```
5. **Save & Close.**

---

### 5.2 Create Site Views

[17:05](https://youtu.be/1KBBtQUxMTc?t=1025)

**List View (`greetings`)**

1. Add a new Site View.
2. Link it to the **list** Dynamic Get.
3. In the PHP output area, insert:

   ```php
   <ul>
   <?php foreach ($this->items as $item): ?>
       <li><?php echo $item->greeting; ?></li>
   <?php endforeach; ?>
   </ul>
   ```
4. **Save & Close.**

**Single View (`greet`)**

1. Add another Site View.
2. Link it to the **single** Dynamic Get.
3. Output:

   ```php
   <h2><?php echo $this->item->greeting; ?></h2>
   ```
4. Name it `greet` (avoid conflict with edit view `greeting`).
5. **Save & Close.**

---

### 5.3 Attach Site Views to Component

[20:30](https://youtu.be/1KBBtQUxMTc?t=1230)

1. In **Component → Settings → Site Views**:

   * `greet` → no menu; metadata on.
   * `greetings` → menu on; metadata on; set default.
   * Access → Public for both.
2. **Save & Close**, then **Compile** and **Install** again.

---

## 6. Verify Frontend and Public Access

[24:00](https://youtu.be/1KBBtQUxMTc?t=1440)

If your new views don’t appear publicly:

1. Uninstall the component.
2. Re-install it fresh – JCB applies public access on first install.

To keep existing data:

* In **Admin View → MySQL Tab**, enable table backup.
* Exclude volatile fields (`created_by`, `modified_by`, `access`, `asset_id`).
* Compile before uninstalling.

---

## 7. Link a Menu Item

[27:40](https://youtu.be/1KBBtQUxMTc?t=1660)

1. In Joomla → **Menus → Main Menu → New**.
2. **Menu Item Type** → Component → Hello World → `Greeting`.
3. Optionally set as **Home**.
4. **Save & Close**, then view the site.
   You’ll see “Hi there Michael”.

---

## 8. Make List Items Clickable (Using Slug & Route Helper)

[31:10](https://youtu.be/1KBBtQUxMTc?t=1870)

In the `greetings` view, wrap each greeting in a link to the `greet` view:

```php
<ul>
<?php foreach ($this->items as $item): ?>
    <li>
        <a href="<?php echo JRoute::_('index.php?option=com_world&view=greet&id=' . $item->slug); ?>">
            <?php echo $item->greeting; ?>
        </a>
    </li>
<?php endforeach; ?>
</ul>
```

> JCB creates the `slug` automatically in the model (using `alias` + `id`).
> Check `models/greetings.php` or use the helper route method `WorldHelperRoute::getGreetRoute($slug)`.

Recompile and install.

---

## 9. Add Edit Links on Frontend

[34:55](https://youtu.be/1KBBtQUxMTc?t=2095)

1. In the **Custom PHP Tab** of the site view, add:

   ```php
   $this->edit = JRoute::_('index.php?option=com_world&task=greeting.edit');
   ```
2. In the default template, add:

   ```php
   <a href="<?php echo $this->edit . '&id=' . $this->item->id; ?>">Edit</a>
   ```
3. Recompile and Install.

If you click **Edit** without permission, Joomla shows a “not permitted” message.
Login as an authorized user to see the edit form.

---

## 10. Verify Permissions Logic

[38:40](https://youtu.be/1KBBtQUxMTc?t=2320)

The helper class (`/admin/helpers/world.php`) contains `getActions($view, $id = 0)` which returns an object of permissions:

* `core.create`
* `core.edit`
* `core.delete`
* `core.edit.state`

Use it to show/hide buttons based on user rights in your templates.

---

## Result

Congratulations 🎉

In under 30 minutes you’ve built a component that supports:

* Admin field definitions and database integration
* Dynamic Gets and site views
* Versioning and permissions
* Public frontend display and editing

Your new **Hello World** component now shows how quickly JCB can build powerful Joomla applications with just a few clicks.

---
