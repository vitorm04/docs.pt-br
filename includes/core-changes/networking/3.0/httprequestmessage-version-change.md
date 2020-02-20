---
ms.openlocfilehash: 5ad9c494fd02059e05cc744aad3b06cfc9399995
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451870"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>Valor padrão de HttpRequestMessage. Version alterado para 1,1

O valor padrão da propriedade <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> foi alterado de 2,0 para 1,1.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="change-description"></a>Alterar descrição

No .NET Core 1,0 até 2,0, o valor padrão da propriedade <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> é 1,1. A partir do .NET Core 2,1, ele foi alterado para 2,1.

A partir do .NET Core 3,0, o número de versão padrão retornado pela propriedade <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> é mais uma vez 1,1.

#### <a name="recommended-action"></a>Ação recomendada

Atualize seu código se ele depender da propriedade <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> retornando um valor padrão de 2,0.

#### <a name="category"></a>Categoria

Rede

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-->
