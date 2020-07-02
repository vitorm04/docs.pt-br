---
ms.openlocfilehash: 2aa424ff5e3308b730c22cb865993d4100f193cc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617780"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a><span data-ttu-id="ce2f3-101">Somas de verificação do arquivo XOML de fluxo de trabalho alteradas de MD5 para SHA256</span><span class="sxs-lookup"><span data-stu-id="ce2f3-101">Workflow XOML file checksums changed from MD5 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="ce2f3-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ce2f3-102">Details</span></span>

<span data-ttu-id="ce2f3-103">Para oferecer suporte à depuração de fluxos de trabalho baseados em XOML com o Visual Studio, quando projetos de fluxo de trabalho que contêm arquivos XOML são criados, uma soma de verificação do conteúdo do arquivo XOML é incluída no código gerado como um valor <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ce2f3-103">To support debugging XOML-based workflows with Visual Studio, when workflow projects containing XOML files build, a checksum of the contents of the XOML file is included in the code generated as a <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="ce2f3-104">No .NET Framework 4.7.2 e versões anteriores, o hash de soma de verificação usava o algoritmo MD5, o que causou problemas em sistemas habilitados para FIPS.</span><span class="sxs-lookup"><span data-stu-id="ce2f3-104">In the .NET Framework 4.7.2 and earlier versions, this checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="ce2f3-105">A partir do .NET Framework 4.8, o algoritmo usado será o SHA256.</span><span class="sxs-lookup"><span data-stu-id="ce2f3-105">Starting with the .NET Framework 4.8, the algorithm used is SHA256.</span></span> <span data-ttu-id="ce2f3-106">Para ser compatível com WorkflowMarkupSourceAttribute.MD5Digest, somente os primeiros 16 bytes da soma de verificação gerada são usados. Isso pode causar problemas durante a depuração.</span><span class="sxs-lookup"><span data-stu-id="ce2f3-106">To be compatibile with the WorkflowMarkupSourceAttribute.MD5Digest, only the first 16 bytes of the generated checksum are used.This may cause problems during debugging.</span></span> <span data-ttu-id="ce2f3-107">Você precisará compilar novamente seu projeto.</span><span class="sxs-lookup"><span data-stu-id="ce2f3-107">You may need to re-build your project.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ce2f3-108">Sugestão</span><span class="sxs-lookup"><span data-stu-id="ce2f3-108">Suggestion</span></span>

<span data-ttu-id="ce2f3-109">Se compilar novamente o projeto não resolver o problema, tente definir a `AppContext` opção &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; como true. no código:</span><span class="sxs-lookup"><span data-stu-id="ce2f3-109">If re-building your project does not solve the problem, try setting the `AppContext` switch &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; to true.In code:</span></span>

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre>

<span data-ttu-id="ce2f3-110">Ou em um arquivo de configuração (isso precisa estar no MSBuild.exe.config para o MSBuild.exe que você está usando):</span><span class="sxs-lookup"><span data-stu-id="ce2f3-110">Or in a configuration file (this needs to be in MSBuild.exe.config for the MSBuild.exe that you are using):</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="ce2f3-111">Name</span><span class="sxs-lookup"><span data-stu-id="ce2f3-111">Name</span></span>    | <span data-ttu-id="ce2f3-112">Valor</span><span class="sxs-lookup"><span data-stu-id="ce2f3-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ce2f3-113">Escopo</span><span class="sxs-lookup"><span data-stu-id="ce2f3-113">Scope</span></span>   | <span data-ttu-id="ce2f3-114">Secundária</span><span class="sxs-lookup"><span data-stu-id="ce2f3-114">Minor</span></span>       |
| <span data-ttu-id="ce2f3-115">Versão</span><span class="sxs-lookup"><span data-stu-id="ce2f3-115">Version</span></span> | <span data-ttu-id="ce2f3-116">4.8</span><span class="sxs-lookup"><span data-stu-id="ce2f3-116">4.8</span></span>         |
| <span data-ttu-id="ce2f3-117">Type</span><span class="sxs-lookup"><span data-stu-id="ce2f3-117">Type</span></span>    | <span data-ttu-id="ce2f3-118">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="ce2f3-118">Retargeting</span></span> |
