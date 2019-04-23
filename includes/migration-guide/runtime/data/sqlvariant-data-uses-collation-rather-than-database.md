---
ms.openlocfilehash: e7a5a95a5d13f3396d396ad0d74a19a0efa3a967
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235051"
---
### <a name="sqlvariant-data-uses-sqlvariant-collation-rather-than-database-collation"></a>Os dados do Sql_variant usam a ordenação sql_variant em vez da ordenação de banco de dados

|   |   |
|---|---|
|Detalhes|<code>sql_variant</code> Os dados usam a ordenação <code>sql_variant</code> em vez da ordenação de banco de dados.|
|Sugestão|Essa alteração aborda os possíveis dados corrompidos caso a ordenação do banco de dados seja diferente da ordenação <code>sql_variant</code>. Os aplicativos que dependem de dados corrompidos podem apresentar falhas.|
|Escopo|Transparente|
|Versão|4.5|
|Tipo|Tempo de execução|
