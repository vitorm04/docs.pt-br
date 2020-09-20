---
ms.openlocfilehash: 4bc8db52efdfe483acb4f6b6e33c4fa7716e0b79
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770788"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a><span data-ttu-id="8cc70-101">Alteração de alto contraste de ComboBox de svcTraceViewer</span><span class="sxs-lookup"><span data-stu-id="8cc70-101">svcTraceViewer ComboBox high contrast change</span></span>

#### <a name="details"></a><span data-ttu-id="8cc70-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8cc70-102">Details</span></span>

<span data-ttu-id="8cc70-103">Na [ferramenta Visualizador de Rastreamento de Serviço da Microsoft](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), os controles ComboBox não eram exibidos na cor correta em determinados temas de alto contraste.</span><span class="sxs-lookup"><span data-stu-id="8cc70-103">In the [Microsoft Service Trace Viewer tool](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), ComboBox controls were not displayed in the correct color in certain high contrast themes.</span></span> <span data-ttu-id="8cc70-104">O problema foi corrigido no .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="8cc70-104">The issue was fixed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="8cc70-105">No entanto, devido aos requisitos de compatibilidade com versões anteriores do SDK do .NET Framework, a correção não estava visível para clientes por padrão.</span><span class="sxs-lookup"><span data-stu-id="8cc70-105">However, due to .NET Framework SDK backward compatibility requirements, the fix was not visible to customers by default.</span></span> <span data-ttu-id="8cc70-106">O .NET 4.8 revela essa alteração adicionando os seguintes [comutadores de configuração do AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) ao arquivo svcTraceViewer.exe.config:</span><span class="sxs-lookup"><span data-stu-id="8cc70-106">.NET 4.8 surfaces this change by adding the following [AppContext configuration switches](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the svcTraceViewer.exe.config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
```

#### <a name="suggestion"></a><span data-ttu-id="8cc70-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="8cc70-107">Suggestion</span></span>

<span data-ttu-id="8cc70-108">Se não quiser que a alteração do comportamento de alto contraste seja alterada, você poderá desabilitá-la removendo a seguinte seção do arquivo de svcTraceViewer.exe.config:</span><span class="sxs-lookup"><span data-stu-id="8cc70-108">If you don't want to have the high contrast behavior change, you can disable it by removing the following section from the svcTraceViewer.exe.config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
```

| <span data-ttu-id="8cc70-109">Nome</span><span class="sxs-lookup"><span data-stu-id="8cc70-109">Name</span></span>    | <span data-ttu-id="8cc70-110">Valor</span><span class="sxs-lookup"><span data-stu-id="8cc70-110">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="8cc70-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="8cc70-111">Scope</span></span>   | <span data-ttu-id="8cc70-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="8cc70-112">Edge</span></span>    |
| <span data-ttu-id="8cc70-113">Versão</span><span class="sxs-lookup"><span data-stu-id="8cc70-113">Version</span></span> | <span data-ttu-id="8cc70-114">4.8</span><span class="sxs-lookup"><span data-stu-id="8cc70-114">4.8</span></span>     |
| <span data-ttu-id="8cc70-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="8cc70-115">Type</span></span>    | <span data-ttu-id="8cc70-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="8cc70-116">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="8cc70-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8cc70-117">Affected APIs</span></span>

<span data-ttu-id="8cc70-118">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="8cc70-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
