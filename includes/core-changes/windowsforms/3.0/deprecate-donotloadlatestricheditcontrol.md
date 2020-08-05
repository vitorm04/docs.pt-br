---
ms.openlocfilehash: e10b5168d59edd56ff549a3a1e3a09d023fe5e28
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556121"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="72579-101">Não há suporte para a opção de compatibilidade DoNotLoadLatestRichEditControl</span><span class="sxs-lookup"><span data-stu-id="72579-101">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="72579-102">A `Switch.System.Windows.Forms.UseLegacyImages` opção de compatibilidade, que foi introduzida no .NET Framework 4.7.1, não tem suporte no Windows Forms no .NET Core ou no .net 5,0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="72579-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="72579-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="72579-103">Change description</span></span>

<span data-ttu-id="72579-104">No .NET Framework 4.6.2 e versões anteriores, o <xref:System.Windows.Forms.RichTextBox> controle instancia o controle RichEdit do Win32 v 3.0 e, para aplicativos direcionados .NET Framework 4.7.1, o <xref:System.Windows.Forms.RichTextBox> controle instancia o RichEdit v 4.1 (em *msftedit.dll*).</span><span class="sxs-lookup"><span data-stu-id="72579-104">In .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control instantiates the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control instantiates RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="72579-105">A `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` opção de compatibilidade foi introduzida para permitir aplicativos direcionados .NET Framework 4.7.1 e versões posteriores para recusar o novo controle RichEdit v 4.1 e usar o antigo controle RichEdit v3.</span><span class="sxs-lookup"><span data-stu-id="72579-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="72579-106">No .NET Core e no .NET 5,0 e versões posteriores, `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` não há suporte para a opção.</span><span class="sxs-lookup"><span data-stu-id="72579-106">In .NET Core and .NET 5.0 and later versions, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="72579-107">Há suporte apenas para novas versões do <xref:System.Windows.Forms.RichTextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="72579-107">Only new versions of the <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="72579-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="72579-108">Version introduced</span></span>

<span data-ttu-id="72579-109">3.0</span><span class="sxs-lookup"><span data-stu-id="72579-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="72579-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="72579-110">Recommended action</span></span>

<span data-ttu-id="72579-111">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="72579-111">Remove the switch.</span></span> <span data-ttu-id="72579-112">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="72579-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="72579-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="72579-113">Category</span></span>

<span data-ttu-id="72579-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="72579-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="72579-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="72579-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

#### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
