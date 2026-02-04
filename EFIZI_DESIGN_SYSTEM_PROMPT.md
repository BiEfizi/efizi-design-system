# Efizi Design System — Prompt Reference

> **Como usar:** Cole este conteúdo no início de qualquer prompt (Claude, Lovable, Cursor, etc.) ao criar um novo projeto que deve seguir o padrão visual Efizi.

---

## Stack & Fundação

- **Framework:** Next.js 16 (App Router, RSC)
- **Linguagem:** TypeScript
- **Estilização:** Tailwind CSS v4 + CSS Variables (oklch)
- **Componentes:** shadcn/ui (estilo `new-york`) + componentes customizados
- **Ícones:** Lucide React
- **Fonte:** Montserrat (fallback: -apple-system, BlinkMacSystemFont, Segoe UI, sans-serif)
- **Utilitários:** `class-variance-authority` (CVA), `clsx`, `tailwind-merge`
- **Função cn():** `import { cn } from "@/lib/utils"` — combina `clsx` + `tailwind-merge`

---

## Design Tokens (globals.css)

### Identidade Visual Efizi

- **Cor primária:** Laranja vibrante `oklch(0.68 0.21 35)` → equivalente a ~#FF5414
- **Cor secundária:** Teal `oklch(0.52 0.09 180)` → equivalente a ~#228474
- **Background:** Cinza claro `oklch(0.975 0 0)` → ~#f7f7f7
- **Cards:** Branco puro `oklch(1 0 0)` → #ffffff
- **Texto:** Escuro `oklch(0.15 0 0)` → ~#121212
- **Fonte:** Montserrat
- **Border radius base:** 0.5rem (8px) — estilo arredondado suave
- **Focus ring:** Laranja primário (mesma cor do brand)

### Cores Semânticas Customizadas

- **Success:** Verde `oklch(0.6 0.15 145)` com texto branco
- **Warning:** Amarelo-laranja `oklch(0.75 0.15 75)` com texto escuro
- **Info:** Azul `oklch(0.6 0.15 250)` com texto branco
- **Destructive:** Vermelho `oklch(0.577 0.245 27.325)` com texto branco

### CSS Variables Completas — Light Mode

```css
:root {
  /* Base */
  --background: oklch(0.975 0 0);         /* #f7f7f7 - Cinza claro */
  --foreground: oklch(0.15 0 0);           /* #121212 - Texto escuro */

  /* Card */
  --card: oklch(1 0 0);                    /* #ffffff */
  --card-foreground: oklch(0.15 0 0);

  /* Popover */
  --popover: oklch(1 0 0);
  --popover-foreground: oklch(0.15 0 0);

  /* Primary (Efizi Orange) */
  --primary: oklch(0.68 0.21 35);          /* ~#FF5414 */
  --primary-foreground: oklch(1 0 0);      /* Branco */

  /* Secondary (Teal) */
  --secondary: oklch(0.52 0.09 180);       /* ~#228474 */
  --secondary-foreground: oklch(1 0 0);    /* Branco */

  /* Muted */
  --muted: oklch(0.95 0 0);
  --muted-foreground: oklch(0.55 0 0);

  /* Accent */
  --accent: oklch(0.95 0 0);
  --accent-foreground: oklch(0.15 0 0);

  /* Destructive */
  --destructive: oklch(0.577 0.245 27.325);
  --destructive-foreground: oklch(1 0 0);

  /* Borders & Inputs */
  --border: oklch(0.88 0 0);              /* #dadada */
  --input: oklch(0.81 0 0);               /* #c1c1c1 */
  --ring: oklch(0.68 0.21 35);            /* Laranja (focus ring) */

  /* Radius */
  --radius: 0.5rem;                        /* 8px */

  /* Charts */
  --chart-1: oklch(0.68 0.21 35);         /* Laranja */
  --chart-2: oklch(0.52 0.09 180);        /* Teal */
  --chart-3: oklch(0.646 0.222 41.116);   /* Amarelo-laranja */
  --chart-4: oklch(0.6 0.118 184.704);    /* Ciano */
  --chart-5: oklch(0.769 0.188 70.08);    /* Amarelo */

  /* Sidebar */
  --sidebar: oklch(1 0 0);
  --sidebar-foreground: oklch(0.15 0 0);
  --sidebar-primary: oklch(0.68 0.21 35);
  --sidebar-primary-foreground: oklch(1 0 0);
  --sidebar-accent: oklch(0.95 0 0);
  --sidebar-accent-foreground: oklch(0.15 0 0);
  --sidebar-border: oklch(0.88 0 0);
  --sidebar-ring: oklch(0.68 0.21 35);

  /* Semantic */
  --success: oklch(0.6 0.15 145);
  --success-foreground: oklch(1 0 0);
  --warning: oklch(0.75 0.15 75);
  --warning-foreground: oklch(0.15 0 0);
  --info: oklch(0.6 0.15 250);
  --info-foreground: oklch(1 0 0);
}
```

### CSS Variables Completas — Dark Mode

```css
.dark {
  --background: oklch(0.15 0 0);
  --foreground: oklch(0.985 0 0);

  --card: oklch(0.205 0 0);
  --card-foreground: oklch(0.985 0 0);

  --popover: oklch(0.205 0 0);
  --popover-foreground: oklch(0.985 0 0);

  --primary: oklch(0.68 0.21 35);          /* Laranja mantido vibrante */
  --primary-foreground: oklch(1 0 0);

  --secondary: oklch(0.52 0.09 180);       /* Teal mantido */
  --secondary-foreground: oklch(1 0 0);

  --muted: oklch(0.269 0 0);
  --muted-foreground: oklch(0.708 0 0);

  --accent: oklch(0.269 0 0);
  --accent-foreground: oklch(0.985 0 0);

  --destructive: oklch(0.704 0.191 22.216);
  --destructive-foreground: oklch(1 0 0);

  --border: oklch(1 0 0 / 10%);
  --input: oklch(1 0 0 / 15%);
  --ring: oklch(0.68 0.21 35);

  --chart-1: oklch(0.68 0.21 35);
  --chart-2: oklch(0.52 0.09 180);
  --chart-3: oklch(0.769 0.188 70.08);
  --chart-4: oklch(0.627 0.265 303.9);
  --chart-5: oklch(0.645 0.246 16.439);

  --sidebar: oklch(0.205 0 0);
  --sidebar-foreground: oklch(0.985 0 0);
  --sidebar-primary: oklch(0.68 0.21 35);
  --sidebar-primary-foreground: oklch(1 0 0);
  --sidebar-accent: oklch(0.269 0 0);
  --sidebar-accent-foreground: oklch(0.985 0 0);
  --sidebar-border: oklch(1 0 0 / 10%);
  --sidebar-ring: oklch(0.68 0.21 35);

  --success: oklch(0.65 0.15 145);
  --success-foreground: oklch(1 0 0);
  --warning: oklch(0.8 0.15 75);
  --warning-foreground: oklch(0.15 0 0);
  --info: oklch(0.65 0.15 250);
  --info-foreground: oklch(1 0 0);
}
```

### Tailwind v4 Theme Mapping

```css
@theme inline {
  --color-background: var(--background);
  --color-foreground: var(--foreground);
  --color-card: var(--card);
  --color-card-foreground: var(--card-foreground);
  --color-popover: var(--popover);
  --color-popover-foreground: var(--popover-foreground);
  --color-primary: var(--primary);
  --color-primary-foreground: var(--primary-foreground);
  --color-secondary: var(--secondary);
  --color-secondary-foreground: var(--secondary-foreground);
  --color-muted: var(--muted);
  --color-muted-foreground: var(--muted-foreground);
  --color-accent: var(--accent);
  --color-accent-foreground: var(--accent-foreground);
  --color-destructive: var(--destructive);
  --color-destructive-foreground: var(--destructive-foreground);
  --color-border: var(--border);
  --color-input: var(--input);
  --color-ring: var(--ring);
  --color-chart-1: var(--chart-1);
  --color-chart-2: var(--chart-2);
  --color-chart-3: var(--chart-3);
  --color-chart-4: var(--chart-4);
  --color-chart-5: var(--chart-5);
  --color-sidebar: var(--sidebar);
  --color-sidebar-foreground: var(--sidebar-foreground);
  --color-sidebar-primary: var(--sidebar-primary);
  --color-sidebar-primary-foreground: var(--sidebar-primary-foreground);
  --color-sidebar-accent: var(--sidebar-accent);
  --color-sidebar-accent-foreground: var(--sidebar-accent-foreground);
  --color-sidebar-border: var(--sidebar-border);
  --color-sidebar-ring: var(--sidebar-ring);
  --color-success: var(--success);
  --color-success-foreground: var(--success-foreground);
  --color-warning: var(--warning);
  --color-warning-foreground: var(--warning-foreground);
  --color-info: var(--info);
  --color-info-foreground: var(--info-foreground);
  --radius-sm: calc(var(--radius) - 4px);
  --radius-md: calc(var(--radius) - 2px);
  --radius-lg: var(--radius);
  --radius-xl: calc(var(--radius) + 4px);
  --radius-2xl: calc(var(--radius) + 8px);
  --radius-3xl: calc(var(--radius) + 12px);
  --radius-4xl: calc(var(--radius) + 16px);
}
```

### Base Layer

```css
@layer base {
  * {
    @apply border-border outline-ring/50;
  }
  body {
    @apply bg-background text-foreground;
    font-family: 'Montserrat', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  }
}
```

---

## Componentes Base (shadcn/ui new-york)

Todos os componentes usam o padrão `data-slot` para identificação e composição.

### Button

Variantes: `default`, `destructive`, `outline`, `secondary`, `ghost`, `link`
Tamanhos: `default` (h-9), `xs` (h-6), `sm` (h-8), `lg` (h-10), `icon` (size-9), `icon-xs` (size-6), `icon-sm` (size-8), `icon-lg` (size-10)

```tsx
import { Button } from "@/components/ui/button"

<Button variant="default" size="default">Texto</Button>
<Button variant="outline" size="sm">Pequeno</Button>
<Button variant="ghost" size="icon"><Icon /></Button>
```

### Badge

Variantes: `default`, `secondary`, `destructive`, `outline`, `ghost`, `link`
Formato: `rounded-full` (pill shape)

```tsx
import { Badge } from "@/components/ui/badge"

<Badge variant="default">Label</Badge>
<Badge variant="outline">Status</Badge>
```

### Card

Composição: `Card` > `CardHeader` > `CardTitle` + `CardDescription` + `CardAction` > `CardContent` > `CardFooter`
Estilo: `rounded-xl`, `border`, `shadow-sm`, `gap-6`, `py-6`

```tsx
import { Card, CardHeader, CardTitle, CardDescription, CardContent, CardFooter } from "@/components/ui/card"
```

### Input

Altura: `h-9`, border-radius: `rounded-md`
Focus: `focus-visible:border-ring focus-visible:ring-ring/50 focus-visible:ring-[3px]`
Erro: `aria-invalid:border-destructive`

```tsx
import { Input } from "@/components/ui/input"
```

### Tabs

Variantes da lista: `default` (bg-muted) e `line` (underline)
Suporta: orientação horizontal e vertical

```tsx
import { Tabs, TabsList, TabsTrigger, TabsContent } from "@/components/ui/tabs"

<Tabs defaultValue="tab1">
  <TabsList variant="line">
    <TabsTrigger value="tab1">Tab 1</TabsTrigger>
  </TabsList>
  <TabsContent value="tab1">Conteúdo</TabsContent>
</Tabs>
```

---

## Componentes Customizados (além do shadcn padrão)

### Field (formulários compostos)

Sistema completo de formulário com composição flexível e orientação responsiva.

```tsx
import {
  Field, FieldLabel, FieldDescription, FieldError,
  FieldGroup, FieldLegend, FieldSet, FieldContent, FieldTitle, FieldSeparator
} from "@/components/ui/field"

<FieldGroup>
  <Field orientation="vertical"> {/* ou "horizontal" | "responsive" */}
    <FieldLabel htmlFor="name">Nome</FieldLabel>
    <FieldContent>
      <Input id="name" />
      <FieldDescription>Seu nome completo</FieldDescription>
      <FieldError>Campo obrigatório</FieldError>
    </FieldContent>
  </Field>
</FieldGroup>
```

### Item (listas de conteúdo)

Componente flexível para listas de itens com media, ações e metadados.

Variantes: `default`, `outline`, `muted`
Tamanhos: `default` (p-4), `sm` (py-3 px-4)

```tsx
import {
  Item, ItemMedia, ItemContent, ItemTitle,
  ItemDescription, ItemActions, ItemGroup, ItemSeparator,
  ItemHeader, ItemFooter
} from "@/components/ui/item"

<ItemGroup>
  <Item variant="outline">
    <ItemMedia variant="icon"><UserIcon /></ItemMedia>
    <ItemContent>
      <ItemTitle>Título</ItemTitle>
      <ItemDescription>Descrição do item</ItemDescription>
    </ItemContent>
    <ItemActions>
      <Button variant="ghost" size="icon-sm"><MoreHorizontalIcon /></Button>
    </ItemActions>
  </Item>
</ItemGroup>
```

### Empty (estados vazios)

```tsx
import { Empty, EmptyHeader, EmptyMedia, EmptyTitle, EmptyDescription, EmptyContent } from "@/components/ui/empty"

<Empty>
  <EmptyHeader>
    <EmptyMedia variant="icon"><InboxIcon /></EmptyMedia>
    <EmptyTitle>Nenhum item</EmptyTitle>
    <EmptyDescription>Adicione seu primeiro item.</EmptyDescription>
  </EmptyHeader>
  <EmptyContent>
    <Button>Criar item</Button>
  </EmptyContent>
</Empty>
```

### InputGroup (inputs compostos)

Input com addons (prefixo, sufixo, botões). Alinhamentos: `inline-start`, `inline-end`, `block-start`, `block-end`.

```tsx
import {
  InputGroup, InputGroupAddon, InputGroupButton,
  InputGroupInput, InputGroupText, InputGroupTextarea
} from "@/components/ui/input-group"

<InputGroup>
  <InputGroupAddon align="inline-start">
    <InputGroupText>R$</InputGroupText>
  </InputGroupAddon>
  <InputGroupInput placeholder="0,00" />
  <InputGroupAddon align="inline-end">
    <InputGroupButton size="icon-xs" variant="ghost"><CopyIcon /></InputGroupButton>
  </InputGroupAddon>
</InputGroup>
```

### ButtonGroup

```tsx
import { ButtonGroup, ButtonGroupSeparator, ButtonGroupText } from "@/components/ui/button-group"

<ButtonGroup orientation="horizontal">
  <Button variant="outline">Opção A</Button>
  <ButtonGroupSeparator />
  <Button variant="outline">Opção B</Button>
</ButtonGroup>
```

### Kbd (atalhos de teclado)

```tsx
import { Kbd, KbdGroup } from "@/components/ui/kbd"

<KbdGroup><Kbd>⌘</Kbd><Kbd>K</Kbd></KbdGroup>
```

### Spinner

```tsx
import { Spinner } from "@/components/ui/spinner"

<Spinner className="size-6" />
```

### NativeSelect

Select nativo do browser com estilo consistente. Tamanhos: `default` (h-9), `sm` (h-8).

```tsx
import { NativeSelect, NativeSelectOption } from "@/components/ui/native-select"

<NativeSelect size="default">
  <NativeSelectOption value="1">Opção 1</NativeSelectOption>
</NativeSelect>
```

---

## Componentes shadcn/ui Disponíveis (lista completa)

Accordion, AlertDialog, Alert, AspectRatio, Avatar, Badge, Breadcrumb, Button, ButtonGroup, Calendar, Card, Carousel, Chart, Checkbox, Collapsible, Combobox, Command, ContextMenu, Dialog, Drawer, DropdownMenu, Empty, Field, Form, HoverCard, InputGroup, InputOTP, Input, Item, Kbd, Label, Menubar, NativeSelect, NavigationMenu, Pagination, Popover, Progress, RadioGroup, Resizable, ScrollArea, Select, Separator, Sheet, Sidebar, Skeleton, Slider, Sonner (toast), Spinner, Switch, Table, Tabs, Textarea, ToggleGroup, Toggle, Tooltip

---

## Padrões de Código

### Imports

```tsx
// Utilitário de classes
import { cn } from "@/lib/utils"

// Componentes UI sempre de @/components/ui/
import { Button } from "@/components/ui/button"
import { Card, CardHeader, CardTitle, CardContent } from "@/components/ui/card"

// Ícones sempre de lucide-react
import { ChevronDownIcon, XIcon, SearchIcon } from "lucide-react"
```

### Padrão de Componente

```tsx
// Todos os componentes usam data-slot para identificação
// Todos aceitam className via cn() para composição
// Variantes são gerenciadas por CVA (class-variance-authority)
// Props são estendidas via React.ComponentProps<"element">

function MeuComponente({ className, variant = "default", ...props }: 
  React.ComponentProps<"div"> & VariantProps<typeof meuComponenteVariants>) {
  return (
    <div
      data-slot="meu-componente"
      data-variant={variant}
      className={cn(meuComponenteVariants({ variant, className }))}
      {...props}
    />
  )
}
```

### Focus & Estados

```
Focus:     focus-visible:border-ring focus-visible:ring-ring/50 focus-visible:ring-[3px]
Erro:      aria-invalid:ring-destructive/20 aria-invalid:border-destructive
Disabled:  disabled:pointer-events-none disabled:opacity-50
Dark mode: Prefixo dark: para overrides (custom-variant: &:is(.dark *))
```

---

## Regras de Uso

1. **Sempre use os componentes UI existentes** — nunca recrie botões, cards, inputs do zero
2. **Sempre use as variáveis CSS** — nunca hardcode cores (use `bg-primary`, não `bg-orange-500`)
3. **Sempre use `cn()` para classes** — nunca concatene strings de classe manualmente
4. **Sempre use Lucide** para ícones — nunca outro icon set
5. **Sempre use CVA** para variantes — nunca if/else com classes
6. **Sempre suporte dark mode** — use variáveis CSS e o prefixo `dark:`
7. **Sempre use `data-slot`** em componentes customizados para identificação
8. **Sempre use composição** — componentes são compostos (Card > CardHeader > CardTitle), não monolíticos
9. **Sempre use Montserrat** como fonte principal
10. **Use cores semânticas** — `success`, `warning`, `info` estão disponíveis além do padrão shadcn
11. **O laranja (#FF5414) é a cor da marca** — use `bg-primary` para CTAs e elementos de destaque
12. **O teal (#228474) é secundário** — use `bg-secondary` para acentos e variação visual
