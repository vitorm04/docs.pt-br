---
title: Inserção em massa
ms.date: 12/13/2019
description: Dicas de desempenho que você pode usar ao fazer inúmeras alterações no banco de dados.
ms.openlocfilehash: 9d87d5c8d70f8e70479f9aa02b7802f73b88de9e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447037"
---
# <a name="bulk-insert"></a>Inserção em massa

O SQLite não tem nenhuma maneira especial para inserir dados em massa. Para obter o desempenho ideal ao inserir ou atualizar dados, certifique-se de fazer o seguinte:

- Use uma transação.
- Reutilize o mesmo comando com parâmetros. As execuções subsequentes reutilizarão a compilação da primeira.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BulkInsertSample/Program.cs?name=snippet_BulkInsert)]
