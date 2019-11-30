---
ms.openlocfilehash: 265fc5bea97bf85bcb9cc8111f915e14297d9957
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643980"
---
### <a name="switchsystemwindowsformsdonotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="eed7c-101">Não há suporte para a opção de compatibilidade switch. System. Windows. Forms. DoNotLoadLatestRichEditControl</span><span class="sxs-lookup"><span data-stu-id="eed7c-101">Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="eed7c-102">O `Switch.System.Windows.Forms.UseLegacyImages` opção de compatibilidade, que foi introduzido no .NET Framework 4.7.1, não tem suporte no Windows Forms no .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="eed7c-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="eed7c-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="eed7c-103">Change description</span></span>

<span data-ttu-id="eed7c-104">No .NET Framework 4.6.2 e versões anteriores, o controle de <xref:System.Windows.Forms.RichTextBox> instanciaria o controle RichEdit do Win32 v 3.0 e, para aplicativos direcionados .NET Framework 4.7.1, o controle de <xref:System.Windows.Forms.RichTextBox> instanciaria o RichEdit v 4.1 (em *MsftEdit. dll*).</span><span class="sxs-lookup"><span data-stu-id="eed7c-104">In the .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control would instantiate the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control would instantiate RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="eed7c-105">A opção de compatibilidade `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` foi introduzida para permitir aplicativos direcionados .NET Framework 4.7.1 e versões posteriores para recusar o novo controle RichEdit v 4.1 e usar o antigo controle RichEdit v3.</span><span class="sxs-lookup"><span data-stu-id="eed7c-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt-out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="eed7c-106">No .NET Core, não há suporte para a opção `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`.</span><span class="sxs-lookup"><span data-stu-id="eed7c-106">In .NET Core, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="eed7c-107">Há suporte apenas para novas versões do controle de <xref:System.Windows.Forms.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="eed7c-107">Only new versions of the  <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="eed7c-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="eed7c-108">Version introduced</span></span>

<span data-ttu-id="eed7c-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="eed7c-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="eed7c-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="eed7c-110">Recommended action</span></span>

<span data-ttu-id="eed7c-111">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="eed7c-111">Remove the switch.</span></span> <span data-ttu-id="eed7c-112">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="eed7c-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="eed7c-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="eed7c-113">Category</span></span>

<span data-ttu-id="eed7c-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eed7c-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="eed7c-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="eed7c-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
