---
ms.openlocfilehash: e609b8006846cd202a6a7eeec2529cf1fbb09e7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937098"
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

- Não detectável via análise de API.

<!--

### Affected APIs

- Not detectable via API analysis.

-->
