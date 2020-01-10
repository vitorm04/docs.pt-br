---
title: Bancos de dados na memória
ms.date: 12/13/2019
description: Saiba como usar bancos de dados do SQLite na memória.
ms.openlocfilehash: 16a9b6536fbfede203c24b757e96e28e7c49dc05
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777407"
---
# <a name="in-memory-databases"></a>Bancos de dados na memória

Os bancos de dados na memória do SQLite são bancos de dados armazenados inteiramente na memória, não no disco. Use o nome de arquivo de fonte de dados especial `:memory:` para criar um banco de dado na memória. Quando a conexão é fechada, o banco de dados é excluído. Ao usar `:memory:`, cada conexão cria seu próprio banco de dados.

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>Bancos de dados compartilhados na memória

Os bancos de dados na memória podem ser compartilhados entre várias conexões usando `Mode=Memory` e `Cache=Shared` na cadeia de conexão. A palavra-chave `Data Source` é usada para fornecer um nome ao banco de dados na memória. As cadeias de conexão que usam o mesmo nome acessarão o mesmo banco de dados na memória. O banco de dados persiste, desde que pelo menos uma conexão permaneça aberta. Um [exemplo](https://github.com/dotnet/samples/blob/master/snippets/standard/data/sqlite/InMemorySample/Program.cs) que demonstra isso está disponível no github.

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
