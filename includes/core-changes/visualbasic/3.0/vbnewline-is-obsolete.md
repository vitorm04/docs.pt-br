---
ms.openlocfilehash: 95a4c807f5c1077cf52f54b196e904ebc98c32f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116368"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft.VisualBasic.Constants.vbNewLine é obsoleto

A <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constante é marcada como [ \[Obsoleta\] ](xref:System.ObsoleteAttribute) começando com .NET Core 3.0 Preview 8.

#### <a name="version-introduced"></a>Versão introduzida

3.0 Visualização 8

#### <a name="change-description"></a>Descrição da alteração

Começando com .NET Core 3.0 [Obsolete](xref:System.ObsoleteAttribute) Preview 8, o <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> atributo Obsolete foi aplicado à constante. O uso da constante produz um aviso compilador. No .NET Framework e nas versões anteriores do .NET Core, ele não foi marcado como obsoleto.

Essa mudança foi feita para apoiar o Visual Basic como uma linguagem para o desenvolvimento de várias plataformas. A <xref:Microsoft.VisualBasic.Constants.vbNewLine> constante é `\r\n`equivalente à seqüência de caracteres newline no Windows. Nos sistemas baseados em Unix, `\n`o caractere newline é .

#### <a name="recommended-action"></a>Ação recomendada

A mensagem <xref:Microsoft.VisualBasic.Constants.vbNewLine> de atributo [Obsoleto](xref:System.ObsoleteAttribute) para inclui a seguinte recomendação:

Para um retorno de carruagem <xref:Microsoft.VisualBasic.Constants.vbCrLf>e alimentação de linha, use . Para a nova linha da <xref:System.Environment.NewLine?displayProperty=nameWithType>plataforma atual, use .

#### <a name="category"></a>Categoria

Visual Basic

#### <a name="affected-apis"></a>APIs afetadas

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
