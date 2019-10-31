---
ms.openlocfilehash: ff156afb3da4b921517fd841c5de2295265a8d7b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198326"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>Valor padrão de HttpRequestMessage. Version alterado para 1,1

O valor padrão da propriedade <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> foi alterado de 2,0 para 1,1.

#### <a name="version-introduced"></a>Versão introduzida

.NET Core 3.0

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
a def
### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-- >

