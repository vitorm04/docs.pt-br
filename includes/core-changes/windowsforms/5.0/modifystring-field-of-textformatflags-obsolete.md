---
ms.openlocfilehash: 56127309c5f5993ffc2e2faedd1f481e8131e094
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400624"
---
### <a name="textformatflagsmodifystring-is-obsolete"></a>TextFormatFlags. Modifystring é obsoleto

O <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> campo é obsoleto, como um aviso, e pode ser removido em uma versão futura do .net.

#### <a name="change-description"></a>Descrição das alterações

Nas versões anteriores do .NET, o <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> campo de enumeração não está marcado como obsoleto. No .NET 5,0 e versões posteriores, ele é marcado como obsoleto como um aviso. Esse campo pode ser removido em uma versão futura do .NET.

#### <a name="reason-for-change"></a>Motivo da alteração

Passar uma cadeia de caracteres para <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> com <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> altera a cadeia de caracteres em algumas situações. Esse comportamento interrompe a promessa de imutabilidade da cadeia de caracteres e pode levar a uma corrupção fatal do estado do tempo de execução .NET.

#### <a name="version-introduced"></a>Versão introduzida

.NET 5,0 RC1

#### <a name="recommended-action"></a>Ação recomendada

Atualize qualquer código que dependa de <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> .

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=fullName>

<!--

#### Affected APIs

- `F:System.Windows.Forms.TextFormatFlags.ModifyString`

-->
