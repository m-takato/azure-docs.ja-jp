---
title: (非推奨) Azure Kubernetes クラスターを CoScale を使用して監視する
description: Azure Container Service の Kubernetes クラスターを CoScale を使用して監視します
author: fryckbos
ms.service: container-service
ms.topic: conceptual
ms.date: 05/22/2017
ms.author: saudas
ms.custom: mvc
ms.openlocfilehash: f195a5c05c6c95dac898b2d471747952a3446d52
ms.sourcegitcommit: acb82fc770128234f2e9222939826e3ade3a2a28
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2020
ms.locfileid: "81681725"
---
# <a name="deprecated-monitor-an-azure-container-service-kubernetes-cluster-with-coscale"></a>(非推奨) Azure Container Service の Kubernetes クラスターを CoScale を使用して監視する

[!INCLUDE [ACS deprecation](../../../includes/container-service-kubernetes-deprecation.md)]

この記事では、Azure Container Service の Kubernetes クラスター内のすべてのノードとコンテナーを監視する [CoScale](https://web.archive.org/web/20180317071550/https://www.coscale.com/) エージェントのデプロイする方法を説明します。 この構成を行うには、CoScale のアカウントが必要です。 


## <a name="about-coscale"></a>CoScale について 

CoScale は、複数のオーケストレーション プラットフォームのすべてのコンテナーからメトリックとイベントを収集する監視プラットフォームです。 CoScale は、Kubernetes 環境のすべてを監視し、 積み重ねられているすべてのレイヤー (OS、Kubernetes、Docker、およびコンテナー内で実行されるアプリケーション) のグラフ化と分析を行います。 CoScale には、多様な監視ダッシュボードと、オペレーターと開発者がインフラストラクチャとアプリケーションの問題をすばやく検出できる異常検出機能が組み込まれています。

![CoScale UI](./media/container-service-kubernetes-coscale/coscale.png)

この記事に示すように、Kubernetes クラスターにエージェントをインストールして、CoScale を SaaS ソリューションとして実行できます。 データをオンサイトで維持する場合は、オンプレミス インストールで CoScale を使用することもできます。


## <a name="prerequisites"></a>前提条件

最初に [CoScale アカウントを作成する](https://web.archive.org/web/20170507123133/https://www.coscale.com/free-trial)必要があります

このチュートリアルでは、[Azure Container Service を使用して Kubernetes クラスターを作成](container-service-kubernetes-walkthrough.md)したことを想定します。

また、`az`Azure CLI と `kubectl` ツールをインストールしていることも想定しています。

`az` ツールがインストールされていることを確認するには、次を実行します。

```azurecli
az --version
```

`az` ツールをインストールしていないない場合、[ここ](/cli/azure/install-azure-cli)に手順が記載されています。

`kubectl` ツールがインストールされていることを確認するには、次を実行します。

```bash
kubectl version
```

`kubectl` をインストールしていない場合、次を実行できます。

```azurecli
az acs kubernetes install-cli
```

## <a name="installing-the-coscale-agent-with-a-daemonset"></a>DaemonSet を使用した CoScale エージェントのインストール
[DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/) は Kubernetes によって使用され、クラスターのホストごとに 1 つのコンテナーの 1 つのインスタンスを実行します。
この DaemonSet は、CoScale などの監視エージェントの実行に最適です。

CoScale にログインしたら、[エージェント ページ](https://developer.newrelic.com/)に移動し、DaemonSet エージェントを使用してクラスターに CoScale エージェントをインストールします。 CoScale UI によって、エージェントの作成とKubernetes クラスター全体の監視を開始するための構成手順が示されます。

![CoScale エージェントの構成](./media/container-service-kubernetes-coscale/installation.png)

クラスターでエージェントを起動するには、指定されたコマンドを実行します。

![CoScale エージェントを開始する](./media/container-service-kubernetes-coscale/agent_script.png)

これで完了です。 エージェントが実行されると、数分後にデータがコンソールに表示されます。 [エージェント ページ](https://developer.newrelic.com/)で、クラスターの概要を確認し、追加の構成手順を実行します。**Kubernetes クラスターの概要**などのダッシュボードが表示されます。

![Kubernetes クラスターの概要](./media/container-service-kubernetes-coscale/dashboard_clusteroverview.png)

CoScale エージェントは、クラスター内の新しいマシンに自動的にデプロイされます。 エージェントは、新しいバージョンがリリースされたときに自動的に更新されます。


## <a name="next-steps"></a>次のステップ

CoScale 監視ソリューションの詳細については、[CoScale のドキュメントと](https://web.archive.org/web/20180415164304/http://docs.coscale.com:80/)と[ブログ](https://web.archive.org/web/20170501021344/http://www.coscale.com:80/blog)を参照してください。 

