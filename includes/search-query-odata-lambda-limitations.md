---
author: brjohnstmsft
ms.service: cognitive-search
ms.topic: include
ms.date: 06/13/2018
ms.author: brjohnst
ms.openlocfilehash: 998d0f1a84dc9cb2a07fb55286c1089787a263e1
ms.sourcegitcommit: 2ec4b3d0bad7dc0071400c2a2264399e4fe34897
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2020
ms.locfileid: "80272816"
---
| データ型 | `any` を含むラムダ式で許可されている機能 | `all` を含むラムダ式で許可されている機能 |
|---|---|---|
| `Collection(Edm.ComplexType)` | `search.ismatch` と `search.ismatchscoring` を除くすべて | 同じ |
| `Collection(Edm.String)` | `eq` または `search.in` での比較 <br/><br/> `or` でのサブ式の組み合わせ | `ne` または `not search.in()` での比較 <br/><br/> `and` でのサブ式の組み合わせ |
| `Collection(Edm.Boolean)` | `eq` または `ne` での比較 | 同じ |
| `Collection(Edm.GeographyPoint)` | `geo.distance` または `lt` での `le` の使用 <br/><br/> `geo.intersects` <br/><br/> `or` でのサブ式の組み合わせ | `geo.distance` または `gt` での `ge` の使用 <br/><br/> `not geo.intersects(...)` <br/><br/> `and` でのサブ式の組み合わせ |
| `Collection(Edm.DateTimeOffset)`、`Collection(Edm.Double)`、`Collection(Edm.Int32)`, `Collection(Edm.Int64)` | `eq`、`ne`、`lt`、`gt`、`le`、または `ge` を使用した比較 <br/><br/> `or` を使用した、比較と他のサブ式の組み合わせ <br/><br/> `ne` を使用した、`and` を除く比較と他のサブ式の組み合わせ <br/><br/> `and`選言標準形 (DNF)`or` での [ と ](https://en.wikipedia.org/wiki/Disjunctive_normal_form) の組み合わせを使用した式 | `eq`、`ne`、`lt`、`gt`、`le`、または `ge` を使用した比較 <br/><br/> `and` を使用した、比較と他のサブ式の組み合わせ <br/><br/> `eq` を使用した、`or` を除く比較と他のサブ式の組み合わせ <br/><br/> `and`連言標準形 (CNF)`or` での [ と ](https://en.wikipedia.org/wiki/Conjunctive_normal_form) の組み合わせを使用した式 |
