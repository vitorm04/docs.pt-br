---
ms.openlocfilehash: f75a652f15be6b0d184db20dc5cd8aafd80539fe
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614312"
---
### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a><span data-ttu-id="4b9d7-101">As ações de upbutton e downbutton de domínio do WinForm agora estão sincronizadas</span><span class="sxs-lookup"><span data-stu-id="4b9d7-101">WinForm's Domain upbutton and downbutton actions are in sync now</span></span>

#### <a name="details"></a><span data-ttu-id="4b9d7-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="4b9d7-102">Details</span></span>

<span data-ttu-id="4b9d7-103">No .NET Framework 4.7.1 e nas versões anteriores, a ação <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> do controle <xref:System.Windows.Forms.DomainUpDown> é ignorada quando o texto do controle está presente e o desenvolvedor precisa usar a ação <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> no controle antes de usar a ação <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4b9d7-103">In the .NET Framework 4.7.1 and previous versions the <xref:System.Windows.Forms.DomainUpDown> control's <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action is ignored when control text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before using <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="4b9d7-104">Começando com o .NET Framework 4.7.2, as ações <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> e <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> funcionam de forma independente neste cenário e permanecem em sincronização.</span><span class="sxs-lookup"><span data-stu-id="4b9d7-104">Starting with the .NET Framework 4.7.2 both the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> actions work independently in this scenario and remain in sync.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4b9d7-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="4b9d7-105">Suggestion</span></span>

<span data-ttu-id="4b9d7-106">Para que o aplicativo se beneficie dessas alterações, ele deverá ser executado no .NET Framework 4.7.2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="4b9d7-106">In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="4b9d7-107">O aplicativo pode se beneficiar dessas alterações de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="4b9d7-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="4b9d7-108">Ser recompilado para ser direcionado ao .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="4b9d7-108">It is recompiled to target the .NET Framework 4.7.2.</span></span> <span data-ttu-id="4b9d7-109">Essa alteração é habilitada por padrão nos aplicativos do Windows Forms direcionados ao .NET Framework 4.7.2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="4b9d7-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="4b9d7-110">Recusar o comportamento de rolagem herdado adicionando a seguinte [Opção de AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) à seção `<runtime>` do arquivo de configuração de aplicativo e configurando-a como `false`, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4b9d7-110">It opts out of the legacy scrolling behavior by adding the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the `<runtime>` section of the app config file and setting it to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="4b9d7-111">Name</span><span class="sxs-lookup"><span data-stu-id="4b9d7-111">Name</span></span>    | <span data-ttu-id="4b9d7-112">Valor</span><span class="sxs-lookup"><span data-stu-id="4b9d7-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4b9d7-113">Escopo</span><span class="sxs-lookup"><span data-stu-id="4b9d7-113">Scope</span></span>   | <span data-ttu-id="4b9d7-114">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="4b9d7-114">Edge</span></span>        |
| <span data-ttu-id="4b9d7-115">Versão</span><span class="sxs-lookup"><span data-stu-id="4b9d7-115">Version</span></span> | <span data-ttu-id="4b9d7-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="4b9d7-116">4.7.2</span></span>       |
| <span data-ttu-id="4b9d7-117">Type</span><span class="sxs-lookup"><span data-stu-id="4b9d7-117">Type</span></span>    | <span data-ttu-id="4b9d7-118">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="4b9d7-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="4b9d7-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="4b9d7-119">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
