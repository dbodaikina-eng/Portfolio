# Portfolio 2026 — horizontal accordion

## Что куда

- `index.html` — готовая страница, один файл (картинки, скрипты, шрифты-ссылки внутри). Положить в корень репозитория `portfolio2026` и запушить — GitHub Pages откроет её как главную.
- `src/` — исходники для правок: `Horizontal Accordion.dc.html`, `support.js`, `image-slot.js`, изображения. Можно тоже закоммитить (не обязательно для работы сайта).

## Внешние файлы в репозитории

Шоурил грузится с `https://dbodaikina-eng.github.io/portfolio2026/showreel.gif` — файл `showreel.gif` должен лежать в корне репо.

## Как выложить

```
cd portfolio2026
cp /path/to/dist/index.html .
git add index.html
git commit -m "Update portfolio"
git push
```

Settings → Pages → Source: `main` / root. Страница появится через ~1 минуту.
