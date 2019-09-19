---
ms.openlocfilehash: 9e9e443be9ea51d214e95c676fc28f0d8790af8b
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117179"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a>A localidade "C" é mapeada para a localidade invariável

O .NET Core 2,2 e versões anteriores dependem do comportamento padrão do ICU, que mapeia a localidade "C" para a localidade en_US_POSIX. A localidade en_US_POSIX tem um comportamento de agrupamento indesejável, pois não oferece suporte a comparações de cadeias de caracteres que não diferenciam maiúsculas de minúscula Como algumas distribuições do Linux definem a localidade "C" como a localidade padrão, os usuários estão apresentando um comportamento inesperado. 

#### <a name="details"></a>Detalhes

A partir do .NET Core 3,0, o mapeamento de localidade "C" foi alterado para usar a localidade invariável em vez de en_US_POSIX. A localidade "C" para mapeamento invariável também é aplicada ao Windows para fins de consistência.

O mapeamento de "C" para a cultura en_US_POSIX causou confusão do cliente, pois o en_US_POSIX não dá suporte a operações de cadeia de caracteres de classificação/pesquisa sem diferenciação Como a localidade "C" é usada como uma localidade padrão em alguns dos distribuições do Linux, os clientes tiveram esse comportamento indesejado nesses sistemas operacionais. 

#### <a name="version-introduced"></a>Versão introduzida

.NET Core 3.0

### <a name="recommended-action"></a>Ação recomendada

Nada mais específico do que a conscientização dessa alteração. Essa alteração afeta apenas os aplicativos que usam o mapeamento de localidade "C".

### <a name="category"></a>Categoria

Globalização 

### <a name="affected-apis"></a>APIs afetadas

Todas as APIs de agrupamento e cultura são afetadas por essa alteração.

<!--

-->
