---
ms.openlocfilehash: 948c83f49b703194ccfe932e53751e0bb2dde37c
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760762"
---
### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a>A propriedade ContextMenuStrip.SourceControl contém um controle válido no caso de ToolStripMenuItems aninhados

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.7.1 e nas versões anteriores, a propriedade <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> retorna nulo incorretamente quando o usuário abre o menu de controles <xref:System.Windows.Forms.ToolStripMenuItem> aninhados. No .NET Framework 4.7.2 e posterior, a propriedade <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> é sempre definida como o controle do código-fonte real.|
|Sugestão|<strong>Como aceitar ou recusar essas alterações</strong>Para que um aplicativo se beneficie dessas alterações, ele precisará ser executado no .NET Framework 4.7.2 ou posterior. O aplicativo pode se beneficiar dessas alterações de uma das seguintes maneiras:<ul><li>Ser direcionado ao .NET Framework 4.7.2. Essa alteração é habilitada por padrão nos aplicativos do Windows Forms direcionados ao .NET Framework 4.7.2 ou posterior.</li><li>Ser direcionado ao .NET Framework 4.7.1 ou a uma versão anterior e recusar os comportamentos de acessibilidade herdados, adicionando a seguinte [Opção AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) à seção <code>&lt;runtime&gt;</code> do arquivo app.config e definindo-a como <code>false</code>, como mostra o exemplo a seguir.</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Os aplicativos direcionados ao .NET Framework 4.7.2 ou posterior que desejam preservar o comportamento de acessibilidade herdado podem aceitar o uso do controle do código-fonte herdado definindo explicitamente essa opção AppContext como <code>true</code>.|
|Escopo|Microsoft Edge|
|Versão|4.7.2|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType></li></ul>|

