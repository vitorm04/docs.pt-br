---
title: 'Como: Implementar validação de associação'
ms.date: 03/30/2017
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: eefdb3b1205a64221e3e9352f70e3d06dc074eff
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368539"
---
# <a name="how-to-implement-binding-validation"></a>Como: Implementar validação de associação
Este exemplo mostra como usar um <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> e um gatilho de estilo para fornecer comentários visuais para informar ao usuário quando um valor inválido é inserido, com base em uma regra de validação personalizada.  
  
## <a name="example"></a>Exemplo  
 Conteúdo de texto a <xref:System.Windows.Controls.TextBox> no exemplo a seguir está associado a `Age` propriedade (do tipo int) de um objeto de origem da associação chamado `ods`. A associação é configurada para usar uma regra de validação chamada `AgeRangeRule` para que, se o usuário inserir caracteres não numéricos ou um valor menor que 21 ou maior que 130, um ponto de exclamação vermelho apareça ao lado da caixa de texto e uma dica de ferramenta com a mensagem de erro seja exibida quando o usuário move o mouse sobre a caixa de texto.  
  
 [!code-xaml[BindValidation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]  
  
 O exemplo a seguir mostra a implementação de `AgeRangeRule`, que herda de <xref:System.Windows.Controls.ValidationRule> e substitui o <xref:System.Windows.Controls.ValidationRule.Validate%2A> método. O método Int32.Parse() é chamado no valor para verificar se ele não contém caracteres inválidos. O <xref:System.Windows.Controls.ValidationRule.Validate%2A> método retorna um <xref:System.Windows.Controls.ValidationResult> que indica se o valor é válido com base em se uma exceção é detectada durante a análise e se o valor de idade está fora os limites inferior e superior.  
  
 [!code-csharp[BindValidation#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]  
  
 O exemplo a seguir mostra o personalizado <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` que cria um ponto de exclamação vermelho para notificar o usuário de um erro de validação. Modelos de controle são usados para redefinir a aparência de um controle.  
  
 [!code-xaml[BindValidation#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]  
  
 Conforme mostrado no exemplo a seguir, o <xref:System.Windows.Controls.ToolTip> que mostra a mensagem de erro é criada usando o estilo chamado `textBoxInError`. Se o valor de <xref:System.Windows.Controls.Validation.HasError%2A> está `true`, o gatilho define a dica de ferramenta do atual <xref:System.Windows.Controls.TextBox> para seu primeiro erro de validação. O <xref:System.Windows.Data.Binding.RelativeSource%2A> é definido como <xref:System.Windows.Data.RelativeSourceMode.Self>, fazendo referência ao elemento atual.  
  
 [!code-xaml[BindValidation#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]  
  
 Para ver o exemplo completo, consulte [Exemplo de validação de associação](https://go.microsoft.com/fwlink/?LinkID=159972).  
  
 Observe que, se você não fornecer um personalizado <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> o modelo de erro padrão é exibido para fornecer comentários visuais para o usuário quando há um erro de validação. Consulte “Validação de dados” na [Visão geral de associação de dados](data-binding-overview.md) para obter mais informações. Além disso, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece uma regra de validação interna que captura exceções que são geradas durante a atualização da propriedade de origem de associação. Para obter mais informações, consulte <xref:System.Windows.Controls.ExceptionValidationRule>.  
  
## <a name="see-also"></a>Consulte também
- [Visão geral da vinculação de dados](data-binding-overview.md)
- [Tópicos de instruções](data-binding-how-to-topics.md)
