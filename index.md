# Стандарти коду Next.js

---

## 1. Експорти

### 1.1 Використовуємо "export default function" у файлах:

```text
page.jsx
layout.jsx
error.jsx
loading.jsx
proxy.js
```

```javascript
export default function Page() {}
```

### 1.2 Звичайні React-компоненти. Використовуємо "export function" іменні експорти:

```javascript
export function Header() {}
export function Logo() {}
export function NavMenuHeader() {}
```

### 1.3 Локальні хелпери всередині компонентів стрілочні функції. Не експортуються:

```javascript
const formatPrice = () => {};
```

### 1.4 Утиліти в /utils, /lib, /config також "export function" іменні експорти:

```javascript
export function generateAlternates() {}
export function getOrigin() {}
```

---

## 2. Порядок імпортів, групи імпортів (зверху вниз)

### 2.1 Імпорти

**Порядок груп:**

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

**Між групами — порожній рядок:**

```javascript
import Link from "next/link";
import { usePathname } from "next/navigation";
import { motion } from "framer-motion";

import { routeList } from "@/config/routes/route-list";
import { COMPANY_INFO } from "@/config/company-info";

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

---

## 3. Неймінг

### 3.1 Імена файлів JS, TS, CSS, SCSS, SASS, JSX, TSX, ...

**Формат — kebab-case:**

```text
nav-menu-header.jsx
example-logo.jsx
blog-page-list.js
create-paginated-routes.js
nav-menu-header.module.css
example-img.webp
```

**Константи - UPPER_SNAKE_CASE:**

```text
SEO_CONFIG.js
STATUS_CODES.js
```

### 3.2. Імена компонентів

**Формат — PascalCase:**

```javascript
export function MobileMenu() {}
export function FooterNav() {}
```

### 3.3. Імена змінних та функцій

**Формат — camelCase:**

```javascript
const mainNavList = [];
const isActive = pathName === href;
const logoData = await getDictionary(lang, "components/logo");
```

### 3.4. Конфіги та структури даних

**Використовуємо camelCase:**

```javascript
export const mainNavList = [{ id: 1, route: "/", routeKey: "home" }];
```

### 3.5 Найменування констант

**Формат — UPPER_SNAKE_CASE:**

```javascript
export const API_BASE_URL = "https://api.test.com";
export const DEFAULT_PAGE_SIZE = 10;
export const IS_PRODUCTION = process.env.NODE_ENV === "production";
```

**Константи як обьєкти або масиви:**

UPPER_SNAKE_CASE — для самої константи
camelCase — для ключів всередині

```javascript
export const SUPPORTED_LANGUAGES = ["en", "pl", "ua", "ru"];
export const BLOG_CONFIG = {
  articlesPerPage: 10,
  categoryNames: ["seo", "design", "development"],
  defaultSort: "latest",
};
```

**Уся папка /constants повинна містити тільки константи у UPPER_SNAKE_CASE:**

> `src/constants/`

```text
SEO_CONFIG.js
BLOG_CATEGORIES.js
VALIDATION_PATTERNS.js
STATUS_CODES.js
```
