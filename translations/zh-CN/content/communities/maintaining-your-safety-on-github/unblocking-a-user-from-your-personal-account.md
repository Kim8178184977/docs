---
title: 取消阻止用户对个人帐户的访问
intro: '如果您使用已阻止的 {% data variables.product.prodname_dotcom %} 用户修改了围栏，则可以取消阻止其帐户。'
redirect_from:
  - /articles/unblocking-a-user-from-your-personal-account
  - /github/building-a-strong-community/unblocking-a-user-from-your-personal-account
versions:
  fpt: '*'
  ghec: '*'
topics:
  - Community
shortTitle: Unblock from your account
ms.openlocfilehash: a88a8613a8d787ee7e42ea9f6f5ef994353aedc8
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2022
ms.locfileid: '145086572'
---
取消阻止用户后，他们将能够邀请您成为其仓库的协作者。 如果他们在 GitHub 中的任意位置 [@mention你](/articles/basic-writing-and-formatting-syntax/#mentioning-people-and-teams)，你将收到通知。

在您拥有的仓库中，用户将能够正常协作。

您可以在您的帐户设置中或从用户的个人资料页面中取消阻止用户。

## 在您的帐户设置中取消阻止用户

{% data reusables.user-settings.access_settings %} {% data reusables.user-settings.blocked_users %}
3. 在“已阻止的用户”下想要取消阻止的用户旁边，单击“取消阻止”。
![取消阻止用户按钮](/assets/images/help/organizations/org-unblock-user-button.png)

## 从用户的个人资料页面取消阻止该用户

{% data reusables.profile.user_profile_page_navigation %}
2. 在左侧边栏中，在用户头像下，单击 {% octicon "kebab-horizontal" aria-label="The horizontal kebab icon" %}，然后单击“取消阻止或举报用户”。
![“取消阻止或举报用户”链接](/assets/images/help/profile/profile-unblock-or-report-user.png)
3. 单击“取消阻止用户”。
  ![包含取消阻止用户或举报滥用选项的模态框](/assets/images/help/profile/profile-unblockuser.png)

{% tip %}

提示：阻止用户时删除的任何设置（例如协作者状态、星号和关注），取消阻止该用户后不会恢复。

{% endtip %}

## 延伸阅读

- “[阻止用户访问你的个人帐户](/communities/maintaining-your-safety-on-github/blocking-a-user-from-your-personal-account)”
- “[阻止用户访问组织](/communities/maintaining-your-safety-on-github/blocking-a-user-from-your-organization)”
- “[取消阻止用户对组织的访问](/communities/maintaining-your-safety-on-github/unblocking-a-user-from-your-organization)”
- “[举报滥用或垃圾邮件](/communities/maintaining-your-safety-on-github/reporting-abuse-or-spam)”
