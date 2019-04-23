---
ms.openlocfilehash: e6c93a1bc31c041f36fca3704bca32012a2b42ac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803175"
---
### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a>Evento SelectionChanged e propriedade SelectedValue do seletor

|   |   |
|---|---|
|Detalhes|Começando com o .NET Framework 4.7.1, um <xref:System.Windows.Controls.Primitives.Selector> sempre atualiza o valor de sua propriedade <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> antes de acionar o evento <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>, quando sua seleção é alterada. Isso torna a propriedade SelectedValue consistente com as outras propriedades de seleção (<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> e <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>), que são atualizadas antes que o evento seja acionado.<p/>No .NET Framework 4.7 e nas versões anteriores, a atualização de SelectedValue ocorria antes do evento na maioria dos casos, mas ocorria depois do evento quando a alteração da seleção era causada pela alteração da propriedade <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>.|
|Sugestão|Aplicativos destinados ao .NET Framework 4.7.1 ou posteriores podem recusar essa alteração e usar o comportamento herdado adicionando o seguinte à seção <code>&lt;runtime&gt;</code> do arquivo de configuração de aplicativo:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Aplicativos destinados ao .NET Framework 4.7 ou anteriores, mas que são executados no .NET Framework 4.7.1 ou posteriores podem habilitar o novo comportamento adicionando a seguinte linha à seção <code>&lt;runtime&gt;</code> do arquivo de configuração de aplicativo:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Versão|4.7.1|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType></li></ul>|
