---
title: Gerenciando configurações de revisão de código para sua equipe
intro: Você pode diminuir o ruído para sua equipe limitando notificações quando se solicita que a sua equipe revise um pull request.
redirect_from:
  - /github/setting-up-and-managing-organizations-and-teams/managing-code-review-assignment-for-your-team
  - /organizations/organizing-members-into-teams/managing-code-review-assignment-for-your-team
product: '{% data reusables.gated-features.code-review-assignment %}'
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
  - Organizations
  - Teams
shortTitle: Code review settings
permissions: Team maintainers and organization owners can configure code review settings.
ms.openlocfilehash: 701ebf6a2306a8c8a734905d752c4b44c225ace6
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2022
ms.locfileid: '146180164'
---
## Sobre as configurações de revisão de código

{% ifversion only-notify-requested-members %} Para reduzir a quantidade de informações desnecessárias para sua equipe e esclarecer a responsabilidade individual pelas revisões de solicitação de pull, defina configurações de revisão de código.

- Notificações da equipe
- Atribuição automática

## Sobre as notificações da equipe

Ao optar por notificar apenas os integrantes da equipe solicitados, você não pode desabilitar o envio de notificações para toda a equipe quando se solicita que a equipe revise um pull request se for solicitado que um integrante específico dessa equipe também faça a revisão. Isso é especialmente útil quando um repositório é configurado com equipes como proprietários de códigos, mas os contribuidores do repositório geralmente conhecem um indivíduo específico que seria o revisor correto para o seu pull request. Para obter mais informações, confira "[Sobre os proprietários de código](/github/creating-cloning-and-archiving-repositories/about-code-owners)".

## Sobre atribuição automática
{% endif %}

Ao habilitar a atribuição automática, qualquer momento em que for solicitado que a sua equipe revise um pull request, ela será removida como revisor e um subconjunto específico de integrantes da equipe será atribuído no lugar da equipe. As atribuições de revisão de código permitem que você decida se toda a equipe ou apenas um subconjunto dos seus integrantes serão notificados quando for solicitado que uma equipe faça a revisão.

Quando se solicita que os proprietários do código façam a revisão automaticamente, a equipe ainda será removida e substituída por indivíduos, a menos que uma regra de proteção de branch esteja configurada que exija revisão dos proprietários de código. Se essa regra de proteção de ramificação estiver em vigor, a solicitação de equipe não poderá ser removida, fazendo com que a solicitação individual seja exibida.

### Encaminhar algoritmos

Escolha as atribuições de revisão de código e atribua os revisores automaticamente com base em um dos dois algoritmos possíveis. 

O algoritmo round robin (rotativo) escolhe os revisores com base em quem recebeu a solicitação de revisão menos recente e tem o foco em alternar entre todos os integrantes da equipe, independentemente do número de avaliações pendentes que possuem atualmente. 

O algoritmo do balanço de carga escolhe os revisores com base no número total de solicitações de revisão recentes de cada integrante e considera o número de revisões pendentes para cada integrante. O algoritmo do balanço de carga tenta garantir que cada integrante da equipe revise um número igual de pull requests em qualquer período de 30 dias.

Todos os integrantes da equipe que definiram seu status como "Ocupado" não serão selecionados para revisão. Se todos os integrantes da equipe estiverem ocupados, o pull request permanecerá atribuído à própria equipe. Para obter mais informações sobre os status do usuário, confira "[Como configurar um status](/account-and-profile/setting-up-and-managing-your-github-profile/customizing-your-profile/personalizing-your-profile#setting-a-status)".

{% ifversion only-notify-requested-members %}
## Configurando notificações da equipe

{% data reusables.profile.access_org %} {% data reusables.user-settings.access_org %} {% data reusables.organizations.specific_team %} {% data reusables.organizations.team_settings %} {% ifversion fpt or ghec or ghes > 3.4 or ghae-issue-5658 %}
1. Na barra lateral esquerda, clique em **{% octicon "code-review" aria-label="The code-review icon" %} Revisão de código**.
{% else %}
1. Na barra lateral esquerda, clique em **Revisão de código**
![botão Revisão de código](/assets/images/help/teams/review-button.png) {% endif %}
1. Selecione **Somente notificar os membros da equipe solicitados.** 
![ Notificações da equipe de revisão de código](/assets/images/help/teams/review-assignment-notifications.png)
1. Clique em **Salvar alterações**.
{% endif %}

## Configurando atribuição automática
{% data reusables.profile.access_org %} {% data reusables.user-settings.access_org %} {% data reusables.organizations.specific_team %} {% data reusables.organizations.team_settings %} {% ifversion fpt or ghec or ghes > 3.4 or ghae-issue-5658 %}
1. Na barra lateral esquerda, clique em **{% octicon "code-review" aria-label="The code-review icon" %} Revisão de código**.
{% else %}
1. Na barra lateral esquerda, clique em **Revisão de código**
![botão Revisão de código](/assets/images/help/teams/review-button.png) {% endif %}
1. Selecione **Habilitar atribuição automática**.
![Botão de atribuição automática](/assets/images/help/teams/review-assignment-enable.png)
1. Em "Quantos membros da equipe devem ser atribuídos para a revisão?, use o menu suspenso e escolha um número de revisores a serem atribuídos a cada pull request.
![Menu suspenso do número de revisores](/assets/images/help/teams/review-assignment-number.png)
1. Em "Algoritmo de encaminhamento", use o menu suspenso e escolha qual algoritmo você gostaria de usar. Para obter mais informações, confira "[Algoritmos de roteamento](#routing-algorithms)".
![Menu suspenso Algoritmos de roteamento](/assets/images/help/teams/review-assignment-algorithm.png)
1. Opcionalmente, para sempre ignorar determinados membros da equipe, selecione **Nunca atribuir determinados membros da equipe**. Em seguida, selecione um ou mais integrantes da equipe que você gostaria de ignorar sempre.
![Caixa de seleção e menu suspenso Nunca atribuir determinados membros da equipe](/assets/images/help/teams/review-assignment-skip-members.png) {% ifversion ghes < 3.4 %}
1. Opcionalmente, para notificar apenas os membros da equipe escolhidos pela atribuição de revisão de código para cada solicitação de revisão de pull, em "Notificações" selecione **Se os membros da equipe forem atribuídos, não notificar toda a equipe.**
{%- endif %} {% ifversion fpt or ghec or ghae-issue-5108 or ghes > 3.2 %}
1. Opcionalmente, para incluir os membros de equipes filho como potenciais revisores ao atribuir solicitações, selecione **Membros da equipe filho**.
1. Opcionalmente, para contar todos os membros cuja revisão já foi solicitada em relação ao número total de membros a serem atribuídos, selecione **Contar solicitações existentes**.
1. Opcionalmente, para remover a solicitação de revisão da equipe ao atribuir membros da equipe, selecione **Solicitação de revisão de equipe**.
{%- endif %}
1. Clique em **Salvar alterações**.

## Desabilitando a atribuição automática
{% data reusables.profile.access_org %} {% data reusables.user-settings.access_org %} {% data reusables.organizations.specific_team %} {% data reusables.organizations.team_settings %}
1. Selecione **Habilitar atribuição automática** para remover a marca de seleção.
![Botão de atribuição de revisão de código](/assets/images/help/teams/review-assignment-enable.png)
1. Clique em **Salvar alterações**.
