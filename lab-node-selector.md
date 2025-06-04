# Laboratorio 7: Etiquetar Nodos y Usar NodeSelector en OpenShift

##  Objetivo

Aprender a etiquetar nodos del clúster y controlar dónde se ejecutan los pods utilizando `nodeSelector`. Cada estudiante trabajará con su propia etiqueta personalizada.

---

## Asignación por estudiante

Cada estudiante utilizará una etiqueta basada en su nombre asignado ('desarrollo`, `pruebas`, y  `produccion`).

---

## Paso 1: Etiquetar el nodo

Ejecuta el siguiente comando para etiquetar el nodo donde quieres que se ejecute tu aplicación:

```bash
oc label node <nombre-del-nodo> student=student01


---
## Paso 2: Crear la aplicación

```bash
oc new-app httpd --name=hello
---
## Paso 3: Agregar nodeSelector al deployment

```bash
oc edit deployment hello

```bash

nodeSelector:
  ambiente: pruebas
---

## Paso 4: Verificar el resultado

```bash
oc get pods -o wide
---
## Paso 5: Arreglar aplicacion con error en su proyecto
