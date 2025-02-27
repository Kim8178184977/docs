---
title: Trabajar con el registro de contenedores
intro: 'Puedes almacenar y administrar imágenes de Docker y OCI en el {% data variables.product.prodname_container_registry %}, que utiliza el espacio de nombre para paquetes `https://{% data reusables.package_registry.container-registry-hostname %}`.'
product: '{% data reusables.gated-features.packages %}'
redirect_from:
  - /packages/managing-container-images-with-github-container-registry/pushing-and-pulling-docker-images
  - /packages/guides/container-guides-for-github-packages/pushing-and-pulling-docker-images
  - /packages/guides/pushing-and-pulling-docker-images
  - /packages/getting-started-with-github-container-registry/about-github-container-registry
  - /packages/managing-container-images-with-github-container-registry
  - /packages/working-with-a-github-packages-registry/enabling-improved-container-support-with-the-container-registry
  - /packages/getting-started-with-github-container-registry/enabling-improved-container-support
  - /packages/guides/container-guides-for-github-packages/enabling-improved-container-support
  - /packages/guides/enabling-improved-container-support
versions:
  fpt: '*'
  ghec: '*'
  ghes: '>= 3.5'
shortTitle: Container registry
ms.openlocfilehash: fc99e2e21a647c7a1a2517de8aa68822faac496e
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2022
ms.locfileid: '147705055'
---
{% data reusables.package_registry.container-registry-ghes-beta %}

## Acerca del {% data variables.product.prodname_container_registry %}

{% data reusables.package_registry.container-registry-benefits %}

{% ifversion ghes > 3.4 %}

Para usar el {% data variables.product.prodname_container_registry %} en {% data variables.product.product_name %}, el administrador del sitio debe configurar primero el {% data variables.product.prodname_registry %} para la instancia **y** habilitar el aislamiento de subdominio. Para obtener más información, consulta "[Introducción a los paquetes de GitHub para la empresa](/admin/packages/getting-started-with-github-packages-for-your-enterprise)" y "[Habilitación del aislamiento de subdominio](/admin/configuration/configuring-network-settings/enabling-subdomain-isolation)".

{% endif %}

## Acerca del soporte para el {% data variables.product.prodname_container_registry %}

El {% data variables.product.prodname_container_registry %} es actualmente compatible con los siguientes formatos de contenedores de imagen:

* [Docker Image Manifest V2, modelo 2](https://docs.docker.com/registry/spec/manifest-v2-2/)
* [Especificaciones de Open Container Initiative (OCI)](https://github.com/opencontainers/image-spec)

Cuando instalas o publicas una imagen de Docker, el {% data variables.product.prodname_container_registry %} es compatible con capas externas, tales como imágenes de Windows.

## Autenticarse en el {% data variables.product.prodname_container_registry %}

{% ifversion fpt or ghec or ghes > 3.4 %} {% data variables.product.prodname_container_registry %} (`ghcr.io`) dentro de un flujo de trabajo de {% data variables.product.prodname_actions %}, usa `GITHUB_TOKEN` para obtener la mejor experiencia y seguridad. {% data reusables.package_registry.authenticate_with_pat_for_v2_registry %} {% endif %}

{% ifversion ghes %} Asegúrate de reemplazar `HOSTNAME` por el nombre de host o la dirección IP de {% data variables.product.product_location_enterprise %} en los ejemplos siguientes.{% endif %}

{% data reusables.package_registry.authenticate-to-container-registry-steps %}

## Subir imágenes de contenedor

En este ejemplo se inserta la versión más reciente de `IMAGE_NAME`.
  ```shell
  $ docker push {% data reusables.package_registry.container-registry-hostname %}/OWNER/IMAGE_NAME:latest
  ```

En este ejemplo se inserta la versión `2.5` de la imagen.
  ```shell
  $ docker push {% data reusables.package_registry.container-registry-hostname %}/OWNER/IMAGE_NAME:2.5
  ```

Cuando publicas un paquete por primera vez, la visibilidad predeterminada es privada. Para cambiar la visibilidad o establecer permisos de acceso, consulte "[Configurar la visibilidad y el control de accesos de un paquete](/packages/learn-github-packages/configuring-a-packages-access-control-and-visibility)".

## Extraer imágenes de contenedor

### Extraer por resúmen

Para garantizar que siempre usa la misma imagen, puede especificar la versión exacta de la imagen de contenedor que quiere extraer de acuerdo con su valor de SHA de `digest`.

1. Para buscar el valor de SHA de hash, use `docker inspect` o `docker pull` y copie el valor de SHA después de `Digest:`.
  ```shell
  $ docker inspect {% data reusables.package_registry.container-registry-hostname %}/OWNER/IMAGE_NAME
  ```
2. Elimina la imagen localmente de acuerdo a tus necesidades.
  ```shell
  $ docker rmi  {% data reusables.package_registry.container-registry-hostname %}/OWNER/IMAGE_NAME:latest
  ```

3. Extraiga la imagen de contenedor con `@YOUR_SHA_VALUE` después del nombre de la imagen.
  ```shell
  $ docker pull {% data reusables.package_registry.container-registry-hostname %}/OWNER/IMAGE_NAME@sha256:82jf9a84u29hiasldj289498uhois8498hjs29hkuhs
  ```

### Extraer por nombre

  ```shell
  $ docker pull {% data reusables.package_registry.container-registry-hostname %}/OWNER/IMAGE_NAME
  ```

### Extraer por nombre y versión

Ejemplo de CLI de Docker que muestra una imagen que se extrae por su nombre y por la etiqueta de la versión `1.14.1`:
  ```shell
  $ docker pull {% data reusables.package_registry.container-registry-hostname %}/OWNER/IMAGE_NAME:1.14.1
  > 5e35bd43cf78: Pull complete
  > 0c48c2209aab: Pull complete
  > fd45dd1aad5a: Pull complete
  > db6eb50c2d36: Pull complete
  > Digest: sha256:ae3b135f133155b3824d8b1f62959ff8a72e9cf9e884d88db7895d8544010d8e
  > Status: Downloaded newer image for {% data reusables.package_registry.container-registry-hostname %}/orgname/image-name/release:1.14.1
  > {% data reusables.package_registry.container-registry-hostname %}/orgname/image-name/release:1.14.1
  ```

### Extraer por nombre y última versión

  ```shell
  $ docker pull {% data reusables.package_registry.container-registry-hostname %}/OWNER/IMAGE_NAME:latest
  > latest: Pulling from user/image-name
  > Digest: sha256:b3d3e366b55f9a54599220198b3db5da8f53592acbbb7dc7e4e9878762fc5344
  > Status: Downloaded newer image for {% data reusables.package_registry.container-registry-hostname %}/user/image-name:latest
  > {% data reusables.package_registry.container-registry-hostname %}/user/image-name:latest
  ```

## Crear imagenes de contenedor

En este ejemplo se compila la imagen `hello_docker`:
  ```shell
  $ docker build -t hello_docker .
  ```

## Etiquetar las imágenes de contenedor

1. Encuentra la ID para la imagen de Docker que quieres etiquetar.
  ```shell
  $ docker images
  > REPOSITORY                                            TAG                 IMAGE ID            CREATED             SIZE
  > {% data reusables.package_registry.container-registry-hostname %}/my-org/hello_docker         latest              38f737a91f39        47 hours ago        91.7MB
  > {% data reusables.package_registry.container-registry-hostname %}/my-username/hello_docker    latest              38f737a91f39        47 hours ago        91.7MB
  > hello-world                                           latest              fce289e99eb9        16 months ago       1.84kB
  ```

2. Etiqueta tu imagen de Docker utilizando la ID ed imagen y el nombre que quieras poner a la misma, así como el destino en donde se hospedará ésta.
  ```shell
  $ docker tag 38f737a91f39 {% data reusables.package_registry.container-registry-hostname %}/OWNER/NEW_IMAGE_NAME:latest
  ```
