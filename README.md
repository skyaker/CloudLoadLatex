# LaTeX шаблон ВКР в МИСИС

LaTeX шаблон для полного текста ВКР в университете МИСИС с примерами оформления и структурой. 
Прошел нормоконтроль, актуален как минимум на 2026 год.

## Требования

- **XeLaTeX**
- **BibTeX**

## Сборка

Из корня проекта (проще через расширения VScode/Pycharm):

```bash
xelatex -interaction=nonstopmode -output-directory=auxil main.tex
bibtex auxil/main
xelatex -interaction=nonstopmode -output-directory=auxil main.tex
xelatex -interaction=nonstopmode -output-directory=auxil main.tex
```

Готовый PDF: `auxil/main.pdf`.

## С чего начать

1. Замените `front_pages/titul.pdf` и `front_pages/diploma_task.pdf` на свои (титул без номера страницы).
2. Заполните файлы в `pages/` вместо примеров.
3. Добавьте источники в `pages/bibliography.bib` (в bib 2 записи-примера).
4. Картинки кладите в `assets/images/` и подключайте через `\includegraphics`.

Порядок разделов задаётся в `main.tex` через `\input{...}`.

## Структура

```
main.tex              — точка входа, порядок разделов
pages/preambula.tex   — пакеты, поля, стили заголовков, списков, рисунков
pages/*.tex           — разделы работы
pages/bibliography.bib
gost2008_local.bst    — стиль списка литературы (ГОСТ)
front_pages/          — титул и дипломное задание (PDF)
assets/images/        — рисунки
timesnewroman*.ttf    — шрифты
```

## Особенности шаблона

- **Движок:** только XeLaTeX, не pdfLaTeX.
- **Шрифт:** Times New Roman (файлы `.ttf` в корне).
- **Кегль:** 14 pt, полуторный интервал.
- **Титул и задание:** вставляются готовыми PDF (`pdfpages`), не верстаются в LaTeX.
- **Нумерация:** в `main.tex` задан `\setcounter{page}{4}` — первая страница реферата считается 4-й (после титула и задания).
- **Стили библиографии:** `gost2008_local.bst`.
- **Правила оформления:** `.cursor/rules/format.mdc` (md файл с промптом для llm с форматом).

## P.S.

Если вам это помогло, закиньте звездочку в репо⭐