# 🛠️ Orchestration d’un Pipeline Big Data avec Apache Airflow

## 📌 Description du Lab

Ce laboratoire pratique a pour objectif de mettre en place un **pipeline Big Data complet**, orchestré à l’aide d’**Apache Airflow**, simulant un workflow industriel de bout en bout.

Le pipeline couvre toutes les étapes classiques d’un système Big Data :
- ingestion des données,
- stockage dans un Data Lake,
- transformation,
- chargement dans un Data Lakehouse,
- exploitation analytique.

L’ensemble est orchestré, supervisé et contrôlé via l’interface web d’Airflow.

---

## 🎯 Objectifs pédagogiques

À la fin de ce lab, vous serez capable de :

- Comprendre un pipeline Big Data end-to-end
- Identifier les rôles du Data Lake et du Data Lakehouse
- Implémenter un DAG Airflow représentant un pipeline réel
- Orchestrer les dépendances entre les tâches
- Superviser et diagnostiquer l’exécution via l’interface Airflow

---

## 🧱 Architecture du Pipeline Big Data

### Pipeline logique

```

Sources → Ingestion → Data Lake (RAW) → Traitement → Data Lakehouse (CURATED) → Analytics / BI / IA

```

### Explication
- **Data Lake (RAW)** : stockage des données brutes
- **Traitement** : nettoyage et structuration
- **Data Lakehouse (CURATED)** : données fiables prêtes pour l’analyse
- **Airflow** : orchestration et supervision du pipeline

📷 *Schéma du pipeline Big Data*  
> *(Insérer ici une image du pipeline logique)*

---

## 🧰 Technologies utilisées

- **Apache Airflow 2.8.1**
- **Docker & Docker Compose**
- **PostgreSQL** (base de métadonnées Airflow)
- **Python** (simulation des traitements Big Data)
- **Système de fichiers local** (Data Lake & Lakehouse)

---

## 📁 Structure du projet

```

airflow-bigdata-pipeline/
│
├── docker-compose.yml
├── dags/
│   └── bigdata_pipeline.py
└── data/
├── raw/
├── processed/
└── curated/

````

### Rôle des dossiers
- `raw/` : Data Lake (données brutes)
- `processed/` : zone intermédiaire
- `curated/` : Data Lakehouse (données prêtes pour l’analyse)

---

## 🚀 Installation et lancement

### 1️⃣ Démarrer les services

```bash
docker-compose up -d
````

### 2️⃣ Initialiser Airflow (une seule fois)

```bash
docker-compose run airflow-webserver airflow db init
```

### 3️⃣ Créer l’utilisateur administrateur (une seule fois)

```bash
docker-compose run airflow-webserver airflow users create \
  --username airflow \
  --password airflow \
  --firstname Airflow \
  --lastname Admin \
  --role Admin \
  --email admin@airflow.local
```

### 4️⃣ Accéder à l’interface Airflow

* URL : [http://localhost:8080](http://localhost:8080)
* Username : `airflow`
* Password : `airflow`

📷 *Interface de connexion Airflow*

> *(Insérer ici une capture de l’écran de login Airflow)*

---

## 🧠 Description du DAG Big Data

Le DAG `bigdata_pipeline_complete` orchestre les tâches suivantes :

1. **Ingestion** : création des données brutes (Data Lake)
2. **Validation** : vérification de l’existence des données
3. **Transformation** : nettoyage et structuration
4. **Chargement Lakehouse** : données finales pour l’analyse
5. **Analytics** : exploitation métier

📷 *Vue Graph du DAG Airflow*

> *(Insérer ici une capture de la vue Graph)*

---

## 🔄 Orchestration et exécution

### Activer le DAG

* Repérer `bigdata_pipeline_complete`
* Activer le DAG (bouton ON)

📷 *Activation du DAG dans Airflow*

> *(Insérer ici une image du DAG activé)*

### Lancer le pipeline

* Cliquer sur **Trigger DAG**
* Confirmer l’exécution

📷 *Lancement manuel du DAG*

> *(Insérer ici une capture du bouton Trigger DAG)*

---

## 📊 Suivi et supervision

### États des tâches

* 🟢 Vert : succès
* 🔴 Rouge : échec
* 🔵 Bleu : en cours
* ⚪ Gris : non exécutée

📷 *Exécution du pipeline en temps réel*

> *(Insérer ici une capture montrant les tâches colorées)*

### Logs

* Cliquer sur une tâche
* Ouvrir l’onglet **Log**
* Analyser les messages d’exécution

📷 *Logs d’une tâche Airflow*

> *(Insérer ici une capture des logs)*

---

## ✅ Vérification des résultats

Après exécution, les fichiers suivants doivent exister :

```
data/raw/sales.csv
data/processed/sales_clean.csv
data/curated/sales_curated.csv
```

📷 *Structure finale des fichiers*

> *(Insérer ici une capture du dossier data/)*

---

## ⚠️ Gestion des erreurs

En cas d’échec :

* consulter les logs,
* corriger le problème si nécessaire,
* cliquer sur **Clear**,
* relancer uniquement la tâche concernée.

Cela permet de ne pas redémarrer tout le pipeline.

---

## 🏁 Conclusion

Ce lab illustre concrètement :

* la mise en place d’un pipeline Big Data réaliste,
* l’orchestration avec Apache Airflow,
* la supervision et la gestion des erreurs,
* les bonnes pratiques utilisées en environnement industriel.

Il constitue une base solide pour évoluer vers des pipelines distribués (Spark, Kafka, Cloud).

---

### 📌 Auteur

**Zakaria El Guazzar**
Master Intelligence Artificielle
