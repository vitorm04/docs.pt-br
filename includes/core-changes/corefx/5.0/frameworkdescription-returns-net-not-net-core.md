---
ms.openlocfilehash: 80d13609f1b02ae0ac875b2028e745670bb8f503
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050554"
---
### <a name="frameworkdescriptions-value-is-net-instead-of-net-core"></a>O valor de FrameworkDescription é .NET, em vez de .NET Core

<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> agora retorna ".NET" em vez de ".NET Core".

#### <a name="change-description"></a>Descrição das alterações

Nas versões anteriores do .NET, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> retorna ".NET Core" como parte da cadeia de caracteres de descrição, por exemplo, `.NET Core 3.1.1` .

A partir do .NET 5,0, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> retorna ".net" como parte da cadeia de caracteres de descrição, por exemplo, `.NET 5.0.0` .

#### <a name="reason-for-change"></a>Motivo da alteração

Com o .NET 5, `netcoreapp` é substituído pelo `net` como o moniker de estrutura de destino curto. Para consistência, a descrição da estrutura também foi atualizada. A alteração é superficial, pois a `FrameworkName` não é codificada em nenhum outro lugar do que na <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> propriedade.

#### <a name="version-introduced"></a>Versão introduzida

5.0

#### <a name="recommended-action"></a>Ação recomendada

Atualize qualquer código que pesquise ".NET Core" na cadeia de caracteres retornada por <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription> .

#### <a name="category"></a>Categoria

Bibliotecas principais do .NET

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
