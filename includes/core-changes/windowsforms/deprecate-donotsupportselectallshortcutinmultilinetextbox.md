---
ms.openlocfilehash: a9d0fe3516ade04bc38b804268a9d989f6891d80
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181854"
---
### <a name="switchsystemwindowsformsdonotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="28677-101">Não há suporte para a opção de compatibilidade switch. System. Windows. Forms. DoNotSupportSelectAllShortcutInMultilineTextBox</span><span class="sxs-lookup"><span data-stu-id="28677-101">Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="28677-102">A `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` opção de compatibilidade, que foi introduzida no .NET Framework 4.6.1, não tem suporte no Windows Forms no .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="28677-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="28677-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="28677-103">Change description</span></span>

<span data-ttu-id="28677-104">Começando com .NET Framework 4.6.1, selecionando a tecla <kbd>Ctrl</kbd> + <kbd>de atalho</kbd> em <xref:System.Windows.Forms.TextBox> um controle selecionar todo o texto.</span><span class="sxs-lookup"><span data-stu-id="28677-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="28677-105">No .NET Framework 4,6 e versões anteriores, a seleção <kbd></kbd> + <kbd>da tecla CTRL a shortcut key</kbd> falhou em selecionar todo o texto se as propriedades <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) e foram `true`ambas definidas como.</span><span class="sxs-lookup"><span data-stu-id="28677-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="28677-106">A `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` opção de compatibilidade foi introduzida no .NET Framework 4.6.1 para manter o comportamento original.</span><span class="sxs-lookup"><span data-stu-id="28677-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="28677-107">Para obter mais informações, consulte <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="28677-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="28677-108">No .NET Core, não `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` há suporte para a opção.</span><span class="sxs-lookup"><span data-stu-id="28677-108">In .NET Core, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="28677-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="28677-109">Version introduced</span></span>

<span data-ttu-id="28677-110">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="28677-110">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="28677-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="28677-111">Recommended action</span></span>

<span data-ttu-id="28677-112">Remova a opção.</span><span class="sxs-lookup"><span data-stu-id="28677-112">Remove the switch.</span></span> <span data-ttu-id="28677-113">Não há suporte para a opção e nenhuma funcionalidade alternativa está disponível.</span><span class="sxs-lookup"><span data-stu-id="28677-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="28677-114">Categoria</span><span class="sxs-lookup"><span data-stu-id="28677-114">Category</span></span>

<span data-ttu-id="28677-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="28677-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="28677-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="28677-116">Affected APIs</span></span>

- <span data-ttu-id="28677-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="28677-117">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
