---
ms.openlocfilehash: 95a4c807f5c1077cf52f54b196e904ebc98c32f8
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116368"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. Constants. vbNewLine é obsoleto

A constante <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> é marcada como [\[obsoleta\]](xref:System.ObsoleteAttribute) a partir do .net Core 3,0 Preview 8.

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 8

#### <a name="change-description"></a>Descrição das alterações

A partir do .NET Core 3,0 Preview 8, o atributo [obsoleto](xref:System.ObsoleteAttribute) foi aplicado à constante <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>. O uso da constante produz um aviso do compilador. Em .NET Framework e versões anteriores do .NET Core, ele não foi marcado como obsoleto.

Essa alteração foi feita para dar suporte a Visual Basic como uma linguagem para o desenvolvimento de várias plataformas. A constante <xref:Microsoft.VisualBasic.Constants.vbNewLine> é equivalente a `\r\n`, a seqüência de caracteres de nova linha no Windows. Em sistemas baseados em UNIX, o caractere de nova linha é `\n`.

#### <a name="recommended-action"></a>Ação recomendada

A mensagem de atributo [obsoleto](xref:System.ObsoleteAttribute) para o <xref:Microsoft.VisualBasic.Constants.vbNewLine> inclui a seguinte recomendação:

Para um retorno de carro e alimentação de linha, use <xref:Microsoft.VisualBasic.Constants.vbCrLf>. Para a nova linha da plataforma atual, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.

#### <a name="category"></a>Categoria

Visual Basic

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
