---
ms.openlocfilehash: cc6d96bd614ff015ae2125c0f1477e18a91a68f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802667"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a>Alteração de alto contraste de ComboBox de svcTraceViewer

|   |   |
|---|---|
|Detalhes|Na [ferramenta Visualizador de Rastreamento de Serviço da Microsoft](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), os controles ComboBox não eram exibidos na cor correta em determinados temas de alto contraste. O problema foi corrigido no .NET Framework 4.7.2. No entanto, devido aos requisitos de compatibilidade com versões anteriores do SDK do .NET Framework, a correção não estava visível para clientes por padrão. O .NET 4.8 revela essa alteração adicionando os seguintes [comutadores de configuração do AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) ao arquivo svcTraceViewer.exe.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|Sugestão|<ul><li>Como recusar a alteração Se você não quiser ter a alteração de comportamento de alto contraste, poderá desabilitá-la removendo a seguinte seção do arquivo svcTraceViewer.exe.config:</li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.8|
|Type|Runtime|
