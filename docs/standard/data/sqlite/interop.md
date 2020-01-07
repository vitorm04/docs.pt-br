---
title: Interoperabilidade
ms.date: 12/13/2019
description: Saiba como interoperar com outras bibliotecas do SQLite.
ms.openlocfilehash: 486e2a8e00999b8ebe9c85a5fcc1539c514676d3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447233"
---
# <a name="interoperability"></a>Interoperabilidade

Microsoft. Data. sqlite usa SQLitePCLRaw para interagir com a biblioteca SQLite nativa. O SQLitePCLRaw fornece uma API .NET fina sobre a API do SQLite nativo. SqliteConnection e SqliteDataReader fornecem acesso aos objetos SQLitePCLRaw subjacentes, permitindo que você chame essas APIs diretamente.

O exemplo a seguir mostra como chamar `sqlite3_trace` para gravar instruções SQL executadas no console do:

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/InteropSample/Program.cs?name=snippet_Trace)]

E o exemplo a seguir mostra a chamada de `sqlite3_stmt_status` para ver quantas etapas de máquina virtual do SQLite uma instrução SQL compilou em:

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/InteropSample/Program.cs?name=snippet_StatementStatus)]

Os objetos SQLitePCLRaw até expõem um ponteiro para os objetos nativos, permitindo P/Invoke APIs adicionais do SQLite nativo.
