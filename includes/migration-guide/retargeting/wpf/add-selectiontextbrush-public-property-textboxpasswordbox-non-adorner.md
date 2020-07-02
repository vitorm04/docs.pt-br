---
ms.openlocfilehash: aade03c29ff16053a97683499cf719a98ae33f3f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617782"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a><span data-ttu-id="ae0a4-101">Adicionar a propriedade pública SelectionTextBrush à seleção não baseada em adorno TextBox/PasswordBox</span><span class="sxs-lookup"><span data-stu-id="ae0a4-101">Add SelectionTextBrush public property to TextBox/PasswordBox non-adorner selection</span></span>

#### <a name="details"></a><span data-ttu-id="ae0a4-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ae0a4-102">Details</span></span>

<span data-ttu-id="ae0a4-103">Em aplicativos do WPF que usam a [seleção de texto não baseada em adorno](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) para <xref:System.Windows.Controls.TextBox> e <xref:System.Windows.Controls.PasswordBox>, os desenvolvedores podem agora definir a propriedade SelectionTextBrush recém-adicionada para alterar a renderização do texto selecionado.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-103">In WPF applications using [non-adorner based text selection](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) for <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox>, developers may now set the newly added SelectionTextBrush property in order to alter the rendering of the selected text.</span></span>  <span data-ttu-id="ae0a4-104">Por padrão, essa cor é alterada com <xref:System.Windows.SystemColors.HighlightTextBrushKey>.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-104">By default, this color changes with <xref:System.Windows.SystemColors.HighlightTextBrushKey>.</span></span>  <span data-ttu-id="ae0a4-105">Se a seleção de texto não baseada em adorno não estiver habilitada, essa propriedade não fará nada.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-105">If non-adorner based text selection is not enabled, this property does nothing.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ae0a4-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="ae0a4-106">Suggestion</span></span>

<span data-ttu-id="ae0a4-107">Depois que a seleção de texto não baseada em adorno estiver habilitada, será possível usar a propriedade <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> e <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> para alterar a aparência do texto selecionado.</span><span class="sxs-lookup"><span data-stu-id="ae0a4-107">Once non-adorner based text selection is enabled, you can use the <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> and <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> property to change the appearance of the selected text.</span></span> <span data-ttu-id="ae0a4-108">Isso pode ser feito usando XAML:</span><span class="sxs-lookup"><span data-stu-id="ae0a4-108">This can be achieved using XAML:</span></span>

<pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="ae0a4-109">Name</span><span class="sxs-lookup"><span data-stu-id="ae0a4-109">Name</span></span>    | <span data-ttu-id="ae0a4-110">Valor</span><span class="sxs-lookup"><span data-stu-id="ae0a4-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ae0a4-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="ae0a4-111">Scope</span></span>   | <span data-ttu-id="ae0a4-112">Principal</span><span class="sxs-lookup"><span data-stu-id="ae0a4-112">Major</span></span>       |
| <span data-ttu-id="ae0a4-113">Versão</span><span class="sxs-lookup"><span data-stu-id="ae0a4-113">Version</span></span> | <span data-ttu-id="ae0a4-114">4.8</span><span class="sxs-lookup"><span data-stu-id="ae0a4-114">4.8</span></span>         |
| <span data-ttu-id="ae0a4-115">Type</span><span class="sxs-lookup"><span data-stu-id="ae0a4-115">Type</span></span>    | <span data-ttu-id="ae0a4-116">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="ae0a4-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="ae0a4-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ae0a4-117">Affected APIs</span></span>

- <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType>
- [<span data-ttu-id="ae0a4-118">System.Windows.Controls.TextBox</span><span class="sxs-lookup"><span data-stu-id="ae0a4-118">System.Windows.Controls.TextBox</span></span>](xref:System.Windows.Controls.TextBox)
- [<span data-ttu-id="ae0a4-119">System.Windows.Controls.PasswordBox</span><span class="sxs-lookup"><span data-stu-id="ae0a4-119">System.Windows.Controls.PasswordBox</span></span>](xref:System.Windows.Controls.PasswordBox)
