---
ms.openlocfilehash: f7c13688236f3d66f3225ecf5d93b4c3284e2e71
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002896"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. Constants. vbNewLine é obsoleto

A constante <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> é marcada como [obsoleta](xref:System.ObsoleteAttribute) a partir do .net Core 3,0 Preview 8.

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 8

#### <a name="details"></a>Detalhes

A partir do .NET Core 3,0 Preview 8, o atributo [obsoleto](xref:System.ObsoleteAttribute) foi aplicado à constante <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>. O uso da constante produz um aviso do compilador. Nas versões anteriores do .NET Core e .NET Framework, ela não estava marcada como obsoleta.

Essa alteração foi feita para dar suporte a Visual Basic como uma linguagem para o desenvolvimento de várias plataformas. A constante `vbNewLine` é equivalente a `\r\n`, a seqüência de caracteres de nova linha no Windows. Em sistemas baseados em UNIX, o caractere de nova linha é `\n`.
 
#### <a name="recommended-action"></a>Ação recomendada

A mensagem de atributo [obsoleto](xref:System.ObsoleteAttribute) para `vbNewLine` inclui a seguinte recomendação:

> Para um retorno de carro e alimentação de linha, use [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf). Para a nova linha da plataforma atual, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.

#### <a name="category"></a>Categoria

Visual Basic

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-- >

