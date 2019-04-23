---
ms.openlocfilehash: f5d93d76ab3409d4d4c1870cfef94cac59f9475c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773986"
---
### <a name="privatefontcollectionaddfontfile-method-releases-font-resources"></a>O método PrivateFontCollection.AddFontFile libera os recursos de fonte

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.7.1 e nas versões anteriores, a classe <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> não libera os recursos de fonte GDI+ depois que a <xref:System.Drawing.Text.PrivateFontCollection> é descartada para os objetos <xref:System.Drawing.Font> que são adicionados a essa coleção usando o método <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)>. No .NET Framework 4.7.2 e posterior <xref:System.Drawing.Text.FontCollection.Dispose%2A> libera as fontes GDI+ que foram adicionadas à coleção como arquivos.|
|Sugestão|<strong>Como aceitar ou recusar essas alterações</strong>Para que um aplicativo se beneficie dessas alterações, ele precisará ser executado no .NET Framework 4.7.2 ou posterior. O aplicativo pode se beneficiar dessas alterações de uma das seguintes maneiras:<ul><li>Ser recompilado para ser direcionado ao .NET Framework 4.7.2. Essa alteração é habilitada por padrão nos aplicativos do Windows Forms direcionados ao .NET Framework 4.7.2 ou posterior.</li><li>Ser direcionado ao .NET Framework 4.7.1 ou a uma versão anterior e recusar os comportamentos de acessibilidade herdados, adicionando a seguinte [Opção AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) à seção <code>&lt;runtime&gt;</code> do arquivo app.config e definindo-a como <code>false</code>, como mostra o exemplo a seguir.</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Drawing.Text.DoNotRemoveGdiFontsResourcesFromFontCollection=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Os aplicativos direcionados ao .NET Framework 4.7.2 ou posterior que desejam preservar o comportamento herdado podem aceitar não liberar os recursos de fonte definindo explicitamente essa opção AppContext como <code>true</code>.|
|Escopo|Microsoft Edge|
|Versão|4.7.2|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType></li><li><xref:System.Drawing.Text.FontCollection.Dispose?displayProperty=nameWithType></li></ul>|
