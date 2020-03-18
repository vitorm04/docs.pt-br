---
ms.openlocfilehash: 9631e64bb403a3fe7b1b91e8ac592b57ce8068d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936991"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="a4c07-101">DoNotSupportSelect$ShortcutInMultilineTextBox não é suportado</span><span class="sxs-lookup"><span data-stu-id="a4c07-101">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="a4c07-102">O `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch de compatibilidade, que foi introduzido no .NET Framework 4.6.1, não é suportado no Windows Forms no .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="a4c07-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a4c07-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="a4c07-103">Change description</span></span>

<span data-ttu-id="a4c07-104">Começando com o Quadro .NET 4.6.1, selecionando <xref:System.Windows.Forms.TextBox> a tecla De atalho <kbd>Ctrl</kbd> + <kbd>A</kbd> em um controle selecionou todo o texto.</span><span class="sxs-lookup"><span data-stu-id="a4c07-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="a4c07-105">Nas versões .NET Framework 4.6 e anteriores, a seleção da tecla <kbd>Ctrl</kbd> + <kbd>A</kbd> não conseguiu selecionar todo o texto se a caixa [de texto.atalhoshabilitados](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) e <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> as propriedades foram definidas como `true`.</span><span class="sxs-lookup"><span data-stu-id="a4c07-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="a4c07-106">O `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch de compatibilidade foi introduzido no .NET Framework 4.6.1 para manter o comportamento original.</span><span class="sxs-lookup"><span data-stu-id="a4c07-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="a4c07-107">Para obter mais informações, consulte <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a4c07-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="a4c07-108">No .NET Core, o `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch não é suportado.</span><span class="sxs-lookup"><span data-stu-id="a4c07-108">In .NET Core, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a4c07-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="a4c07-109">Version introduced</span></span>

<span data-ttu-id="a4c07-110">3.0 Visualização 9</span><span class="sxs-lookup"><span data-stu-id="a4c07-110">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a4c07-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="a4c07-111">Recommended action</span></span>

<span data-ttu-id="a4c07-112">Remova o interruptor.</span><span class="sxs-lookup"><span data-stu-id="a4c07-112">Remove the switch.</span></span> <span data-ttu-id="a4c07-113">O switch não é suportado e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="a4c07-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="a4c07-114">Categoria</span><span class="sxs-lookup"><span data-stu-id="a4c07-114">Category</span></span>

<span data-ttu-id="a4c07-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a4c07-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a4c07-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="a4c07-116">Affected APIs</span></span>

- <span data-ttu-id="a4c07-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a4c07-117">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
