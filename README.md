# Ateliers Pratiques : Infrastructure as Code avec Ansible

<table><tr><td style="vertical-align: top; width: 70%;"><blockquote><strong>NOTE</strong><br>
      Ce dépôt contient l'ensemble des <strong>ateliers pratiques</strong> et des
      <strong>exercices</strong> réalisés dans le cadre du cours <strong>Infrastructure as Code
      (IaC)</strong> à <strong>IMT Mines Alès</strong>.<br><br>
      Le cours se concentre sur la technologie <strong>Ansible</strong>, un outil
      d'automatisation dédié à la <strong>gestion de configuration</strong> et au
      <strong>déploiement d'infrastructures</strong>.
      </blockquote></td></tr></table>

---

<p align="center">
  <a href="https://github.com/nathanmartel21/ansible_kovacs/commits/main">
    <img src="https://img.shields.io/badge/build-passing-brightgreen?style=flat-square" alt="CI Status"/>
  </a>
  <img src="https://img.shields.io/badge/outil-Ansible-black?logo=ansible&logoColor=white" alt="Ansible"/>
  <img src="https://img.shields.io/badge/infrastructure-IaC-blue" alt="Infrastructure as Code"/>
  <img src="https://img.shields.io/badge/école-IMT%20Mines%20Alès-orange" alt="IMT Mines Alès"/>
  <img src="https://img.shields.io/badge/langue-Français-blue" alt="Français"/>
</p>

---

## À propos de l'auteur

<table align="center">
  <tr>
    <th>Author</th>
  </tr>
  <tr>
    <td align="center">
      <a href="https://github.com/nathanmartel21">
        <img src="https://github.com/nathanmartel21.png?size=115" width="115" alt="@nathanmartel21" /><br />
        <sub>@nathanmartel21</sub>
      </a>
      <br /><br />
      <a href="https://github.com/sponsors/nathanmartel21">
        <img src="https://img.shields.io/badge/sponsor-30363D?style=for-the-badge&logo=GitHub-Sponsors&logoColor=white" alt="Sponsor nathanmartel21" />
      </a>
    </td>
  </tr>
</table>

Le seul auteur de ce dépôt s'appelle **Nathan MARTEL**, étudiant promo INFRES17 en deuxième année à l'**École des Mines d'Alès**. Je suis également étudiant alternant chez **Groupama Supports et Services** en tant qu'**apprenti ingénieur automation**. Je travaille donc avec **Ansible** tous les jours depuis un an et demi, j'ai déjà une solide maîtrise de cet outil et des concepts liés à l'Infrastructure as Code.

---

## À propos du projet

Ce projet est un recueil d'ateliers pratiques progressifs visant à maîtriser **Ansible**. En partant de l'initialisation d'environnements locaux avec **Vagrant** et **VirtualBox**, ce dépôt couvre toutes les étapes d'apprentissage : de l'installation du Control Node à la configuration avancée (handlers, précédence des variables, facts multi-distributions, etc.) en passant par la mise en place de l'authentification et des inventaires.

Chaque laboratoire est documenté de manière approfondie avec des explications pas à pas, des extraits de code et des captures d'écran des résultats obtenus.

*⚠️ Remarque : Les documents techniques de ce dépôt ont été rédigés avec une classification initiale **TLP: RED**.*

## Documentation

La documentation complète et interactive de ce projet est propulsée par **Zensical**. Pour la générer et la consulter en local avec son thème et sa navigation personnalisée, suivez ces étapes :

```bash
python3 -m venv .venv
source .venv/bin/activate

pip install zensical

zensical serve
```

Ouvrez ensuite votre navigateur web et rendez-vous à l'adresse **[http://localhost:8000](http://localhost:8000)** pour parcourir les ateliers interactifs.

## Structuration du projet

Le projet est découpé en plusieurs dossiers, chacun correspondant à une thématique de configuration ou à un niveau de difficulté précis :

- **[`challenges-labo/`](docs/challenges-labo/)** : Prise en main de l'environnement Vagrant. Déploiement de clusters Alpine Linux et d'environnements multi-distributions (Rocky, Debian, OpenSUSE, Ubuntu).
- **[`challenges-installer-ansible/`](docs/challenges-installer-ansible/)** : Démonstration de différentes méthodes d'installation du Control Host Ansible (via un PPA sur Ubuntu ou via PIP dans un `virtualenv` sur Rocky Linux).
- **[`challenges-authentification/`](docs/challenges-authentification/)** : Mise en place des clés SSH et du fichier `known_hosts` pour l'authentification sans mot de passe entre le Control Host et les Target Hosts.
- **[`challenges-configuration-de-base/`](docs/challenges-configuration-de-base/)** : Initiation à l'organisation d'un projet Ansible, paramétrage du fichier `ansible.cfg`, gestion des inventaires statiques et mise en place de la journalisation.
- **[`challenges-idempotence/`](docs/challenges-idempotence/)** : Illustration par la pratique du concept clé d'idempotence (comparaison entre les modules `package`, `copy`, `file` et l'absence d'idempotence du module `command`).
- **[`challenges-serveur-web/`](docs/challenges-serveur-web/)** : Création d'un playbook robuste capable de s'adapter automatiquement à la distribution cible (Debian, Rocky, SUSE) pour installer Apache en s'appuyant sur les *Ansible facts* (`ansible_os_family`).
- **[`challenges-handlers/`](docs/challenges-handlers/)** : Utilisation de la directive `notify` et des `handlers` pour n'effectuer des actions (ex: redémarrer `chrony`) que lorsqu'une modification réelle de la configuration est détectée.
- **[`challenges-variables/`](docs/challenges-variables/)** : Découverte de la précédence et des différentes méthodes d'injection de variables (`play vars`, `set_fact`, `group_vars`, `host_vars`, surcharge via `extra vars` et saisie via `vars_prompt`).
- **[`challenges-variables-enregistrees/`](docs/challenges-variables-enregistrées/)** : Utilisation de la directive `register` pour capturer la sortie de commandes (`uname`, `rpm`) et la manipuler avec `debug`. Introduction à `changed_when` pour maîtriser l'état de changement des tâches.
- **[`challenges-facts-variables-implictes/`](docs/challenges-facts-variables-implictes/)** : Intégration des facts (`ansible_pkg_mgr`, `ansible_python_version`, `ansible_dns`) et des variables implicites (`inventory_hostname`) pour récupérer dynamiquement des informations sur les cibles.
- **[`challenges-cibles-hétérogènes/`](docs/challenges-cibles-hétérogènes/)** : Gestion de Target Hosts hétérogènes pour déployer un service (`chrony`) sur diverses distributions (Debian, Ubuntu, Rocky, SUSE) en utilisant des conditions ou la directive `set_fact`.
- **[`challenges-jinja-templates/`](docs/challenges-jinja-templates/)** : Manipulation des templates Jinja2 et du module `template` pour générer et injecter dynamiquement des fichiers de configuration adaptés au système cible.

## Ressources

Les ateliers sont basés sur la formation :

- **Source** : [Formation Ansible](https://formations.microlinux.fr/ansible/a-propos/)
- **Auteur de la formation** : Microlinux (Nicolas Kovacs)

## Licence

Ce dépôt est distribué sous la classification **TLP: RED**.

Pour plus de détails sur les restrictions de partage et d'utilisation, veuillez consulter le fichier de [LICENSE.md](LICENSE).
