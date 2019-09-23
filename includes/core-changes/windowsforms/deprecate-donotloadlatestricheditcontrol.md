---
ms.openlocfilehash: 265fc5bea97bf85bcb9cc8111f915e14297d9957
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181864"
---
### <a name="switchsystemwindowsformsdonotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="74270-101">Não há suporte para a opção de compatibilidade switch. System. Windows. Forms. DoNotLoadLatestRichEditControl</span><span class="sxs-lookup"><span data-stu-id="74270-101">Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="74270-102">A `Switch.System.Windows.Forms.UseLegacyImages` opção de compatibilidade, que foi introduzida no .NET Framework 4.7.1, não tem suporte no Windows Forms no .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="74270-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="74270-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="74270-103">Change description</span></span>

<span data-ttu-id="74270-104">No .NET Framework 4.6.2 e versões anteriores, o <xref:System.Windows.Forms.RichTextBox> controle criaria uma instância do controle RichEdit do Win32 v 3.0 e para aplicativos direcionados .NET Framework 4.7.1, o controle criaria uma instância do <xref:System.Windows.Forms.RichTextBox> RichEdit v 4.1 (no  *MsftEdit. dll*).</span><span class="sxs-lookup"><span data-stu-id="74270-104">In the .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control would instantiate the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control would instantiate RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="74270-105">A `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` opção de compatibilidade foi introduzida para permitir aplicativos direcionados .NET Framework 4.7.1 e versões posteriores para recusar o novo controle RichEdit v 4.1 e usar o antigo controle RichEdit v3.</span><span class="sxs-lookup"><span data-stu-id="74270-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt-out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="74270-106">No .NET Core, não `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` há suporte para a opção.</span><span class="sxs-lookup"><span data-stu-id="74270-106">In .NET Core, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="74270-107">Há suporte apenas para novas <xref:System.Windows.Forms.RichTextBox> versões do controle.</span><span class="sxs-lookup"><span data-stu-id="74270-107">Only new versions of the  <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="74270-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="74270-108">Version introduced</span></span>

<span data-ttu-id="74270-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="74270-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="74270-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="74270-110">Recommended action</span></span>

<span data-ttu-id="74270-111">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="74270-111">Remove the switch.</span></span> <span data-ttu-id="74270-112">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="74270-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="74270-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="74270-113">Category</span></span>

<span data-ttu-id="74270-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="74270-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="74270-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="74270-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
