---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643952"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a>SerializableAttribute removido de alguns tipos de formulários do Windows

O <xref:System.SerializableAttribute> foi removido de algumas classes do Windows Forms que não têm cenários de serialização binários conhecidos.

#### <a name="change-description"></a>Descrição da alteração

Os seguintes tipos são <xref:System.SerializableAttribute> decorados com o framework .NET, mas o atributo foi removido no .NET Core:

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

Historicamente, esse mecanismo de serialização tem tido sérias preocupações de manutenção e segurança. A `SerializableAttribute` manutenção dos tipos significa que esses tipos devem ser testados para alterações de serialização de versão a versão e alterações de serialização potencialmente de framework para framework. Isso torna mais difícil evoluir esses tipos e pode ser caro para manter. Esses tipos não têm cenários de serialização binários conhecidos, o que minimiza o impacto da remoção do atributo.

Para obter mais informações, consulte [Serialização binária](~/docs/standard/serialization/binary-serialization.md).

#### <a name="version-introduced"></a>Versão introduzida

3.0 Visualização 9

#### <a name="recommended-action"></a>Ação recomendada

Atualize qualquer código que possa depender que esses tipos sejam marcados como serializáveis.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- Nenhum

<!--

### Affected APIs

- Not detectable via API analysis

-->
