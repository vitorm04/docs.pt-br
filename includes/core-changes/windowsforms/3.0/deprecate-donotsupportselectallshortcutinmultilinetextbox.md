---
ms.openlocfilehash: bba74f26eafd52b966928835d5003d03af1eabdc
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720888"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="30ee3-101">Não há suporte para a opção de compatibilidade DoNotSupportSelectAllShortcutInMultilineTextBox</span><span class="sxs-lookup"><span data-stu-id="30ee3-101">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="30ee3-102">A `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` opção de compatibilidade, que foi introduzida no .NET Framework 4.6.1, não tem suporte no Windows Forms no .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="30ee3-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="30ee3-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="30ee3-103">Change description</span></span>

<span data-ttu-id="30ee3-104">Começando com .NET Framework 4.6.1, selecionando a tecla <kbd>Ctrl</kbd>  +  <kbd>de</kbd> atalho em um <xref:System.Windows.Forms.TextBox> controle selecionar todo o texto.</span><span class="sxs-lookup"><span data-stu-id="30ee3-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="30ee3-105">No .NET Framework 4,6 e versões anteriores, a seleção da tecla <kbd>Ctrl</kbd>  +  <kbd>a</kbd> shortcut key falhou em selecionar todo o texto se as propriedades [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) e <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> foram ambas definidas como `true` .</span><span class="sxs-lookup"><span data-stu-id="30ee3-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="30ee3-106">A `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` opção de compatibilidade foi introduzida no .NET Framework 4.6.1 para manter o comportamento original.</span><span class="sxs-lookup"><span data-stu-id="30ee3-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="30ee3-107">Para obter mais informações, consulte <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="30ee3-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="30ee3-108">No .NET Core, `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` não há suporte para a opção.</span><span class="sxs-lookup"><span data-stu-id="30ee3-108">In .NET Core, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="30ee3-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="30ee3-109">Version introduced</span></span>

<span data-ttu-id="30ee3-110">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="30ee3-110">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="30ee3-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="30ee3-111">Recommended action</span></span>

<span data-ttu-id="30ee3-112">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="30ee3-112">Remove the switch.</span></span> <span data-ttu-id="30ee3-113">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="30ee3-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="30ee3-114">Categoria</span><span class="sxs-lookup"><span data-stu-id="30ee3-114">Category</span></span>

<span data-ttu-id="30ee3-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="30ee3-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="30ee3-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="30ee3-116">Affected APIs</span></span>

- <span data-ttu-id="30ee3-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="30ee3-117">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
