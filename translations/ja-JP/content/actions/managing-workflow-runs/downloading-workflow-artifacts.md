---
title: ワークフローの成果物をダウンロードする
intro: アーカイブされた成果物は、自動的に有効期限切れになる前にダウンロードできます。
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
shortTitle: Download workflow artifacts
ms.openlocfilehash: 71e00a13769b696b47864d53d702770fb4f2b47a
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2022
ms.locfileid: '145117189'
---
{% data reusables.actions.enterprise-beta %} {% data reusables.actions.enterprise-github-hosted-runners %}

既定では、{% data variables.product.product_name %} にはビルド ログと成果物が 90 日間保存され、リポジトリの種類に応じてこの保持期間をカスタマイズできます。 詳細については、「[リポジトリの {% data variables.product.prodname_actions %} 設定の管理](/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#configuring-the-retention-period-for-github-actions-artifacts-and-logs-in-your-repository)」を参照してください。

{% data reusables.repositories.permissions-statement-read %}

{% webui %}

{% data reusables.repositories.navigate-to-repo %} {% data reusables.repositories.actions-tab %} {% data reusables.repositories.navigate-to-workflow %} {% data reusables.repositories.view-run %}
1. **[Artifacts]\(成果物\)** で、ダウンロードする成果物をクリックします。
    
    ![成果物のダウンロードのドロップダウンメニュー](/assets/images/help/repository/artifact-drop-down-updated.png)
    

{% endwebui %}

{% cli %}

{% data reusables.cli.cli-learn-more %}

{% data variables.product.prodname_cli %} は、成果物の名前に基づいて各成果物を個別のディレクトリにダウンロードします。 成果物が 1 つだけ指定されている場合は、現在のディレクトリに抽出されます。

ワークフローの実行によって生成されたすべての成果物をダウンロードするには、`run download` サブコマンドを使用します。 `run-id` を、成果物のダウンロード元の実行の ID に置き換えます。 `run-id` を指定しない場合、{% data variables.product.prodname_cli %} は、最近の実行を選択するためのインタラクティブ メニューを返します。

```shell
gh run download <em>run-id</em>
```

実行から特定の成果物をダウンロードするには、`run download` サブコマンドを使用します。 `run-id` を、成果物のダウンロード元の実行の ID に置き換えます。 `artifact-name` を、ダウンロードする成果物の名前に置き換えます。

```shell
gh run download <em>run-id</em> -n <em>artifact-name</em>
```

複数の成果物を指定できます。

```shell
gh run download <em>run-id</em> -n <em>artifact-name-1</em> -n <em>artifact-name-2</em>
```

リポジトリ内のすべての実行に対して特定の成果物をダウンロードするには、`run download` サブコマンドを使用します。

```shell
gh run download -n <em>artifact-name-1</em> -n <em>artifact-name-2</em>
```

{% endcli %}
