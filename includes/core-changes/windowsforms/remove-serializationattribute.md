---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217041"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a>SerializableAttribute removido de alguns tipos de Windows Forms

O <xref:System.SerializableAttribute> foi removido de algumas classes de Windows Forms que não têm cenários de serialização binária conhecidos.

#### <a name="change-description"></a>Alterar descrição

Os tipos a seguir são decorados com <xref:System.SerializableAttribute> o no .NET Framework, mas o atributo foi removido no .NET Core:

- `System.InvariantComparer`
- <xref:System.ComponentModel.Design.ExceptionCollection?displayProperty=nameWithType>
- <xref:System.ComponentModel.Design.Serialization.CodeDomSerializerException?displayProperty=nameWithType>
- `System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService.CodeDomSerializationStore`
- <xref:System.Drawing.Design.ToolboxItem?displayProperty=nameWithType>
- `System.Resources.ResXNullRef`
- `System.Resources.ResXDataNode`
- `System.Resources.ResXFileRef`
- <xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>
- `System.Windows.Forms.NativeMethods.MSOCRINFOSTRUCT`
- `System.Windows.Forms.NativeMethods.MSG`

Historicamente, esse mecanismo de serialização teve preocupações sérias em manutenção e segurança. Manter `SerializableAttribute` em tipos significa que esses tipos devem ser testados para alterações de serialização de versão para versão e alterações de serialização de estrutura para estrutura potencialmente. Isso dificulta a evolução desses tipos e pode ser dispendioso para manter. Esses tipos não têm nenhum cenário de serialização binária conhecido, o que minimiza o impacto da remoção do atributo.

Para obter mais informações, consulte [serialização binária](~/docs/standard/serialization/binary-serialization.md).

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 9

#### <a name="recommended-action"></a>Ação recomendada

Atualize qualquer código que possa depender desses tipos sendo marcados como serializáveis.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- Nenhum

<!--

### Affected APIs

- Not detectable via API analysis

-->
