---
ms.openlocfilehash: 24b88b3ba1b6cfe9fb9fb1f6398a6daeb57596a9
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756098"
---
### <a name="order-of-tags-in-activitytags-is-reversed"></a>Ordem das marcas na atividade. as marcas são revertidas

<xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> Agora armazena itens na lista de acordo com a ordem em que são adicionados, ou seja, o primeiro item que é adicionado é o primeiro na lista. Essa alteração foi feita para corresponder à [especificação de atributos OpenTelemetry](https://github.com/open-telemetry/opentelemetry-specification/blob/master/specification/common/common.md#attributes).

#### <a name="change-description"></a>Descrição das alterações

Nas versões anteriores do .NET, o <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> armazena itens na ordem inversa da qual eles são adicionados. Ou seja, o primeiro item adicionado é o último na lista. A partir do .NET 5,0, a ordem dos itens é revertida e o primeiro item adicionado sempre é o primeiro na lista.

#### <a name="version-introduced"></a>Versão introduzida

5,0

#### <a name="recommended-action"></a>Ação recomendada

Se seu aplicativo tiver uma dependência na <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> ordem da lista e você estiver atualizando para o .net 5,0 ou posterior, você precisará alterar esta parte do seu código.

#### <a name="category"></a>Categoria

Bibliotecas principais do .NET

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Diagnostics.Activity.Tags?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Activity.Tags`

-->
