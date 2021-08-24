# What To Do About ‘Grandchild’ Selectors (And Beyond)?
To clarify, you would use a grandchild selector when you need to reference an element that is nested two levels deep. These bad boys are the bane of my life, and I’m sure their misuse is one of the reasons people have an immediate aversion to BEM. I’ll give you an example:

```html
<div class="c-card">

    <div class="c-card__header">
        <!-- Here comes the grandchild… -->
        <h2 class="c-card__header__title">Title text here</h2>
    </div>

    <div class="c-card__body">

        <img class="c-card__body__img" src="some-img.png" alt="description">
        <p class="c-card__body__text">Lorem ipsum dolor sit amet, consectetur</p>
        <p class="c-card__body__text">Adipiscing elit.
            <a href="/somelink.html" class="c-card__body__text__link">Pellentesque amet</a>
        </p>

    </div>
</div>
```

As you might imagine, naming in this way can quickly get out of hand, and the more nested a component is, the more hideous and unreadable the class names become. I’ve used a short block name of c-card and the short element names of body, text and link, but you can imagine how out of control it gets when the initial block element is named something like c-drop-down-menu.

I believe the double-underscore pattern should appear only once in a selector name. BEM stands for Block__Element–Modifier, not Block__Element__Element–Modifier. So, avoid multiple element level naming. If you’re getting to great-great-great-grandchild levels, then you’ll probably want to revisit your component structure anyway.

BEM naming isn’t strictly tied to the DOM, so it doesn’t matter how many levels deep a descendent element is nested. The naming convention is there to help you identify relationships with the top-level component block — in this case, c-card.

This is how I would treat the same card component:

```html
<div class="c-card">
    <div class="c-card__header">
        <h2 class="c-card__title">Title text here</h2>
    </div>

    <div class="c-card__body">

        <img class="c-card__img" src="some-img.png" alt="description">
        <p class="c-card__text">Lorem ipsum dolor sit amet, consectetur</p>
        <p class="c-card__text">Adipiscing elit.
            <a href="/somelink.html" class="c-card__link">Pellentesque amet</a>
        </p>

    </div>
</div>
```

This means that all of the descendent elements will be affected only by the card block. So, we would be able to move the text and images into c-card__header or even introduce a new c-card__footer element without breaking the semantic structure.

Source: [Smashing Magazine - Battling BEM CSS: 10 Common Problems And How To Avoid Them](https://www.smashingmagazine.com/2016/06/battling-bem-extended-edition-common-problems-and-how-to-avoid-them)
