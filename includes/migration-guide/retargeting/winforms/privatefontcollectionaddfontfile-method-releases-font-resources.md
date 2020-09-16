---
ms.openlocfilehash: 6ee290f6722480778381376f588e16877894f232
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606849"
---
### <a name="privatefontcollectionaddfontfile-method-releases-font-resources"></a><span data-ttu-id="4a3f5-101">O método PrivateFontCollection.AddFontFile libera os recursos de fonte</span><span class="sxs-lookup"><span data-stu-id="4a3f5-101">PrivateFontCollection.AddFontFile method releases Font resources</span></span>

#### <a name="details"></a><span data-ttu-id="4a3f5-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="4a3f5-102">Details</span></span>

<span data-ttu-id="4a3f5-103">No .NET Framework 4.7.1 e nas versões anteriores, a classe <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> não libera os recursos de fonte GDI+ depois que a <xref:System.Drawing.Text.PrivateFontCollection> é descartada para os objetos <xref:System.Drawing.Font> que são adicionados a essa coleção usando o método <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="4a3f5-103">In the .NET Framework 4.7.1 and previous versions, the <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> class does not release the GDI+ font resources after the <xref:System.Drawing.Text.PrivateFontCollection> is disposed for <xref:System.Drawing.Font> objects that are added to this collection using the <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)> method.</span></span> <span data-ttu-id="4a3f5-104">No .NET Framework 4.7.2 e posterior <xref:System.Drawing.Text.FontCollection.Dispose%2A> libera as fontes GDI+ que foram adicionadas à coleção como arquivos.</span><span class="sxs-lookup"><span data-stu-id="4a3f5-104">In the .NET Framework 4.7.2 and later <xref:System.Drawing.Text.FontCollection.Dispose%2A> releases the GDI+ fonts that were added to the collection as files.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4a3f5-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="4a3f5-105">Suggestion</span></span>

<span data-ttu-id="4a3f5-106">**Como aceitar ou recusar essas alterações** Para que um aplicativo se beneficie dessas alterações, ele deve ser executado no .NET Framework 4.7.2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="4a3f5-106">**How to opt in or out of these changes** In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="4a3f5-107">O aplicativo pode se beneficiar dessas alterações de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="4a3f5-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="4a3f5-108">Ser recompilado para ser direcionado ao .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="4a3f5-108">It is recompiled to target the .NET Framework 4.7.2.</span></span> <span data-ttu-id="4a3f5-109">Essa alteração é habilitada por padrão nos aplicativos do Windows Forms direcionados ao .NET Framework 4.7.2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="4a3f5-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="4a3f5-110">Ser direcionado ao .NET Framework 4.7.1 ou a uma versão anterior e recusar os comportamentos de acessibilidade herdados, adicionando a seguinte [Opção AppContext](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) à seção `<runtime>` do arquivo app.config e definindo-a como `false`, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4a3f5-110">It targets the .NET Framework 4.7.1 or an earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext Switch](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the `<runtime>` section of the app.config file and setting it to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Drawing.Text.DoNotRemoveGdiFontsResourcesFromFontCollection=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

<span data-ttu-id="4a3f5-111">Os aplicativos direcionados ao .NET Framework 4.7.2 ou posterior que desejam preservar o comportamento herdado podem aceitar não liberar os recursos de fonte definindo explicitamente essa opção AppContext como `true`.</span><span class="sxs-lookup"><span data-stu-id="4a3f5-111">Applications that target the .NET Framework 4.7.2 or later, and want to preserve the legacy behavior can opt in to not release font resources by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="4a3f5-112">Name</span><span class="sxs-lookup"><span data-stu-id="4a3f5-112">Name</span></span>    | <span data-ttu-id="4a3f5-113">Valor</span><span class="sxs-lookup"><span data-stu-id="4a3f5-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4a3f5-114">Escopo</span><span class="sxs-lookup"><span data-stu-id="4a3f5-114">Scope</span></span>   | <span data-ttu-id="4a3f5-115">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="4a3f5-115">Edge</span></span>        |
| <span data-ttu-id="4a3f5-116">Versão</span><span class="sxs-lookup"><span data-stu-id="4a3f5-116">Version</span></span> | <span data-ttu-id="4a3f5-117">4.7.2</span><span class="sxs-lookup"><span data-stu-id="4a3f5-117">4.7.2</span></span>       |
| <span data-ttu-id="4a3f5-118">Tipo</span><span class="sxs-lookup"><span data-stu-id="4a3f5-118">Type</span></span>    | <span data-ttu-id="4a3f5-119">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="4a3f5-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="4a3f5-120">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="4a3f5-120">Affected APIs</span></span>

- <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType>
- <xref:System.Drawing.Text.FontCollection.Dispose?displayProperty=nameWithType>
