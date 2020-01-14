---
ms.openlocfilehash: e609b8006846cd202a6a7eeec2529cf1fbb09e7c
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937098"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a>APIs duplicadas removidas do Windows Forms

Várias APIs duplicadas acidentalmente no namespace <xref:System.Windows.Forms?displayProperty=fullName> a partir do .NET Core 3,0 Preview 4 foram removidas no .NET Core 3,0 RC1.

#### <a name="change-description"></a>Descrição das alterações

O .NET Core 3,0 Preview 4 duplicava inadvertidamente um número de tipos no namespace de <xref:System.Windows.Forms?displayProperty=fullName> que já existiam no namespace <xref:System.ComponentModel.Design?displayProperty=fullName>. A partir do .NET Core 3,0 RC1, esses tipos duplicados não estão mais disponíveis. A tabela a seguir mostra como lista o tipo original e seu tipo duplicado:

> [!div class="mx-tdCol2BreakAll"]
> |Tipo original|Tipo duplicado|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a>Versão introduzida

RC1 3,0

#### <a name="recommended-action"></a>Ação recomendada

Atualize o código para referenciar o tipo original, conforme mostrado na coluna **tipo original** da tabela.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

- Não detectável via análise de API.

<!--

### Affected APIs

- Not detectable via API analysis.

-->
