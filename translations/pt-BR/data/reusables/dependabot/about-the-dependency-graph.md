---
ms.openlocfilehash: 8cf9b4b70c5295ad2c7178a586fd660e05a88076
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2022
ms.locfileid: "146458193"
---
O grafo de dependência é um resumo dos arquivos de manifesto e de bloqueio armazenados em um repositório{% ifversion dependency-submission-api %} e das dependências enviadas ao repositório usando a API Envio de dependência (beta){% endif %}. Para cada repositório, ele mostra{% ifversion fpt or ghec %}:

- As dependências, os ecossistemas e os pacotes do qual depende
- Dependentes, os repositórios e pacotes que dependem dele{% else %} dependências, isto é, os ecossistemas e pacotes de que ele depende. O {% data variables.product.product_name %} não calcula informações sobre dependentes, os repositórios e os pacotes que dependem de um repositório.{% endif %}
