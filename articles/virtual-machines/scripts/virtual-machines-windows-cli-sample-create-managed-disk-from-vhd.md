---
title: 同じサブスクリプションのストレージ アカウントに VHD ファイルからマネージド ディスクを作成する - CLI サンプル
description: Azure CLI サンプル スクリプト - 同じサブスクリプションのストレージ アカウントに VHD ファイルからマネージド ディスクを作成する
services: virtual-machines-windows
documentationcenter: storage
author: ramankumarlive
manager: kavithag
tags: azure-service-management
ms.assetid: ''
ms.service: virtual-machines-windows
ms.devlang: azurecli
ms.topic: sample
ms.tgt_pltfrm: vm-windows
ms.workload: infrastructure
ms.date: 05/19/2017
ms.author: ramankum
ms.custom: mvc
ms.openlocfilehash: b0ce935e03a6202ac444987cbecf853ee6717d3b
ms.sourcegitcommit: 58faa9fcbd62f3ac37ff0a65ab9357a01051a64f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2020
ms.locfileid: "81459524"
---
# <a name="create-a-managed-disk-from-a-vhd-file-in-a-storage-account-in-the-same-subscription-with-cli"></a>CLI で同じサブスクリプションのストレージ アカウントに VHD ファイルからマネージド ディスクを作成する

このスクリプトは、同じサブスクリプションのストレージ アカウントに VHD ファイルからマネージド ディスクを作成します。 sysprep された汎用的な VHD ではなく特殊化された VHD を OS の管理ディスクにインポートして仮想マシンを作成するには、このスクリプトを使います。 または、このスクリプトを使用して、データ VHD をマネージド データ ディスクにインポートします。

[!INCLUDE [sample-cli-install](../../../includes/sample-cli-install.md)]

[!INCLUDE [quickstarts-free-trial-note](../../../includes/quickstarts-free-trial-note.md)]

## <a name="sample-script"></a>サンプル スクリプト

[!code-azurecli[main](../../../cli_scripts/virtual-machine/create-managed-data-disks-from-vhd/create-managed-data-disks-from-vhd.sh "Create managed disk from VHD")]

## <a name="script-explanation"></a>スクリプトの説明

このスクリプトは、以下のコマンドを使って VHD からマネージド ディスクを作成します。 表内の各コマンドは、それぞれのドキュメントにリンクされています。

| command | メモ |
|---|---|
| [az disk create](https://docs.microsoft.com/cli/azure/disk) | 同じサブスクリプション内のストレージ アカウントに VHD の URI を使用してマネージド ディスクを作成する |

## <a name="next-steps"></a>次のステップ

Azure CLI の詳細については、[Azure CLI のドキュメント](https://docs.microsoft.com/cli/azure)のページをご覧ください。

その他の仮想マシンとマネージド ディスクの CLI サンプル スクリプトは、[Azure Windows VM のドキュメント](../windows/cli-samples.md?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json)にあります。
