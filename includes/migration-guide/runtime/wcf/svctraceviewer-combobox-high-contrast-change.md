---
ms.openlocfilehash: 5a45d616001be5a2a2bdf2c654c10526125d7d86
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802667"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a>Alteração de alto contraste de ComboBox de svcTraceViewer

|   |   |
|---|---|
|Detalhes|Na [ferramenta Visualizador de Rastreamento de Serviço da Microsoft](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), os controles ComboBox não eram exibidos na cor correta em determinados temas de alto contraste. O problema foi corrigido no .NET Framework 4.7.2. No entanto, devido aos requisitos de compatibilidade com versões anteriores do SDK do .NET Framework, a correção não estava visível para clientes por padrão. O .NET 4.8 revela essa alteração adicionando os seguintes [comutadores de configuração do AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) ao arquivo svcTraceViewer.exe.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|Sugestão|<ul><li>Como recusar a alteração Se você não quiser ter a alteração de comportamento de alto contraste, poderá desabilitá-la removendo a seguinte seção do arquivo svcTraceViewer.exe.config:</li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.8|
|Tipo|Tempo de execução|

