---
ms.openlocfilehash: d35de48dd22003c851cf5dba9e8517ec48b9217b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567778"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a>Mapas locais "C" para o local invariante

O .NET Core 2.2 e as versões anteriores dependem do comportamento padrão da UTI, que mapeia o local "C" para o local en_US_POSIX. O local en_US_POSIX tem um comportamento de colagem indesejável, porque não suporta comparações de seqüências insensíveis a casos. Como algumas distribuições Linux definiram o local "C" como o local padrão, os usuários estavam experimentando um comportamento inesperado.

#### <a name="change-description"></a>Descrição da alteração

Começando com o .NET Core 3.0, o mapeamento local "C" foi alterado para usar o local Invariant em vez de en_US_POSIX. O mapeamento "C" para Invariant também é aplicado ao Windows para obter consistência.

O mapeamento de "C" para en_US_POSIX cultura causou confusão no cliente, porque en_US_POSIX não suporta operações de cadeias de classificação/pesquisa insensíveis. Como o local "C" é usado como local padrão em algumas das distros do Linux, os clientes experimentaram esse comportamento indesejado nesses sistemas operacionais.

#### <a name="version-introduced"></a>Versão introduzida

3.0

### <a name="recommended-action"></a>Ação recomendada

Nada específico mais do que a consciência desta mudança. Essa alteração afeta apenas os aplicativos que usam o mapeamento local "C".

### <a name="category"></a>Categoria

Globalização

### <a name="affected-apis"></a>APIs afetadas

Todas as APIs de colagem e cultura são afetadas por essa mudança.

<!--

-->
