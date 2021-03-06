---
title: Папки с материалами
---
## Глобальная папка с материалами

Материалы, не связанные с постами, такие как изображения, CSS или JavaScript файлы хранятся в папке `source`. Например, если нужно добавить несколько изображений в проект Hexo, то самый простой способ - положить их в исходный каталог изображений `source/images`. Затем можно получить к ним доступ, используя что-то вроде `![](/images/image.jpg)`.

## Папка с материалами поста

Для пользователей, которые планируют регулярно использовать изображения и/или другие материалы, и для тех, кто предпочитает разделять свои материалы по постам, Hexo обеспечивает возможность организовать управление материалами. Этот немного сложный, но в то же время удобный подход к управлению материалами может быть включён в настройках установкой переменной `post_asset_folder` в `_config.yml` в значение `true`.

``` yaml _config.yml
post_asset_folder: true
```

Если управление материалами включено, то каждый раз при создании поста создастся папка с аналогичным именем. Например: `hexo new [layout] <title>` создаст папку с именем `title`. Можно использовать файлы, связанные с постом, используя относительный путь, это облегчает и упрощает работу с материалами.

## Плагины тегов для создания относительных ссылок

Привязка изображений или других материалов, используя обычный синтаксис markdown и относительные пути, может привести к их неправильному отображению в архивных страницах или на главной странице. Плагины были созданы сообществом для решения этой проблемы в Hexo 2. С выходом Hexo 3 были добавлены в ядро новые плагины тегов. Они позволяют с лёгкостью создавать ссылки на ваши материалы в markdown:

```
{% asset_path slug %}
{% asset_img slug [title] %}
{% asset_link slug [title] %}
```

К примеру, при включённом управление материалами, если поместить в папку с материалами поста изображение `example.jpg`, то ссылка *не заработает* на главной странице, если использовать её по относительному пути `![](example.jpg)` (но в самом посте ссылка будет работать, как и положено).

Правильный путём для ссылки на изображение будет использование синтаксиса плагина тега, а не markdown:

```
{% asset_img example.jpg This is an example image %}
{% asset_img "spaced asset.jpg" "spaced title" %}
```

При использовании этого способа, изображение появится в самом посте и на главной странице и в архивах.
