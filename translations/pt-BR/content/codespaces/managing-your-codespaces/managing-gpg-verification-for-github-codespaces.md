---
title: Como gerenciar a verificação GPG para o GitHub Codespaces
intro: 'Você pode permitir que {% data variables.product.company_short %} use o GPG automaticamente para assinar os commits que você faz nos seus codespaces para que outras pessoas possam confiar que as alterações vêm de uma fonte de confiança.'
product: '{% data reusables.gated-features.codespaces %}'
versions:
  fpt: '*'
  ghec: '*'
type: how_to
topics:
  - Codespaces
  - Developer
  - Security
redirect_from:
  - /github/developing-online-with-codespaces/managing-gpg-verification-for-codespaces
  - /codespaces/working-with-your-codespace/managing-gpg-verification-for-codespaces
  - /codespaces/managing-your-codespaces/managing-gpg-verification-for-codespaces
shortTitle: GPG verification
ms.openlocfilehash: 368f5db095ea42e87cf2517ec56f3945ca528bd1
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2022
ms.locfileid: '147111429'
---
Depois que você habilitar a verificação do GPG, {% data variables.product.company_short %} assinará automaticamente os commits que você fizer em {% data variables.product.prodname_github_codespaces %}, e os commits terão um status de verificado em {% data variables.product.product_name %}. Por padrão, a verificação do GPG está desabilitada para os codespaces que você criar. Você pode optar por permitir a verificação do GPG para todos os repositórios ou repositórios específicos. Habilite apenas a verificação do GPG para repositórios nos quais você confia. Para obter mais informações sobre os commits assinados do {% data variables.product.product_name %}, confira "[Sobre a verificação de assinatura de commit](/github/authenticating-to-github/about-commit-signature-verification)".

Assim que você habilitar a verificação GPG, ela entrará em vigor para todos os seus codespaces.

{% data reusables.user-settings.access_settings %} {% data reusables.user-settings.codespaces-tab %}
1. Em "Verificação do GPG, selecione a configuração que deseja para verificação do GPG.
  ![Botões de opção usados para gerenciar a verificação de GPG](/assets/images/help/settings/codespaces-gpg-verification-radio-buttons.png) 
1. Se você escolheu "repositórios selecionados", selecione o menu suspenso e, em seguida, clique em um repositório para o qual deseja habilitar a verificação do GPG. Repita esse procedimento para todos os repositórios para os quais você deseja habilitar a verificação do GPG.
  ![Menu suspenso "Repositórios selecionados"](/assets/images/help/settings/codespaces-gpg-verification-repository-drop-down.png) 


{% note %}

**Observação:** depois de habilitar a verificação de GPG para o {% data variables.product.prodname_codespaces %}, você também precisa acrescentar `-S` a cada commit para que ele seja assinado. Para fazer isso em {% data variables.product.prodname_vscode %}, verifique se a opção "Git: Habilitar a assinatura do commit" está habilitada nas Configurações.

{% endnote %}
