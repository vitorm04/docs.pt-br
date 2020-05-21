---
ms.openlocfilehash: 3dfacadb5127319d4ce27f367803637cfb1ed00f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721660"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a>APIs duplicadas removidas do Windows Forms

Várias APIs duplicadas acidentalmente no <xref:System.Windows.Forms?displayProperty=fullName> namespace a partir do .net core 3,0 Preview 4 foram removidas no .net core 3,0 RC1.

#### <a name="change-description"></a>Descrição da alteração

O .NET Core 3,0 Preview 4 duplicava inadvertidamente um número de tipos no <xref:System.Windows.Forms?displayProperty=fullName> namespace que já existia no <xref:System.ComponentModel.Design?displayProperty=fullName> namespace. A partir do .NET Core 3,0 RC1, esses tipos duplicados não estão mais disponíveis. A tabela a seguir mostra como lista o tipo original e seu tipo duplicado:

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

- Nenhum.

<!--

#### Affected APIs

- Not detectable via API analysis.

-->
