## Paso 0: Vinculación
gcloud init

## Paso 1: Creación del repositorio
gcloud artifacts repositories create repo-mlops14-streamlit-regresion --repository-format docker --project mlops-14-project-deploy-fast --location us-central1

## Paso Automatizacion:
- git init
- git add .
- git commit -m "Proyecto de automatización de despliegue en GCR"
- git branch -M main
- git remote add origin https://github.com/KevinInoCol/mlops12-deploy-gcr-streamlit-regresion.git
- git push -u origin main



## Paso 2: Crear la imagen de mi APLICACION y subir al repositorio
gcloud builds submit --config=cloudbuild.yaml --project project-mlops-10-streamlit

## Paso 3: Comando para despliegue o ejecución de la imagen en el repositorio
gcloud run services replace service.yaml --region us-central1 --project project-mlops-10-streamlit

## Paso 4: OPCIONAL, Dar permisos de acceso a mi APLICACION. ESTO SE EJECUTA UNA SOLA VEZ
gcloud run services set-iam-policy servicio-streamlit-sesion3-kevin-inofuente gcr-service-policy.yaml --region us-central1 --project project-mlops-10-streamlit