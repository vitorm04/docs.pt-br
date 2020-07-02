---
ms.openlocfilehash: a82b720fd4e771481ea1142a88a095443afa0d5b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614317"
---
### <a name="keyboard-focus-now-moves-correctly-across-multiple-layers-of-winformswpf-hosting"></a><span data-ttu-id="652db-101">O foco do teclado agora é movido corretamente em várias camadas de hospedagem do WinForms/WPF</span><span class="sxs-lookup"><span data-stu-id="652db-101">Keyboard focus now moves correctly across multiple layers of WinForms/WPF hosting</span></span>

#### <a name="details"></a><span data-ttu-id="652db-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="652db-102">Details</span></span>

<span data-ttu-id="652db-103">Considere um aplicativo WPF que hospede um controle do WinForms que, por sua vez, hospede controles do WPF.</span><span class="sxs-lookup"><span data-stu-id="652db-103">Consider a WPF application hosting a WinForms control which in turn hosts WPF controls.</span></span> <span data-ttu-id="652db-104">É possível que os usuários não consigam sair com Tab da camada do WinForms se o primeiro ou o último controle nessa camada for o `System.Windows.Forms.Integration.ElementHost` do WPF.</span><span class="sxs-lookup"><span data-stu-id="652db-104">Users may not be able to tab out of the WinForms layer if the first or last control in that layer is the WPF `System.Windows.Forms.Integration.ElementHost`.</span></span> <span data-ttu-id="652db-105">Essa alteração corrige esse problema e os usuários agora conseguem sair com Tab da camada do WinForms. Os aplicativos automatizados baseados em foco que nunca saem da camada do WinForms podem não funcionar mais conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="652db-105">This change fixes this issue, and users are now able to tab out of the WinForms layer.Automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="652db-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="652db-106">Suggestion</span></span>

<span data-ttu-id="652db-107">O desenvolvedor que desejar utilizar esta alteração ao direcionar a uma versão do framework abaixo do .NET 4.7.2 poderá definir o seguinte conjunto de sinalizadores de AppContext como false para que a alteração seja habilitada.</span><span class="sxs-lookup"><span data-stu-id="652db-107">A developer who wants to utilize this change while targeting a framework version below .NET 4.7.2 can set the following set of AppContext flags to false for the change to be enabled.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="652db-108">Os aplicativos WPF precisam aceitar todas as melhorias de acessibilidade iniciais para obter as melhorias mais recentes.</span><span class="sxs-lookup"><span data-stu-id="652db-108">WPF applications must opt in to all early accessibility improvements to get the later improvements.</span></span> <span data-ttu-id="652db-109">Em outras palavras, ambas as opções `Switch.UseLegacyAccessibilityFeatures` e `Switch.UseLegacyAccessibilityFeatures.2` precisam ser definidas. O desenvolvedor que precisar da funcionalidade anterior ao direcionar ao .NET 4.7.2 ou a versões posteriores poderá definir o seguinte sinalizador de AppContext como true para que a alteração seja desabilitada.</span><span class="sxs-lookup"><span data-stu-id="652db-109">In other words, both the `Switch.UseLegacyAccessibilityFeatures` and the `Switch.UseLegacyAccessibilityFeatures.2` switches must be setA developer who requires the previous functionality while targeting .NET 4.7.2 or greater can set the following AppContext flag to true for the change to be disabled.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="652db-110">Name</span><span class="sxs-lookup"><span data-stu-id="652db-110">Name</span></span>    | <span data-ttu-id="652db-111">Valor</span><span class="sxs-lookup"><span data-stu-id="652db-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="652db-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="652db-112">Scope</span></span>   | <span data-ttu-id="652db-113">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="652db-113">Edge</span></span>        |
| <span data-ttu-id="652db-114">Versão</span><span class="sxs-lookup"><span data-stu-id="652db-114">Version</span></span> | <span data-ttu-id="652db-115">4.7.2</span><span class="sxs-lookup"><span data-stu-id="652db-115">4.7.2</span></span>       |
| <span data-ttu-id="652db-116">Type</span><span class="sxs-lookup"><span data-stu-id="652db-116">Type</span></span>    | <span data-ttu-id="652db-117">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="652db-117">Retargeting</span></span> |
