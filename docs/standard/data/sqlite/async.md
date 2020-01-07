---
title: Limitações assíncronas
ms.date: 12/13/2019
description: Explica as limitações das APIs assíncronas e algumas alternativas que você pode usar em vez disso.
ms.openlocfilehash: 350237dc5c03023f60e9680e8b9c94aabb62606f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447079"
---
# <a name="async-limitations"></a>Limitações assíncronas

SQLite não dá suporte a e/s assíncrona. Os métodos Async ADO.NET serão executados de forma síncrona em Microsoft. Data. sqlite. Evite chamá-los.

Em vez disso, use o [log write-ahead](https://www.sqlite.org/wal.html) para melhorar o desempenho e a simultaneidade.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AsyncSample/Program.cs?name=snippet_WAL)]

> [!TIP]
> O registro em log write-ahead é habilitado por padrão em bancos de dados criados usando [Entity Framework Core](/ef/core/).
