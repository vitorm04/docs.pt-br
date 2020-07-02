---
ms.openlocfilehash: 4303b177ffe01328965c909a5a3809414fcead91
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614315"
---
### <a name="the-default-hash-algorithm-for-wpfs-markup-compiler-is-now-sha256"></a><span data-ttu-id="4fa9f-101">O algoritmo de hash padrão do compilador de marcação do WPF agora é o SHA256</span><span class="sxs-lookup"><span data-stu-id="4fa9f-101">The default hash algorithm for WPF's Markup Compiler is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="4fa9f-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="4fa9f-102">Details</span></span>

<span data-ttu-id="4fa9f-103">O MarkupCompiler do WPF fornece serviços de compilação para arquivos de marcação XAML.</span><span class="sxs-lookup"><span data-stu-id="4fa9f-103">The WPF MarkupCompiler provides compilation services for XAML markup files.</span></span>  <span data-ttu-id="4fa9f-104">No .NET Framework 4.7.1 e nas versões anteriores, o algoritmo de hash padrão usado para as somas de verificação era o SHA1.</span><span class="sxs-lookup"><span data-stu-id="4fa9f-104">In the .NET Framework 4.7.1 and earlier versions, the default hash algorithm used for checksums was SHA1.</span></span> <span data-ttu-id="4fa9f-105">Devido a questões de segurança recentes com o SHA1, esse padrão foi alterado para o SHA256 começando com o .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="4fa9f-105">Due to recent security concerns with SHA1, this default has been changed to SHA256 starting with the .NET Framework 4.7.2.</span></span>  <span data-ttu-id="4fa9f-106">Essa alteração afeta toda a geração de soma de verificação para arquivos de marcação durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="4fa9f-106">This change affects all checksum generation for markup files during compilation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4fa9f-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="4fa9f-107">Suggestion</span></span>

<span data-ttu-id="4fa9f-108">O desenvolvedor que direcionar ao .NET Framework 4.7.2 ou superior e desejar reverter para o comportamento de hash do SHA1 precisará definir o sinalizador de AppContext a seguir.</span><span class="sxs-lookup"><span data-stu-id="4fa9f-108">A developer who targets .NET Framework 4.7.2 or greater and wants to revert to SHA1 hashing behavior must set the following AppContext flag.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="4fa9f-109">O desenvolvedor que desejar utilizar o hash SHA256 ao direcionar a uma versão do framework abaixo do .NET 4.7.2 precisará definir o sinalizador de AppContext abaixo.</span><span class="sxs-lookup"><span data-stu-id="4fa9f-109">A developer who wants to utilize SHA256 hashing while targeting a framework version below .NET 4.7.2 must set the below AppContext flag.</span></span>  <span data-ttu-id="4fa9f-110">Observe que a versão instalada do .NET Framework precisará ser a 4.7.2 ou superior.</span><span class="sxs-lookup"><span data-stu-id="4fa9f-110">Note that the installed version of the .NET Framework must be 4.7.2 or greater.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=false&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="4fa9f-111">Name</span><span class="sxs-lookup"><span data-stu-id="4fa9f-111">Name</span></span>    | <span data-ttu-id="4fa9f-112">Valor</span><span class="sxs-lookup"><span data-stu-id="4fa9f-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4fa9f-113">Escopo</span><span class="sxs-lookup"><span data-stu-id="4fa9f-113">Scope</span></span>   | <span data-ttu-id="4fa9f-114">Transparente</span><span class="sxs-lookup"><span data-stu-id="4fa9f-114">Transparent</span></span> |
| <span data-ttu-id="4fa9f-115">Versão</span><span class="sxs-lookup"><span data-stu-id="4fa9f-115">Version</span></span> | <span data-ttu-id="4fa9f-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="4fa9f-116">4.7.2</span></span>       |
| <span data-ttu-id="4fa9f-117">Type</span><span class="sxs-lookup"><span data-stu-id="4fa9f-117">Type</span></span>    | <span data-ttu-id="4fa9f-118">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="4fa9f-118">Retargeting</span></span> |
