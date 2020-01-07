---
title: Separação em lotes
ms.date: 12/13/2019
description: Saiba como executar um lote de instruções SQL em um único comando.
ms.openlocfilehash: 0799784471520bb279db6a4b5879ad30945bdebb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447051"
---
# <a name="batching"></a>Separação em lotes

O SQLite não dá suporte nativo a instruções SQL em lote em um único comando. Mas, como não há nenhuma rede envolvida, isso realmente ajudaria o desempenho mesmo assim. O Microsoft. Data. sqlite, no entanto, implementa o envio em lote de instruções como uma conveniência para fazê-lo se comportar mais como outros provedores de ADO.NET.

Ao chamar <xref:System.Data.Common.DbCommand.ExecuteReader%2A?displayProperty=nameWithType>, as instruções são executadas até a primeira que retorna os resultados. Chamar <xref:System.Data.Common.DbDataReader.NextResult%2A?displayProperty=nameWithType> continua executando instruções até o próximo que retorna resultados ou até atingir o final do lote. Chamar <xref:System.Data.Common.DbDataReader.Dispose%2A?displayProperty=nameWithType> ou <xref:System.Data.Common.DbDataReader.Close%2A> executa quaisquer instruções restantes que não tenham sido consumidas pelo `NextResult()`. Se você não descartar um leitor de dados, o finalizador tentará executar as instruções restantes, mas os erros encontrados serão ignorados. Por isso, é importante descartar `DbDataReader` objetos ao usar lotes.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BatchingSample/Program.cs?name=snippet_Batching)]

## <a name="see-also"></a>Veja também

* [Inserção em massa](bulk-insert.md)
