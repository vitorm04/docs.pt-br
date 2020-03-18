---
ms.openlocfilehash: 5ad9c494fd02059e05cc744aad3b06cfc9399995
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451870"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>Valor padrão de HttpRequestMessage.Version alterado para 1.1

O valor padrão <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> da propriedade passou de 2,0 para 1,1.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="change-description"></a>Descrição da alteração

No .NET Core 1.0 a 2.0, <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> o valor padrão da propriedade é de 1,1. A partir do .NET Core 2.1, foi alterado para 2.1.

Começando com .NET Core 3.0, o número <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> da versão padrão retornado pela propriedade é novamente 1.1.

#### <a name="recommended-action"></a>Ação recomendada

Atualize seu código se <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> depender da propriedade que retornar um valor padrão de 2.0.

#### <a name="category"></a>Categoria

Rede

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-->
