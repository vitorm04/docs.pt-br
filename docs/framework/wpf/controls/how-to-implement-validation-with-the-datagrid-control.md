---
title: Como implementar validação com o controle DataGrid
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], validation
- validation [WPF], DataGrid
ms.assetid: ec6078a8-1e42-4648-b414-f4348e81bda1
ms.openlocfilehash: 38b4c9cd7679f0d8da9b18fb5bd6bb729d33ed54
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646093"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>Como implementar validação com o controle DataGrid
O <xref:System.Windows.Controls.DataGrid> controle permite que você execute a validação tanto no nível da célula quanto da linha. Com a validação no nível da célula, você valida propriedades individuais de um objeto com associação de dados quando um usuário atualiza um valor. Com a validação no nível da linha, você valida objetos de dados inteiros quando um usuário confirma alterações em uma linha. Você também pode fornecer feedback visual personalizado para erros de <xref:System.Windows.Controls.DataGrid> validação ou usar o feedback visual padrão que o controle fornece.  
  
 Os procedimentos a seguir descrevem <xref:System.Windows.Controls.DataGrid> como aplicar regras de validação às vinculações e personalizar o feedback visual.  
  
### <a name="to-validate-individual-cell-values"></a>Para validar valores de células individuais  
  
- Especifique uma ou mais regras de validação para a associação usada com uma coluna. Isso é semelhante à validação de dados em controles simples, conforme descrito em [Visão geral da associação de dados](../../../desktop-wpf/data/data-binding-overview.md).  
  
     O exemplo a <xref:System.Windows.Controls.DataGrid> seguir mostra um controle com quatro colunas vinculadas a diferentes propriedades de um objeto de negócios. Três das colunas <xref:System.Windows.Controls.ExceptionValidationRule> especificam <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> o `true`definindo a propriedade para .  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Quando um usuário insere um valor inválido (como um número não inteiro na coluna de ID do Curso), uma borda vermelha aparece em torno da célula. É possível alterar esses comentários de validação padrão conforme descrito no procedimento a seguir.  
  
### <a name="to-customize-cell-validation-feedback"></a>Para personalizar os comentários de validação de célula  
  
- Defina a <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> propriedade da coluna como um estilo apropriado para o controle de edição da coluna. Como os controles de edição são criados em <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> tempo de execução, você não pode usar a propriedade anexada como faria com controles simples.  
  
     O exemplo a seguir atualiza o exemplo anterior adicionando um estilo de erro compartilhado pelas três colunas com regras de validação. Quando um usuário insere um valor inválido, o estilo altera a cor da tela de fundo da célula e adiciona uma dica de ferramenta. Observe o uso de um gatilho para determinar se há um erro de validação. Isso é necessário porque atualmente não há um modelo de erro dedicado para células.  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Você pode implementar uma personalização <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> mais extensa substituindo a usada pela coluna.  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>Para validar vários valores em uma única linha  
  
1. Implemente <xref:System.Windows.Controls.ValidationRule> uma subclasse que verifique várias propriedades do objeto de dados vinculado. Na <xref:System.Windows.Controls.ValidationRule.Validate%2A> implementação do `value` método, lance <xref:System.Windows.Data.BindingGroup> o valor do parâmetro em uma instância. Em seguida, você pode <xref:System.Windows.Data.BindingGroup.Items%2A> acessar o objeto de dados através da propriedade.  
  
     O exemplo a seguir demonstra esse processo para validar se o valor da propriedade `StartDate` para um objeto `Course` é anterior ao valor de sua propriedade `EndDate`.  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2. Adicione a regra <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> de validação à coleção. A <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> propriedade fornece acesso <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> direto <xref:System.Windows.Data.BindingGroup> à propriedade de uma instância que agrupa todas as vinculações usadas pelo controle.  
  
     O exemplo a <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> seguir define a propriedade em XAML. A <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> propriedade é <xref:System.Windows.Controls.ValidationStep.UpdatedValue> definida para que a validação ocorra somente após a atualização do objeto de dados vinculado.  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Quando um usuário especificar uma data de término anterior à data de início, um ponto de exclamação vermelho (!) será exibido no cabeçalho da linha. É possível alterar esses comentários de validação padrão conforme descrito no procedimento a seguir.  
  
### <a name="to-customize-row-validation-feedback"></a>Para personalizar os comentários de validação de linha  
  
- Definir a propriedade <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType>. Esta propriedade permite que você personalize <xref:System.Windows.Controls.DataGrid> o feedback de validação de linha para controles individuais. Você também pode afetar vários controles usando um <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> estilo de linha implícito para definir a propriedade.  
  
     O exemplo a seguir substitui os comentários de validação de linha padrão por um indicador mais visível. Quando um usuário insere um valor inválido, um círculo vermelho com um ponto de exclamação branco aparece no cabeçalho da linha. Isso ocorre para erros de validação de linha e de célula. A mensagem de erro associada é exibida em uma dica de ferramenta.  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir fornece uma demonstração completa da validação de linha e de célula. A `Course` classe fornece um objeto <xref:System.ComponentModel.IEditableObject> de dados de amostra que implementa para suportar transações. O <xref:System.Windows.Controls.DataGrid> controle interage <xref:System.ComponentModel.IEditableObject> para permitir que os usuários revertam as alterações pressionando ESC.  
  
> [!NOTE]
> Se você estiver usando o Visual Basic, na primeira linha de MainWindow.xaml, substitua `x:Class="DataGridValidation.MainWindow"` por `x:Class="MainWindow"`.  
  
 Para testar a validação, tente o seguinte:  
  
- Na coluna ID do Curso, insira um valor não inteiro.  
  
- Na coluna Data de Término, insira uma data anterior à Data de Início.  
  
- Exclua o valor de ID do C, Data de Início ou Data de Término.  
  
- Para desfazer um valor de célula inválido, coloque o cursor novamente na célula e pressione a tecla ESC.  
  
- Para desfazer alterações em uma linha inteira quando a célula atual estiver no modo de edição, pressione a tecla ESC duas vezes.  
  
- Quando um erro de validação ocorrer, mova o ponteiro do mouse sobre o indicador no cabeçalho da linha para ver a mensagem de erro associada.  
  
 [!code-csharp[DataGrid_Validation#FullCode](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Controls.DataGrid>
- [DataGrid](datagrid.md)
- [Vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Implementar validação de vinculação](../data/how-to-implement-binding-validation.md)
- [Implementar lógica de validação em objetos personalizados](../data/how-to-implement-validation-logic-on-custom-objects.md)
