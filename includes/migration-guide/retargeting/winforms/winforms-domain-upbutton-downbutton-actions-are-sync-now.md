---
ms.openlocfilehash: c64431fd651fd7d53fb46231c6acc10c5cb43fff
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606907"
---
### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a><span data-ttu-id="1c00b-101">As ações de upbutton e downbutton de domínio do WinForm agora estão sincronizadas</span><span class="sxs-lookup"><span data-stu-id="1c00b-101">WinForm's Domain upbutton and downbutton actions are in sync now</span></span>

#### <a name="details"></a><span data-ttu-id="1c00b-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="1c00b-102">Details</span></span>

<span data-ttu-id="1c00b-103">No .NET Framework 4.7.1 e nas versões anteriores, a ação <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> do controle <xref:System.Windows.Forms.DomainUpDown> é ignorada quando o texto do controle está presente e o desenvolvedor precisa usar a ação <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> no controle antes de usar a ação <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1c00b-103">In the .NET Framework 4.7.1 and previous versions the <xref:System.Windows.Forms.DomainUpDown> control's <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action is ignored when control text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before using <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="1c00b-104">Começando com o .NET Framework 4.7.2, as ações <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> e <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> funcionam de forma independente neste cenário e permanecem em sincronização.</span><span class="sxs-lookup"><span data-stu-id="1c00b-104">Starting with the .NET Framework 4.7.2 both the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> actions work independently in this scenario and remain in sync.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1c00b-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="1c00b-105">Suggestion</span></span>

<span data-ttu-id="1c00b-106">Para que o aplicativo se beneficie dessas alterações, ele deverá ser executado no .NET Framework 4.7.2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="1c00b-106">In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="1c00b-107">O aplicativo pode se beneficiar dessas alterações de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="1c00b-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="1c00b-108">Ser recompilado para ser direcionado ao .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="1c00b-108">It is recompiled to target the .NET Framework 4.7.2.</span></span> <span data-ttu-id="1c00b-109">Essa alteração é habilitada por padrão nos aplicativos do Windows Forms direcionados ao .NET Framework 4.7.2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="1c00b-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="1c00b-110">Recusar o comportamento de rolagem herdado adicionando a seguinte [Opção de AppContext](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) à seção `<runtime>` do arquivo de configuração de aplicativo e configurando-a como `false`, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1c00b-110">It opts out of the legacy scrolling behavior by adding the following [AppContext Switch](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the `<runtime>` section of the app config file and setting it to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="1c00b-111">Name</span><span class="sxs-lookup"><span data-stu-id="1c00b-111">Name</span></span>    | <span data-ttu-id="1c00b-112">Valor</span><span class="sxs-lookup"><span data-stu-id="1c00b-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1c00b-113">Escopo</span><span class="sxs-lookup"><span data-stu-id="1c00b-113">Scope</span></span>   | <span data-ttu-id="1c00b-114">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="1c00b-114">Edge</span></span>        |
| <span data-ttu-id="1c00b-115">Versão</span><span class="sxs-lookup"><span data-stu-id="1c00b-115">Version</span></span> | <span data-ttu-id="1c00b-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="1c00b-116">4.7.2</span></span>       |
| <span data-ttu-id="1c00b-117">Tipo</span><span class="sxs-lookup"><span data-stu-id="1c00b-117">Type</span></span>    | <span data-ttu-id="1c00b-118">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="1c00b-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="1c00b-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="1c00b-119">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
