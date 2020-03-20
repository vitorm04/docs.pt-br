---
ms.openlocfilehash: f814703e187726d3988787fac52e5049988fd4d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803502"
---
### <a name="workflow-xaml-checksums-for-symbols-changed-from-sha1-to-sha256"></a>As somas de verificação XAML do Fluxo de Trabalho para símbolos mudaram de SHA1 para SHA256

|   |   |
|---|---|
|Detalhes|Para compatibilidade com a depuração com o Visual Studio, o runtime de fluxo de trabalho gera uma soma de verificação para um arquivo XAML do fluxo de trabalho usando um algoritmo de hash. No .NET Framework 4.6.2 e versões anteriores, o hash de soma de verificação do fluxo de trabalho usava o algoritmo MD5, o que causou problemas em sistemas habilitados para FIPS. Começando com o .NET Framework 4.7, o algoritmo padrão mudou para SHA1. Começando com o .NET Framework 4.8, o algoritmo padrão mudou para SHA256.|
|Sugestão|Se seu código não conseguir carregar instâncias do fluxo de trabalho ou encontrar símbolos adequados devido a uma falha na soma de verificação, tente definir o comutador <code>AppContext</code>&quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols&quot; como true.No código:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols&quot;, true);&#13;&#10;</code></pre>Ou em nossa configuração:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseSHA1HashForDebuggerSymbols=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Escopo|Secundária|
|Versão|4.8|
|Type|Redirecionando|
