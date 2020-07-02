---
ms.openlocfilehash: 06f4186e8f233f5c769dfc5e05d2de5eacd9b053
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621912"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a><span data-ttu-id="2cbf1-101">Alteração de alto contraste de ComboBox de svcTraceViewer</span><span class="sxs-lookup"><span data-stu-id="2cbf1-101">svcTraceViewer ComboBox high contrast change</span></span>

#### <a name="details"></a><span data-ttu-id="2cbf1-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="2cbf1-102">Details</span></span>

<span data-ttu-id="2cbf1-103">Na [ferramenta Visualizador de Rastreamento de Serviço da Microsoft](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), os controles ComboBox não eram exibidos na cor correta em determinados temas de alto contraste.</span><span class="sxs-lookup"><span data-stu-id="2cbf1-103">In the [Microsoft Service Trace Viewer tool](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), ComboBox controls were not displayed in the correct color in certain high contrast themes.</span></span> <span data-ttu-id="2cbf1-104">O problema foi corrigido no .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="2cbf1-104">The issue was fixed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="2cbf1-105">No entanto, devido aos requisitos de compatibilidade com versões anteriores do SDK do .NET Framework, a correção não estava visível para clientes por padrão.</span><span class="sxs-lookup"><span data-stu-id="2cbf1-105">However, due to .NET Framework SDK backward compatibility requirements, the fix was not visible to customers by default.</span></span> <span data-ttu-id="2cbf1-106">O .NET 4.8 revela essa alteração adicionando os seguintes [comutadores de configuração do AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) ao arquivo svcTraceViewer.exe.config:</span><span class="sxs-lookup"><span data-stu-id="2cbf1-106">.NET 4.8 surfaces this change by adding the following [AppContext configuration switches](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the svcTraceViewer.exe.config file:</span></span><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>

#### <a name="suggestion"></a><span data-ttu-id="2cbf1-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="2cbf1-107">Suggestion</span></span>

<ul><li><span data-ttu-id="2cbf1-108">Como recusar a alteração Se você não quiser ter a alteração de comportamento de alto contraste, poderá desabilitá-la removendo a seguinte seção do arquivo svcTraceViewer.exe.config:</span><span class="sxs-lookup"><span data-stu-id="2cbf1-108">How to opt out of the change If you don't want to have the high contrast behavior change, you can disable it by removing the following section from the svcTraceViewer.exe.config file:</span></span></li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="2cbf1-109">Name</span><span class="sxs-lookup"><span data-stu-id="2cbf1-109">Name</span></span>    | <span data-ttu-id="2cbf1-110">Valor</span><span class="sxs-lookup"><span data-stu-id="2cbf1-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2cbf1-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="2cbf1-111">Scope</span></span>   |<span data-ttu-id="2cbf1-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="2cbf1-112">Edge</span></span>|
|<span data-ttu-id="2cbf1-113">Versão</span><span class="sxs-lookup"><span data-stu-id="2cbf1-113">Version</span></span>|<span data-ttu-id="2cbf1-114">4.8</span><span class="sxs-lookup"><span data-stu-id="2cbf1-114">4.8</span></span>|
|<span data-ttu-id="2cbf1-115">Type</span><span class="sxs-lookup"><span data-stu-id="2cbf1-115">Type</span></span>|<span data-ttu-id="2cbf1-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="2cbf1-116">Runtime</span></span>|
