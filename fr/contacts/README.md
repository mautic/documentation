# Contacts

*Les prospects ont été renommés en contacts lors de Mautic 1.4.0.*

Les contacts sont le point central d'une plateforme de marketing automation. Ils représentent toutes les personnes qui ont visité votre site web ou interagi avec vous en quelque sorte.

### Types de contacts

Il existe deux types de contacts :
* **Contacts anonymes** (ou visiteurs) — ce sont les visiteurs de votre site qui ne sont pas encore identifiés par un formulaire ou une autre interaction.
  * Ces contacts sont tracés par Mautic dès leur première visite mais restent masqués.
* **Contacts standards** — ces contacts se sont identifiés par un formulaire ou une autre action. Comme résultat, ces contacts ont généralement un nom, email, etc.

#### Contacts anonymes (visiteurs)

Les contacts anonymes sont des visiteurs de votre site qui n'ont pas encore été identifiés par une forme ou une autre d'interaction. Ces contacts sont suivis par Mautic, mais généralement restent cachés pour ne pas encombrer votre liste de contacts. Vous pouvez afficher les contacts anonymes en utilisant l'affichage des anonymes dans la liste des contacts.

Les contacts anonymes sont suivis, car ils sont vos futurs clients. En les suivant tout au long de leur comportement et avant même qu'ils engagent une action sur votre site (soumission de formulaire par exemple), vous enregistrez un fil d'activité de ce comportement. Cela vous permettra d'en apprendre beaucoup sur leur profil par la suite.

##### Texte de recherche

```
is:anonymous
```

![](/media/contacts-anonymous.jpg)
La liste résultante contient les adresses IP des visiteurs qui n'ont pas encore fourni d'information supplémentaires.

#### Contacts standards

Le deuxième type de contacts sont les contacts standard. Ce sont des contacts qui ont fourni des informations supplémentaires par le biais d'un formulaire ou d'une autre source, ou que ces informations sont connues car vous avez eu des interactions avec eux avant. Par conséquent, ces contacts ont typiquement un nom, e-mail, et d'autres informations d'identification pouvant être associées à une personne.

Le contact standard est celui que nous préférons dans Mautic. Ce sont des contacts qui peuvent avoir commencé comme contact anonyme mais qui ont à un moment donné des informations supplémentaires telles que le nom, l'adresse e-mail, un identifiant de réseau social, ou d'autres caractéristiques d'identification. Ces contacts sont ceux qui peuvent ensuite être nourris par la plateforme de marketing automation.

Les informations suivantes dans la section [Gestion des contacts](https://www.mautic.org/docs/en/contacts/managing_contacts.html) fournira plus d'informations sur ce qui peut être géré avec ces contacts standard.
