---
ms.openlocfilehash: 4d67da34cf692133df95480a7f0215943337a34e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003014"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a>APIs duplicadas removidas do Windows Forms

Várias APIs duplicadas acidentalmente no namespace <xref:System.Windows.Forms?displayProperty=fullName> a partir do .NET Core 3,0 Preview 4 foram removidas no .NET Core 3,0 RC1. 

#### <a name="change-description"></a>Alterar descrição

O .NET Core 3,0 Preview 4 duplicava inadvertidamente um número de tipos no namespace <xref:System.Windows.Forms?displayProperty=fullName> que já existiam no namespace <xref:System.ComponentModel.Design?displayProperty=fullName>. A partir do .NET Core 3,0 RC1, esses tipos duplicados não estão mais disponíveis. A tabela a seguir mostra como lista o tipo original e seu tipo duplicado:

|Tipo original|Tipo duplicado|
|---|---|
|<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
|<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
|<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
|<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
|<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

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
