# webionix-nextjs-coding-standard

## 1. Exports

### 1.1 We use "export default function" in the files:

```text
page.jsx
layout.jsx
error.jsx
loading.jsx
proxy.js
```

```javascript
export default function Page() {}
export default function Layout() {}
```

### 1.2 Regular React components. We use "export function" named exports:

```javascript
export function ReactComponent() {}
export function Header() {}
export function Logo() {}
export function Footer() {}
```

### 1.3 Local helpers inside components are arrow functions. They are not exported:

```javascript
const exampleFunction = () => {};
```

### 1.4 Utilities in /utils, /lib, /config also use "export function" named exports:

```javascript
export function exampleFunction() {}
export function getOrigin() {}
```

## 2. Import order and import groups (from top to bottom)

### 2.1 Imports

**Order of groups:**

```text
external libs (react / next / packages)
config
constants
utils / lib
hooks
components
images / icons
styles
```

**There is an empty line between groups:**

```javascript
import Link from "next/link";
import { usePathname } from "next/navigation";
import { motion } from "framer-motion";

import { routeList } from "@/config/routes/route-list";
import { companyInfo } from "@/config/company-info";

import { BLOG_CATEGORIES } from "@/constants/blog-categories";

import { generateAlternates } from "@/utils/seo/generate-alternates";
import { getOrigin } from "@/utils/origin";
import { getDictionary } from "@/lib/i18n/get-dictionary";

import { useScrollLock } from "@/hooks/use-scroll-lock";

import { Logo } from "@/components/shared/logo/logo";
import { Header } from "@/components/layout/header/header";

import HeroImage from "@/public/images/home/hero.webp";
import { LogoIcon } from "@/components/icons/logo-icon";

import styles from "./nav-menu-header.module.css";
```

## 3. Naming

### 3.1 File and folder names in JS, TS, CSS, SCSS, SASS, JSX, TSX, ...

**Format — kebab-case:**

```text
folder-example-name
nav-menu-header.jsx
example-logo.jsx
blog-page-list.js
create-paginated-routes.js
nav-menu-header.module.css
example-img.webp
```

**Constants — UPPER_SNAKE_CASE:**

```text
SEO_CONFIG.js
STATUS_CODES.js
```

### 3.2. Component names

**Format — PascalCase:**

```javascript
export function MobileMenu() {}
export function FooterNav() {}
```

### 3.3. Variable and function names

**Format — camelCase:**

```javascript
const mainNavList = [];
const isActive = pathName === href;
const logoData = await getDictionary(lang, "components/logo");
```

### 3.4. Configs and data structures

**Format — camelCase:**

```javascript
export const mainNavList = [{ id: 1, route: "/", routeKey: "home" }];
```

### 3.5 Naming of constants

**Format — UPPER_SNAKE_CASE:**

```javascript
export const API_BASE_URL = "https://api.base.com";
export const DEFAULT_PAGE_SIZE = 10;
export const IS_PRODUCTION = process.env.NODE_ENV === "production";
```

**Constants as objects or arrays:**

UPPER_SNAKE_CASE for the constant itself, camelCase for the keys inside

```javascript
export const SUPPORTED_LANGUAGES = ["en", "pl", "ua", "ru"];
export const BLOG_CONFIG = {
  articlesPerPage: 10,
  categoryNames: ["seo", "design", "development"],
  defaultSort: "latest",
};
```

**The entire /constants folder must contain only constants in UPPER_SNAKE_CASE:**

> `src/constants/`

```text
SEO_CONFIG.js
BLOG_CATEGORIES.js
VALIDATION_PATTERNS.js
STATUS_CODES.js
```
