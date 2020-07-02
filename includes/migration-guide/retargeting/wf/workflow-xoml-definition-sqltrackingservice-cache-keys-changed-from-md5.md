---
ms.openlocfilehash: 7a7ecf052276fe8e62463498b83230d466630c79
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617779"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a><span data-ttu-id="2a004-101">Alteração da definição XOML do fluxo de trabalho e das chaves de cache SqlTrackingService de MD5 para SHA256</span><span class="sxs-lookup"><span data-stu-id="2a004-101">Workflow XOML definition and SqlTrackingService cache keys changed from MD5 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="2a004-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="2a004-102">Details</span></span>

<span data-ttu-id="2a004-103">O runtime de fluxo de trabalho mantém um cache de definições de fluxo de trabalho definido em XOML.</span><span class="sxs-lookup"><span data-stu-id="2a004-103">The Workflow Runtime in keeps a cache of workflow definitions defined in XOML.</span></span> <span data-ttu-id="2a004-104">O SqlTrackingService também mantém um cache inserido por cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="2a004-104">The SqlTrackingService also keeps a cache that is keyed by strings.</span></span> <span data-ttu-id="2a004-105">Esses caches são inseridos por valores que incluem o valor de hash da soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="2a004-105">These caches are keyed by values that include checksum hash value.</span></span> <span data-ttu-id="2a004-106">No .NET Framework 4.7.2 e versões anteriores, o hash de soma de verificação usava o algoritmo MD5, o que causou problemas em sistemas habilitados para FIPS.</span><span class="sxs-lookup"><span data-stu-id="2a004-106">In the .NET Framework 4.7.2 and earlier versions, this checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="2a004-107">A partir do .NET Framework 4,8, o algoritmo usado é SHA256. Não deve haver um problema de compatibilidade com essa alteração porque os valores são recalculados toda vez que o tempo de execução do fluxo de trabalho e o SqlTrackingService são iniciados.</span><span class="sxs-lookup"><span data-stu-id="2a004-107">Starting with the .NET Framework 4.8, the algorithm used is SHA256.There shouldn't be a compatibility issue with this change because the values are recalculated each time the Workflow Runtime and SqlTrackingService is started.</span></span> <span data-ttu-id="2a004-108">No entanto, fornecemos quirks para permitir que os clientes revertam para o uso do algoritmo de hash herdado, se necessário.</span><span class="sxs-lookup"><span data-stu-id="2a004-108">However, we have provided quirks to allow customers to revert back to usage of the legacy hashing algorithm, if necessary.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2a004-109">Sugestão</span><span class="sxs-lookup"><span data-stu-id="2a004-109">Suggestion</span></span>

<span data-ttu-id="2a004-110">Se essa alteração apresentar um problema ao executar fluxos de trabalho, tente definir um ou ambos os comutadores `AppContext`:</span><span class="sxs-lookup"><span data-stu-id="2a004-110">If this change presents a problem when executing workflows, try setting one or both of the `AppContext` switches:</span></span>

- <span data-ttu-id="2a004-111">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; como true.</span><span class="sxs-lookup"><span data-stu-id="2a004-111">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; to true.</span></span>
- <span data-ttu-id="2a004-112">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; como true.</span><span class="sxs-lookup"><span data-stu-id="2a004-112">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; to true.</span></span>
<span data-ttu-id="2a004-113">No código:</span><span class="sxs-lookup"><span data-stu-id="2a004-113">In code:</span></span>

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>

<span data-ttu-id="2a004-114">Ou, no arquivo de configuração (isso precisa estar no arquivo de configuração para o aplicativo que está criando o objeto <xref:System.Workflow.Runtime.WorkflowRuntime>):</span><span class="sxs-lookup"><span data-stu-id="2a004-114">Or in the configuration file (this needs to be in the config file for the application that is creating the <xref:System.Workflow.Runtime.WorkflowRuntime> object):</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="2a004-115">Name</span><span class="sxs-lookup"><span data-stu-id="2a004-115">Name</span></span>    | <span data-ttu-id="2a004-116">Valor</span><span class="sxs-lookup"><span data-stu-id="2a004-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2a004-117">Escopo</span><span class="sxs-lookup"><span data-stu-id="2a004-117">Scope</span></span>   | <span data-ttu-id="2a004-118">Secundária</span><span class="sxs-lookup"><span data-stu-id="2a004-118">Minor</span></span>       |
| <span data-ttu-id="2a004-119">Versão</span><span class="sxs-lookup"><span data-stu-id="2a004-119">Version</span></span> | <span data-ttu-id="2a004-120">4.8</span><span class="sxs-lookup"><span data-stu-id="2a004-120">4.8</span></span>         |
| <span data-ttu-id="2a004-121">Type</span><span class="sxs-lookup"><span data-stu-id="2a004-121">Type</span></span>    | <span data-ttu-id="2a004-122">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="2a004-122">Retargeting</span></span> |
