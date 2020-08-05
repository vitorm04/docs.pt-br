---
ms.openlocfilehash: d3bfeda8309af83d8e4199999ed91263a17caeea
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556128"
---
### <a name="removed-status-bar-controls"></a><span data-ttu-id="81c84-101">Controles da barra de status removidos</span><span class="sxs-lookup"><span data-stu-id="81c84-101">Removed status bar controls</span></span>

<span data-ttu-id="81c84-102">A partir do .NET 5,0, alguns controles Windows Forms não estão mais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="81c84-102">Starting in .NET 5.0, some Windows Forms controls are no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="81c84-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="81c84-103">Change description</span></span>

<span data-ttu-id="81c84-104">A partir do .NET 5,0, alguns dos controles de Windows Forms relacionados à barra de status não estão mais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="81c84-104">Starting with .NET 5.0, some of the status bar-related Windows Forms controls are no longer available.</span></span> <span data-ttu-id="81c84-105">Os controles de substituição com design e suporte melhores foram introduzidos no .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="81c84-105">Replacement controls that have better design and support were introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="81c84-106">Os controles preteridos foram removidos anteriormente das caixas de ferramentas do designer, mas ainda estavam disponíveis para serem usados.</span><span class="sxs-lookup"><span data-stu-id="81c84-106">The deprecated controls were previously removed from designer toolboxes but were still available to be used.</span></span> <span data-ttu-id="81c84-107">Agora, eles foram completamente removidos.</span><span class="sxs-lookup"><span data-stu-id="81c84-107">Now, they have been completely removed.</span></span>

<span data-ttu-id="81c84-108">Os seguintes tipos não estão mais disponíveis:</span><span class="sxs-lookup"><span data-stu-id="81c84-108">The following types are no longer available:</span></span>

* `StatusBar`
* `StatusBarDrawItemEventArgs`
* `StatusBarDrawItemEventHandler`
* `StatusBarPanel`
* `StatusBarPanelAutoSize`
* `StatusBarPanelBorderStyle`
* `StatusBarPanelClickEventArgs`
* `StatusBarPanelClickEventHandler`
* `StatusBarPanelStyle`

#### <a name="version-introduced"></a><span data-ttu-id="81c84-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="81c84-109">Version introduced</span></span>

<span data-ttu-id="81c84-110">5,0 visualização 1</span><span class="sxs-lookup"><span data-stu-id="81c84-110">5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="81c84-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="81c84-111">Recommended action</span></span>

<span data-ttu-id="81c84-112">Vá para as APIs de substituição para esses controles e seus cenários:</span><span class="sxs-lookup"><span data-stu-id="81c84-112">Move to the replacement APIs for these controls and their scenarios:</span></span>

| <span data-ttu-id="81c84-113">Controle antigo (API)</span><span class="sxs-lookup"><span data-stu-id="81c84-113">Old Control (API)</span></span> | <span data-ttu-id="81c84-114">Substituição recomendada</span><span class="sxs-lookup"><span data-stu-id="81c84-114">Recommended Replacement</span></span>                          |
|-------------------|--------------------------------------------------|
| <span data-ttu-id="81c84-115">StatusBar</span><span class="sxs-lookup"><span data-stu-id="81c84-115">StatusBar</span></span>         | <xref:System.Windows.Forms.StatusStrip>          |
| <span data-ttu-id="81c84-116">StatusBarPanel</span><span class="sxs-lookup"><span data-stu-id="81c84-116">StatusBarPanel</span></span>    | <xref:System.Windows.Forms.ToolStripStatusLabel> |

#### <a name="category"></a><span data-ttu-id="81c84-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="81c84-117">Category</span></span>

<span data-ttu-id="81c84-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="81c84-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="81c84-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="81c84-119">Affected APIs</span></span>

- <xref:System.Windows.Forms.StatusBar?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanel?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelAutoSize?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelBorderStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelStyle?displayProperty=fullName>

<!-- 

#### Affected APIs

- `T:System.Windows.Forms.StatusBar`
- `T:System.Windows.Forms.StatusBarDrawItemEventArgs`
- `T:System.Windows.Forms.StatusBarDrawItemEventHandler`
- `T:System.Windows.Forms.StatusBarPanel`
- `T:System.Windows.Forms.StatusBarPanelAutoSize`
- `T:System.Windows.Forms.StatusBarPanelBorderStyle`
- `T:System.Windows.Forms.StatusBarPanelClickEventArgs`
- `T:System.Windows.Forms.StatusBarPanelClickEventHandler`
- `T:System.Windows.Forms.StatusBarPanelStyle` 

-->
