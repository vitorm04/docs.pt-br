---
title: Bancos de dados na memória
ms.date: 12/13/2019
description: Saiba como usar bancos de dados do SQLite na memória.
ms.openlocfilehash: b125ff5aa4128bd4c3ff558c5573b7d11802090a
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447240"
---
# <a name="in-memory-databases"></a>Bancos de dados na memória

Os bancos de dados na memória do SQLite são bancos de dados armazenados inteiramente na memória, não no disco. Use o nome de arquivo de fonte de dados especial `:memory:` para criar um banco de dado na memória. Quando a conexão é fechada, o banco de dados é excluído. Ao usar `:memory:`, cada conexão cria seu próprio banco de dados.

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>Bancos de dados compartilhados na memória

Os bancos de dados na memória podem ser compartilhados entre várias conexões usando `Mode=Memory` e `Cache=Shared` na cadeia de conexão. A palavra-chave `Data Source` é usada para fornecer um nome ao banco de dados na memória. As cadeias de conexão que usam o mesmo nome acessarão o mesmo banco de dados na memória. O banco de dados persiste, desde que pelo menos uma conexão permaneça aberta. Um [exemplo](https://github.com/dotnet/samples/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) que demonstra isso está disponível no github.

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
