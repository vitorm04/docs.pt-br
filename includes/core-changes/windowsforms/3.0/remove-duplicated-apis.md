---
ms.openlocfilehash: 0be59258df10aa13920551f011d68bc8efe20b93
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888094"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a>APIs duplicadas removidas dos formulários do Windows

Uma série de APIs acidentalmente <xref:System.Windows.Forms?displayProperty=fullName> duplicadas no namespace a partir do .NET Core 3.0 Preview 4 foram removidas no .NET Core 3.0 RC1.

#### <a name="change-description"></a>Descrição da alteração

.NET Core 3.0 Preview 4 inadvertidamente duplicava <xref:System.Windows.Forms?displayProperty=fullName> uma série de tipos <xref:System.ComponentModel.Design?displayProperty=fullName> no namespace que já existiam no namespace. A partir do .NET Core 3.0 RC1, esses tipos duplicados não estão mais disponíveis. A tabela a seguir mostra listas do tipo original e seu tipo duplicado:

> [!div class="mx-tdCol2BreakAll"]
> |Tipo original|Tipo duplicado|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a>Versão introduzida

3.0 RC1

#### <a name="recommended-action"></a>Ação recomendada

Atualize o código para fazer referência ao tipo original, conforme mostrado na coluna **de tipo Original** da tabela.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- Nenhum.

<!--

### Affected APIs

- Not detectable via API analysis.

-->
