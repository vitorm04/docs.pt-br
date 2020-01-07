---
title: E/s de BLOB
ms.date: 12/13/2019
description: Saiba como usar O recurso de e/s de BLOB do SQLite.
ms.openlocfilehash: 0c133deacdc19684eca3a6724fb398dc01fda558
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447044"
---
# <a name="blob-io"></a>E/s de BLOB

Você pode reduzir o uso de memória durante a leitura e a gravação de objetos grandes transmitindo os dados para dentro e fora dele. Isso pode ser especialmente útil ao analisar ou transformar os dados.

Comece inserindo uma linha como normal. Use a função `zeroblob()` SQL para alocar espaço no banco de dados para manter o objeto grande. A função `last_insert_rowid()` fornece uma maneira conveniente de obter seu ROWID.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Insert)]

Depois de inserir a linha, abra um fluxo para gravar o objeto grande usando <xref:Microsoft.Data.Sqlite.SqliteBlob>.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Write)]

Para transmitir o objeto grande para fora do banco de dados, você deve selecionar o ROWID ou um de seus aliases, como mostrado aqui, além da coluna do objeto grande. Se você não selecionar o ROWID, todo o objeto será carregado na memória. O objeto retornado por `GetStream()` será uma `SqliteBlob` quando feito corretamente.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Read)]
