---
ms.openlocfilehash: 8b0617d8f021a9534289fd7ae8539cd054684862
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774283"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a>O TextBox.Text do WPF pode estar fora de sincronia com a associação de dados

|   |   |
|---|---|
|Detalhes|Em alguns casos, a propriedade <xref:System.Windows.Controls.TextBox.Text> reflete um valor anterior do valor da propriedade vinculada se a propriedade é modificada durante uma operação de escrita de vinculação de dados.|
|Sugestão|Isso não deve ter nenhum impacto negativo. No entanto, é possível restaurar o comportamento anterior ao definir a propriedade <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> como <code>false</code>.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|
