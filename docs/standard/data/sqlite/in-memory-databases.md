---
title: Bancos de dados na memória
ms.date: 12/13/2019
description: Aprenda a usar bancos de dados SQLite na memória.
ms.openlocfilehash: 408c81f538e27dcfffad20db74b7809912b7905f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391202"
---
# <a name="in-memory-databases"></a>Bancos de dados na memória

Os bancos de dados de memória sqlite são bancos de dados armazenados inteiramente na memória, não em disco. Use o nome `:memory:` de arquivo de origem de dados especial para criar um banco de dados na memória. Quando a conexão é fechada, o banco de dados é excluído. Ao `:memory:`usar, cada conexão cria seu próprio banco de dados.

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>Bancos de dados de memória compartilháveis

Os bancos de dados na memória podem `Mode=Memory` ser `Cache=Shared` compartilhados entre várias conexões usando e na seqüência de conexões. A `Data Source` palavra-chave é usada para dar um nome ao banco de dados na memória. As seqüências de conexão usando o mesmo nome acessarão o mesmo banco de dados na memória. O banco de dados persiste enquanto pelo menos uma conexão com ele permanecer aberta. Uma [amostra](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) demonstrando isso está disponível no GitHub.

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
