---
ms.openlocfilehash: e73fe48467ede501bae0ddd9362d9d55b3ca998b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59233914"
---
### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a>As ações de upbutton e downbutton de domínio do WinForm agora estão sincronizadas

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.7.1 e nas versões anteriores, a ação <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> do controle <xref:System.Windows.Forms.DomainUpDown> é ignorada quando o texto do controle está presente e o desenvolvedor precisa usar a ação <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> no controle antes de usar a ação <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>. Começando com o .NET Framework 4.7.2, as ações <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> e <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> funcionam de forma independente neste cenário e permanecem em sincronização.|
|Sugestão|Para que o aplicativo se beneficie dessas alterações, ele deverá ser executado no .NET Framework 4.7.2 ou posterior. O aplicativo pode se beneficiar dessas alterações de uma das seguintes maneiras:<ul><li>Ser recompilado para ser direcionado ao .NET Framework 4.7.2. Essa alteração é habilitada por padrão nos aplicativos do Windows Forms direcionados ao .NET Framework 4.7.2 ou posterior.</li><li>Recusar o comportamento de rolagem herdado adicionando a seguinte [Opção de AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) à seção <code>&lt;runtime&gt;</code> do arquivo de configuração de aplicativo e configurando-a como <code>false</code>, como mostra o exemplo a seguir.</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.7.2|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType></li><li><xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType></li></ul>|
