---
title: Como associar a um método
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
ms.openlocfilehash: 58e243812f9c2dcb65dc37bfd50d9bcfb124e4f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-to-a-method"></a>Como associar a um método
O exemplo a seguir mostra como associar a um método usando <xref:System.Windows.Data.ObjectDataProvider>.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, `TemperatureScale` é uma classe que tem um método `ConvertTemp`, que usa dois parâmetros (um do tipo `double` e outro do tipo `enum` `TempType)` e converte o valor dado de uma escala de temperatura em outra. No exemplo a seguir, uma <xref:System.Windows.Data.ObjectDataProvider> é usado para instanciar o `TemperatureScale` objeto. O método `ConvertTemp` é chamado com dois parâmetros especificados.  
  
 [!code-xaml[BindToMethod#WindowResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 Agora que o método está disponível como um recurso, é possível associar aos seus resultados. No exemplo a seguir, o <xref:System.Windows.Controls.TextBox.Text%2A> propriedade o <xref:System.Windows.Controls.TextBox> e o <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> do <xref:System.Windows.Controls.ComboBox> estão associados aos dois parâmetros do método. Isso permite que os usuários especifiquem a temperatura a ser convertida e a escala de conversão. Observe que <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> é definido como `true` porque estamos ligando o <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> propriedade do <xref:System.Windows.Data.ObjectDataProvider> instância e não propriedades do objeto encapsulados pelo <xref:System.Windows.Data.ObjectDataProvider> (o `TemperatureScale` objeto).  
  
 O <xref:System.Windows.Controls.ContentControl.Content%2A> da última <xref:System.Windows.Controls.Label> atualiza quando o usuário modifica o conteúdo do <xref:System.Windows.Controls.TextBox> ou a seleção do <xref:System.Windows.Controls.ComboBox>.  
  
 [!code-xaml[BindToMethod#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 O conversor `DoubleToString` usa double e a transforma em uma cadeia de caracteres a <xref:System.Windows.Data.IValueConverter.Convert%2A> direção (da fonte de associação para o destino da associação, que é o <xref:System.Windows.Controls.TextBox.Text%2A> propriedade) e converte um `string` para um `double` no <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> direção.  
  
 O `InvalidationCharacterRule` é um <xref:System.Windows.Controls.ValidationRule> que verifica se há caracteres inválidos. O modelo de erro padrão, que é uma borda vermelha ao redor do <xref:System.Windows.Controls.TextBox>, é exibido notificar os usuários quando o valor de entrada não é um valor duplo.  
  
## <a name="see-also"></a>Consulte também  
 [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [Associar a uma enumeração](../../../../docs/framework/wpf/data/how-to-bind-to-an-enumeration.md)
