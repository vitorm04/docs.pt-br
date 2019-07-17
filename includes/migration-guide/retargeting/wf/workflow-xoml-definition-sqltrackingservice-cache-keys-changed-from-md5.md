---
ms.openlocfilehash: 47aa67096f8dcd250521d9c34dde97cb2eb368d7
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803446"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a>Alteração da definição XOML do fluxo de trabalho e das chaves de cache SqlTrackingService de MD5 para SHA256

|   |   |
|---|---|
|Detalhes|O Tempo de Execução de Fluxo de Trabalho mantém um cache de definições de fluxo de trabalho definido em XOML. O SqlTrackingService também mantém um cache inserido por cadeias de caracteres. Esses caches são inseridos por valores que incluem o valor de hash da soma de verificação. No .NET Framework 4.7.2 e versões anteriores, o hash de soma de verificação usava o algoritmo MD5, o que causou problemas em sistemas habilitados para FIPS. Começando com o .NET Framework 4.8, o algoritmo usado é SHA256. Não deve haver nenhum problema de compatibilidade com essa alteração, porque os valores são recalculados sempre que o Tempo de Execução de Fluxo de Trabalho e o SqlTrackingService são iniciados. No entanto, fornecemos quirks para permitir que os clientes revertam para o uso do algoritmo de hash herdado, se necessário.|
|Sugestão|Se essa alteração apresentar um problema ao executar fluxos de trabalho, tente definir um ou ambos os comutadores <code>AppContext</code>:<ul><li>&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; como true.</li><li>&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; como true.</li></ul>No código:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>Ou, no arquivo de configuração (isso precisa estar no arquivo de configuração para o aplicativo que está criando o objeto <xref:System.Workflow.Runtime.WorkflowRuntime>):<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Versão|4.8|
|Tipo|Redirecionando|

