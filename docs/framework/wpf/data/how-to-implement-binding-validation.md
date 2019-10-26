---
title: Como implementar validação de associação
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 7a1a8df78a785066992472c7de37f958ae3467f1
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920164"
---
# <a name="how-to-implement-binding-validation"></a><span data-ttu-id="39260-102">Como implementar validação de associação</span><span class="sxs-lookup"><span data-stu-id="39260-102">How to: Implement Binding Validation</span></span>

<span data-ttu-id="39260-103">Este exemplo mostra como usar um <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> e um gatilho de estilo para fornecer comentários visuais para informar o usuário quando um valor inválido é inserido, com base em uma regra de validação personalizada.</span><span class="sxs-lookup"><span data-stu-id="39260-103">This example shows how to use an <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> and a style trigger to provide visual feedback to inform the user when an invalid value is entered, based on a custom validation rule.</span></span>

## <a name="example"></a><span data-ttu-id="39260-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="39260-104">Example</span></span>

<span data-ttu-id="39260-105">O conteúdo de texto do <xref:System.Windows.Controls.TextBox> no exemplo a seguir é associado à propriedade `Age` (do tipo int) de um objeto de origem de associação chamado `ods`.</span><span class="sxs-lookup"><span data-stu-id="39260-105">The text content of the <xref:System.Windows.Controls.TextBox> in the following example is bound to the `Age` property (of type int) of a binding source object named `ods`.</span></span> <span data-ttu-id="39260-106">A associação é configurada para usar uma regra de validação chamada `AgeRangeRule` para que, se o usuário inserir caracteres não numéricos ou um valor menor que 21 ou maior que 130, um ponto de exclamação vermelho apareça ao lado da caixa de texto e uma dica de ferramenta com a mensagem de erro seja exibida quando o usuário move o mouse sobre a caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="39260-106">The binding is set up to use a validation rule named `AgeRangeRule` so that if the user enters non-numeric characters or a value that is smaller than 21 or greater than 130, a red exclamation mark appears next to the text box and a tool tip with the error message appears when the user moves the mouse over the text box.</span></span>

[!code-xaml[BindValidation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]

<span data-ttu-id="39260-107">O exemplo a seguir mostra a implementação de `AgeRangeRule`, que herda de <xref:System.Windows.Controls.ValidationRule> e substitui o método <xref:System.Windows.Controls.ValidationRule.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="39260-107">The following example shows the implementation of `AgeRangeRule`, which inherits from <xref:System.Windows.Controls.ValidationRule> and overrides the <xref:System.Windows.Controls.ValidationRule.Validate%2A> method.</span></span> <span data-ttu-id="39260-108">O método `Int32.Parse` é chamado no valor para garantir que ele não contenha caracteres inválidos.</span><span class="sxs-lookup"><span data-stu-id="39260-108">The `Int32.Parse` method is called on the value to make sure that it does not contain any invalid characters.</span></span> <span data-ttu-id="39260-109">O método <xref:System.Windows.Controls.ValidationRule.Validate%2A> retorna um <xref:System.Windows.Controls.ValidationResult> que indica se o valor é válido com base em se uma exceção é detectada durante a análise e se o valor de idade está fora dos limites inferior e superior.</span><span class="sxs-lookup"><span data-stu-id="39260-109">The <xref:System.Windows.Controls.ValidationRule.Validate%2A> method returns a <xref:System.Windows.Controls.ValidationResult> that indicates if the value is valid based on whether an exception is caught during the parsing and whether the age value is outside of the lower and upper bounds.</span></span>

[!code-csharp[BindValidation#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]
[!code-vb[BindValidation#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindValidation/VisualBasic/AgeRangeRule.vb#3)]

<span data-ttu-id="39260-110">O exemplo a seguir mostra o `validationTemplate` de <xref:System.Windows.Controls.ControlTemplate> personalizado que cria um ponto de exclamação vermelho para notificar o usuário sobre um erro de validação.</span><span class="sxs-lookup"><span data-stu-id="39260-110">The following example shows the custom <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` that creates a red exclamation mark to notify the user of a validation error.</span></span> <span data-ttu-id="39260-111">Modelos de controle são usados para redefinir a aparência de um controle.</span><span class="sxs-lookup"><span data-stu-id="39260-111">Control templates are used to redefine the appearance of a control.</span></span>

[!code-xaml[BindValidation#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]

<span data-ttu-id="39260-112">Conforme mostrado no exemplo a seguir, a <xref:System.Windows.Controls.ToolTip> que mostra a mensagem de erro é criada usando o estilo chamado `textBoxInError`.</span><span class="sxs-lookup"><span data-stu-id="39260-112">As shown in the following example, the <xref:System.Windows.Controls.ToolTip> that shows the error message is created using the style named `textBoxInError`.</span></span> <span data-ttu-id="39260-113">Se o valor de <xref:System.Windows.Controls.Validation.HasError%2A> for `true`, o gatilho definirá a dica de ferramenta da <xref:System.Windows.Controls.TextBox> atual como seu primeiro erro de validação.</span><span class="sxs-lookup"><span data-stu-id="39260-113">If the value of <xref:System.Windows.Controls.Validation.HasError%2A> is `true`, the trigger sets the tool tip of the current <xref:System.Windows.Controls.TextBox> to its first validation error.</span></span> <span data-ttu-id="39260-114">O <xref:System.Windows.Data.Binding.RelativeSource%2A> é definido como <xref:System.Windows.Data.RelativeSourceMode.Self>, referindo-se ao elemento atual.</span><span class="sxs-lookup"><span data-stu-id="39260-114">The <xref:System.Windows.Data.Binding.RelativeSource%2A> is set to <xref:System.Windows.Data.RelativeSourceMode.Self>, referring to the current element.</span></span>

[!code-xaml[BindValidation#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]

<span data-ttu-id="39260-115">Para obter o exemplo completo, consulte [exemplo de validação de associação](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).</span><span class="sxs-lookup"><span data-stu-id="39260-115">For the complete example, see [Bind Validation sample](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).</span></span>
  
<span data-ttu-id="39260-116">Observe que, se você não fornecer um <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> personalizado, o modelo de erro padrão será exibido para fornecer comentários visuais ao usuário quando houver um erro de validação.</span><span class="sxs-lookup"><span data-stu-id="39260-116">Note that if you do not provide a custom <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> the default error template appears to provide visual feedback to the user when there is a validation error.</span></span> <span data-ttu-id="39260-117">Consulte “Validação de dados” na [Visão geral de associação de dados](data-binding-overview.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="39260-117">See "Data Validation" in [Data Binding Overview](data-binding-overview.md) for more information.</span></span> <span data-ttu-id="39260-118">Além disso, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece uma regra de validação interna que captura exceções que são geradas durante a atualização da propriedade de origem de associação.</span><span class="sxs-lookup"><span data-stu-id="39260-118">Also, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provides a built-in validation rule that catches exceptions that are thrown during the update of the binding source property.</span></span> <span data-ttu-id="39260-119">Para obter mais informações, consulte <xref:System.Windows.Controls.ExceptionValidationRule>.</span><span class="sxs-lookup"><span data-stu-id="39260-119">For more information, see <xref:System.Windows.Controls.ExceptionValidationRule>.</span></span>

## <a name="see-also"></a><span data-ttu-id="39260-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39260-120">See also</span></span>

- [<span data-ttu-id="39260-121">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="39260-121">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="39260-122">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="39260-122">How-to Topics</span></span>](data-binding-how-to-topics.md)
