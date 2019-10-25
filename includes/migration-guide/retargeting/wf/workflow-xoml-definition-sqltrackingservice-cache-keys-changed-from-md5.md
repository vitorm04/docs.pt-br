---
ms.openlocfilehash: 4254cceab0048341b32fe5babf53b5ea3e5a52d6
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "72846994"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a>Alteração da definição XOML do fluxo de trabalho e das chaves de cache SqlTrackingService de MD5 para SHA256

|   |   |
|---|---|
|Detalhes|O Tempo de Execução de Fluxo de Trabalho mantém um cache de definições de fluxo de trabalho definido em XOML. O SqlTrackingService também mantém um cache inserido por cadeias de caracteres. Esses caches são inseridos por valores que incluem o valor de hash da soma de verificação. No .NET Framework 4.7.2 e versões anteriores, o hash de soma de verificação usava o algoritmo MD5, o que causou problemas em sistemas habilitados para FIPS. A partir do .NET Framework 4,8, o algoritmo usado é SHA256. Não deve haver um problema de compatibilidade com essa alteração porque os valores são recalculados toda vez que o tempo de execução do fluxo de trabalho e o SqlTrackingService são iniciados. No entanto, fornecemos quirks para permitir que os clientes revertam para o uso do algoritmo de hash herdado, se necessário.|
|Sugestão|Se essa alteração apresentar um problema ao executar fluxos de trabalho, tente definir um ou ambos os comutadores <code>AppContext</code>:<ul><li>&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; como true.</li><li>&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; como true.</li></ul>No código:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>Ou, no arquivo de configuração (isso precisa estar no arquivo de configuração para o aplicativo que está criando o objeto <xref:System.Workflow.Runtime.WorkflowRuntime>):<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Version|4.8|
|Digite|Redirecionando|
