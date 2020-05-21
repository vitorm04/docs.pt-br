---
ms.openlocfilehash: cb8c0532bb2bcfbcd619cd382f3d236b431c3480
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720989"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="408c6-101">Não há suporte para a opção de compatibilidade DoNotLoadLatestRichEditControl</span><span class="sxs-lookup"><span data-stu-id="408c6-101">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="408c6-102">A `Switch.System.Windows.Forms.UseLegacyImages` opção de compatibilidade, que foi introduzida no .NET Framework 4.7.1, não tem suporte no Windows Forms no .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="408c6-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="408c6-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="408c6-103">Change description</span></span>

<span data-ttu-id="408c6-104">No .NET Framework 4.6.2 e versões anteriores, o <xref:System.Windows.Forms.RichTextBox> controle criaria uma instância do controle RichEdit do Win32 v 3.0 e, para aplicativos direcionados .NET Framework 4.7.1, o <xref:System.Windows.Forms.RichTextBox> controle criaria uma instância de RichEdit v 4.1 (em *MsftEdit. dll*).</span><span class="sxs-lookup"><span data-stu-id="408c6-104">In the .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control would instantiate the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control would instantiate RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="408c6-105">A `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` opção de compatibilidade foi introduzida para permitir aplicativos direcionados .NET Framework 4.7.1 e versões posteriores para recusar o novo controle RichEdit v 4.1 e usar o antigo controle RichEdit v3.</span><span class="sxs-lookup"><span data-stu-id="408c6-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt-out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="408c6-106">No .NET Core, `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` não há suporte para a opção.</span><span class="sxs-lookup"><span data-stu-id="408c6-106">In .NET Core, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="408c6-107">Há suporte apenas para novas versões do <xref:System.Windows.Forms.RichTextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="408c6-107">Only new versions of the  <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="408c6-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="408c6-108">Version introduced</span></span>

<span data-ttu-id="408c6-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="408c6-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="408c6-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="408c6-110">Recommended action</span></span>

<span data-ttu-id="408c6-111">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="408c6-111">Remove the switch.</span></span> <span data-ttu-id="408c6-112">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="408c6-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="408c6-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="408c6-113">Category</span></span>

<span data-ttu-id="408c6-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="408c6-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="408c6-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="408c6-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

#### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
