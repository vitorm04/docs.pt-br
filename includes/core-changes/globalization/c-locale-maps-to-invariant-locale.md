---
ms.openlocfilehash: d35de48dd22003c851cf5dba9e8517ec48b9217b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198329"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a>A localidade "C" é mapeada para a localidade invariável

O .NET Core 2,2 e versões anteriores dependem do comportamento padrão do ICU, que mapeia a localidade "C" para a localidade en_US_POSIX. A localidade en_US_POSIX tem um comportamento de agrupamento indesejável, pois não oferece suporte a comparações de cadeias de caracteres que não diferenciam maiúsculas de minúscula Como algumas distribuições do Linux definem a localidade "C" como a localidade padrão, os usuários estão apresentando um comportamento inesperado.

#### <a name="change-description"></a>Alterar descrição

A partir do .NET Core 3,0, o mapeamento de localidade "C" foi alterado para usar a localidade invariável em vez de en_US_POSIX. A localidade "C" para mapeamento invariável também é aplicada ao Windows para fins de consistência.

O mapeamento de "C" para a cultura en_US_POSIX causou confusão do cliente, pois o en_US_POSIX não dá suporte a operações de cadeia de caracteres de classificação/pesquisa sem diferenciação Como a localidade "C" é usada como uma localidade padrão em alguns dos distribuições do Linux, os clientes tiveram esse comportamento indesejado nesses sistemas operacionais.

#### <a name="version-introduced"></a>Versão introduzida

3.0

### <a name="recommended-action"></a>Ação recomendada

Nada mais específico do que a conscientização dessa alteração. Essa alteração afeta apenas os aplicativos que usam o mapeamento de localidade "C".

### <a name="category"></a>Categoria

Globalização

### <a name="affected-apis"></a>APIs afetadas

Todas as APIs de agrupamento e cultura são afetadas por essa alteração.

<!--

-->
