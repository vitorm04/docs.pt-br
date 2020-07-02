---
ms.openlocfilehash: 97299ddb9bee89c792ddb3d2b9c37516180996f7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614308"
---
### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a><span data-ttu-id="7a1b9-101">A propriedade ContextMenuStrip.SourceControl contém um controle válido no caso de ToolStripMenuItems aninhados</span><span class="sxs-lookup"><span data-stu-id="7a1b9-101">ContextMenuStrip.SourceControl property contains a valid control in the case of nested ToolStripMenuItems</span></span>

#### <a name="details"></a><span data-ttu-id="7a1b9-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="7a1b9-102">Details</span></span>

<span data-ttu-id="7a1b9-103">No .NET Framework 4.7.1 e nas versões anteriores, a propriedade <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> retorna nulo incorretamente quando o usuário abre o menu de controles <xref:System.Windows.Forms.ToolStripMenuItem> aninhados.</span><span class="sxs-lookup"><span data-stu-id="7a1b9-103">In the .NET Framework 4.7.1 and previous versions, the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property incorrectly returns null when the user opens the menu from nested <xref:System.Windows.Forms.ToolStripMenuItem> controls.</span></span> <span data-ttu-id="7a1b9-104">No .NET Framework 4.7.2 e posterior, a propriedade <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> é sempre definida como o controle do código-fonte real.</span><span class="sxs-lookup"><span data-stu-id="7a1b9-104">In the .NET Framework 4.7.2 and later, <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> property is always set to the actual source control.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7a1b9-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="7a1b9-105">Suggestion</span></span>

<span data-ttu-id="7a1b9-106">**Como aceitar ou recusar essas alterações** Para que um aplicativo se beneficie dessas alterações, ele deve ser executado no .NET Framework 4.7.2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="7a1b9-106">**How to opt in or out of these changes** In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="7a1b9-107">O aplicativo pode se beneficiar dessas alterações de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="7a1b9-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="7a1b9-108">Ser direcionado ao .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="7a1b9-108">It targets the .NET Framework 4.7.2.</span></span> <span data-ttu-id="7a1b9-109">Essa alteração é habilitada por padrão nos aplicativos do Windows Forms direcionados ao .NET Framework 4.7.2 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="7a1b9-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="7a1b9-110">Ser direcionado ao .NET Framework 4.7.1 ou a uma versão anterior e recusar os comportamentos de acessibilidade herdados, adicionando a seguinte [Opção AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) à seção `<runtime>` do arquivo app.config e definindo-a como `false`, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7a1b9-110">It targets the .NET Framework 4.7.1 or an earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the `<runtime>` section of the app.config file and setting it to `false`, as the following example shows.</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false"/>
</runtime>
```

<span data-ttu-id="7a1b9-111">Os aplicativos direcionados ao .NET Framework 4.7.2 ou posterior que desejam preservar o comportamento de acessibilidade herdado podem aceitar o uso do controle do código-fonte herdado definindo explicitamente essa opção AppContext como `true`.</span><span class="sxs-lookup"><span data-stu-id="7a1b9-111">Applications that target the .NET Framework 4.7.2 or later, and want to preserve the legacy behavior can opt in to the use of the legacy source control value by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="7a1b9-112">Name</span><span class="sxs-lookup"><span data-stu-id="7a1b9-112">Name</span></span>    | <span data-ttu-id="7a1b9-113">Valor</span><span class="sxs-lookup"><span data-stu-id="7a1b9-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7a1b9-114">Escopo</span><span class="sxs-lookup"><span data-stu-id="7a1b9-114">Scope</span></span>   | <span data-ttu-id="7a1b9-115">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="7a1b9-115">Edge</span></span>        |
| <span data-ttu-id="7a1b9-116">Versão</span><span class="sxs-lookup"><span data-stu-id="7a1b9-116">Version</span></span> | <span data-ttu-id="7a1b9-117">4.7.2</span><span class="sxs-lookup"><span data-stu-id="7a1b9-117">4.7.2</span></span>       |
| <span data-ttu-id="7a1b9-118">Type</span><span class="sxs-lookup"><span data-stu-id="7a1b9-118">Type</span></span>    | <span data-ttu-id="7a1b9-119">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="7a1b9-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="7a1b9-120">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="7a1b9-120">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>
