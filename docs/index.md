title: Accueil
alpha: true

## Bienvenue sur ma base de connaissances

!!! info "Ce que vous trouverez ici : "

    Dans cette base de connaissances, je vais répertorier tout ce que j'ai appris et que je trouve intéressant de savoir dans mon métier (Administrateur Systèmes, Réseaux et Sécurité).

## Contenu types de la base

* Fichiers de configurations entiers. ex : [cisco-48p](./ais/conf/cisco-48p.md),
* Guides d'installations. ex : [mkdocs](./general/mkdocs.md),
* Petites infos diverses dans des fichiers datés. ex : [27-01-25](./daily/27-01-25.md).

## Suivi des modifications :

!!! info "Dernière mise à jour de la doc :" 
    `Mer 22/09/2026`

!!! info "Dernière page mise à jour :" 
    [Daily](./daily.md)

## Quelques liens utiles

<a class="button outline" href="https://dreynaud.ipv64.net">+mdi:web+ Portfolio</a>
<a class="button outline" href="https://linkedin.com/in/dreynaud">+line-md:linkedin+ LinkedIn</a>
<a class="button outline" href="https://github.com/coockiepickle">+line-md:github-loop+ Github</a>
<a class="button outline" href="https://ko-fi.com/A0A51NJ7PE">+cib:ko-fi+ ko-fi</a>

## Complétion de la base de connaissances

/// echarts
const option = {
  tooltip: {
    trigger: "item",
  },
  legend: {
    top: "5%",
    left: "center",
  },
  series: [
    {
      name: "Pourcentage (%)",
      type: "pie",
      radius: ["40%", "70%"],
      avoidLabelOverlap: false,
      itemStyle: {
        borderRadius: 10,
        borderColor: "#fff",
        borderWidth: 2,
      },
      label: {
        show: false,
        position: "center",
      },
      emphasis: {
        label: {
          show: false,
          fontSize: 40,
          fontWeight: "bold",
        },
      },
      labelLine: {
        show: false,
      },
      data: [
        { value: 30, name: "Terminé" },
        { value: 20, name: "En rédaction" },
        { value: 5, name: "Mise en page" },
        { value: 45, name: "Pas commencé" },
        { value: 0, name: "Erreur rencontrée" },
      ],
    },
  ],
};

///

## Theme Docs

<a class="button ghost" href="https://asiffer.github.io/mkdocs-shadcn/">+bxl:shadcn-ui+ mkdocs-shadcn docs</a>
<a class="button ghost" href="https://icon-sets.iconify.design/">+simple-icons:iconify+ iconify</a>
