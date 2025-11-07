title: Accueil
alpha: true

## Bienvenue sur ma base de connaissances

!!! info "Ce que vous trouverez ici : "

    Dans cette base de connaissances, je vais répertorier tout ce que j'ai appris et que je trouve intéressant de savoir dans mon métier (Administrateur Systèmes, Réseaux et Sécurité).

## Contenu types de la base

* Fichiers de configurations entiers. ex : [cisco-48p](./ais/conf/cisco-48p.md),
* Guides d'installations. ex : [mkdocs](./general/mkdocs.md),
* Petites infos diverses dans des fichiers datés. ex : [27-01-25](./daily/27-01-25.md).

## Quelques liens utiles

| [ +mdi:web+ Portfolio](https://dreynaud.ipv64.net) | [ +line-md:linkedin+ LinkedIn](https://linkedin.com/in/dreynaud) | [ +line-md:github-loop+ Github](https://github.com/coockiepickle) | [ +cib:ko-fi+ ko-fi](https://ko-fi.com/A0A51NJ7PE) |

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
        { value: 5, name: "Terminé" },
        { value: 15, name: "En rédaction" },
        { value: 5, name: "Mise en page en cours" },
        { value: 75, name: "Pas commencé" },
        { value: 0, name: "Erreur rencontrée" },
      ],
    },
  ],
};

///

## Theme Docs

[mkdocs-shadcn docs](https://asiffer.github.io/mkdocs-shadcn/) | [iconify](https://icon-sets.iconify.design/)
