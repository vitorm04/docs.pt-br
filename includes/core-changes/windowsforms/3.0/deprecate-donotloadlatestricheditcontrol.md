---
ms.openlocfilehash: 3f0e8fb4d0d727b40cff5de7cfdc7529bf32dac4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937010"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="fa99b-101">DoNotLoadLastRichEditO switch de compatibilidade não suportado</span><span class="sxs-lookup"><span data-stu-id="fa99b-101">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="fa99b-102">O `Switch.System.Windows.Forms.UseLegacyImages` switch de compatibilidade, que foi introduzido no .NET Framework 4.7.1, não é suportado no Windows Forms no .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="fa99b-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="fa99b-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="fa99b-103">Change description</span></span>

<span data-ttu-id="fa99b-104">No Quadro .NET 4.6.2 e <xref:System.Windows.Forms.RichTextBox> nas versões anteriores, o controle instanciaria o controle Win32 RichEdit v3.0, e para aplicativos que visam o .NET Framework 4.7.1, o <xref:System.Windows.Forms.RichTextBox> controle instanciaria RichEdit v4.1 (in *msftedit.dll*).</span><span class="sxs-lookup"><span data-stu-id="fa99b-104">In the .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control would instantiate the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control would instantiate RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="fa99b-105">O `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch de compatibilidade foi introduzido para permitir que aplicativos que visam as versões .NET Framework 4.7.1 e posteriores optem pelo novo controle RichEdit v4.1 e usem o antigo controle RichEdit v3.</span><span class="sxs-lookup"><span data-stu-id="fa99b-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt-out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="fa99b-106">No .NET Core, o `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch não é suportado.</span><span class="sxs-lookup"><span data-stu-id="fa99b-106">In .NET Core, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="fa99b-107">Apenas novas versões do <xref:System.Windows.Forms.RichTextBox> controle são suportadas.</span><span class="sxs-lookup"><span data-stu-id="fa99b-107">Only new versions of the  <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fa99b-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="fa99b-108">Version introduced</span></span>

<span data-ttu-id="fa99b-109">3.0 Visualização 9</span><span class="sxs-lookup"><span data-stu-id="fa99b-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fa99b-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="fa99b-110">Recommended action</span></span>

<span data-ttu-id="fa99b-111">Remova o interruptor.</span><span class="sxs-lookup"><span data-stu-id="fa99b-111">Remove the switch.</span></span> <span data-ttu-id="fa99b-112">O switch não é suportado e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="fa99b-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="fa99b-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="fa99b-113">Category</span></span>

<span data-ttu-id="fa99b-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fa99b-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fa99b-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="fa99b-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
