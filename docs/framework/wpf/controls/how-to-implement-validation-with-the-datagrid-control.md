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
ms.openlocfilehash: 20fcc8ebafb25e4e4f176447972e7637aaa5cd7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>Como implementar validação com o controle DataGrid
O <xref:System.Windows.Controls.DataGrid> controle permite que você execute a validação no nível de linha e célula. Com a validação no nível da célula, você valida propriedades individuais de um objeto com associação de dados quando um usuário atualiza um valor. Com a validação no nível da linha, você valida objetos de dados inteiros quando um usuário confirma alterações em uma linha. Você também pode fornecer comentários visuais personalizados para erros de validação ou usar o comentário visual padrão que o <xref:System.Windows.Controls.DataGrid> fornece controle.  
  
 Os procedimentos a seguir descrevem como aplicar regras de validação para <xref:System.Windows.Controls.DataGrid> associações e personalizar os comentários visuais.  
  
### <a name="to-validate-individual-cell-values"></a>Para validar valores de células individuais  
  
-   Especifique uma ou mais regras de validação para a associação usada com uma coluna. Isso é semelhante à validação de dados em controles simples, conforme descrito em [Visão geral da associação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
     A exemplo a seguir mostra um <xref:System.Windows.Controls.DataGrid> controle com quatro colunas associadas a diferentes propriedades de um objeto comercial. Três das colunas de especificar o <xref:System.Windows.Controls.ExceptionValidationRule> definindo o <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> propriedade `true`.  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Quando um usuário insere um valor inválido (como um número não inteiro na coluna de ID do Curso), uma borda vermelha aparece em torno da célula. É possível alterar esses comentários de validação padrão conforme descrito no procedimento a seguir.  
  
### <a name="to-customize-cell-validation-feedback"></a>Para personalizar os comentários de validação de célula  
  
-   Definir a coluna <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> apropriado de propriedade para um estilo para a coluna do controle de edição. Como os controles de edição são criados em tempo de execução, você não pode usar o <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> como faria com controles simples de propriedade anexada.  
  
     O exemplo a seguir atualiza o exemplo anterior adicionando um estilo de erro compartilhado pelas três colunas com regras de validação. Quando um usuário insere um valor inválido, o estilo altera a cor da tela de fundo da célula e adiciona uma dica de ferramenta. Observe o uso de um gatilho para determinar se há um erro de validação. Isso é necessário porque atualmente não há um modelo de erro dedicado para células.  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Você pode implementar mais ampla personalização, substituindo o <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> usado pela coluna.  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>Para validar vários valores em uma única linha  
  
1.  Implementar um <xref:System.Windows.Controls.ValidationRule> subclasse que verifica várias propriedades do objeto de dados associado. No seu <xref:System.Windows.Controls.ValidationRule.Validate%2A> convertido de implementação de método, o `value` valor de parâmetro para um <xref:System.Windows.Data.BindingGroup> instância. Você pode acessar o objeto de dados por meio de <xref:System.Windows.Data.BindingGroup.Items%2A> propriedade.  
  
     O exemplo a seguir demonstra esse processo para validar se o valor da propriedade `StartDate` para um objeto `Course` é anterior ao valor de sua propriedade `EndDate`.  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2.  Adicionar a regra de validação para o <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> coleção. O <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> propriedade fornece acesso direto ao <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> propriedade de um <xref:System.Windows.Data.BindingGroup> instância que agrupa todas as associações usadas pelo controle.  
  
     O exemplo a seguir define o <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> propriedade em XAML. O <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> está definida como <xref:System.Windows.Controls.ValidationStep.UpdatedValue> para que a validação ocorre somente depois que o objeto de dados associado será atualizado.  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Quando um usuário especificar uma data de término anterior à data de início, um ponto de exclamação vermelho (!) será exibido no cabeçalho da linha. É possível alterar esses comentários de validação padrão conforme descrito no procedimento a seguir.  
  
### <a name="to-customize-row-validation-feedback"></a>Para personalizar os comentários de validação de linha  
  
-   Definir a propriedade <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType>. Essa propriedade permite que você personalize a comentários de validação de linha para o indivíduo <xref:System.Windows.Controls.DataGrid> controles. Você também pode afetar vários controles usando um estilo de linha implícita para definir o <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> propriedade.  
  
     O exemplo a seguir substitui os comentários de validação de linha padrão por um indicador mais visível. Quando um usuário insere um valor inválido, um círculo vermelho com um ponto de exclamação branco aparece no cabeçalho da linha. Isso ocorre para erros de validação de linha e de célula. A mensagem de erro associada é exibida em uma dica de ferramenta.  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir fornece uma demonstração completa da validação de linha e de célula. O `Course` classe fornece um objeto de dados de exemplo que implementa <xref:System.ComponentModel.IEditableObject> oferecer suporte a transações. O <xref:System.Windows.Controls.DataGrid> controle interage com <xref:System.ComponentModel.IEditableObject> para permitir que os usuários reverter alterações pressionando ESC.  
  
> [!NOTE]
>  Se você estiver usando o Visual Basic, na primeira linha de MainWindow.xaml, substitua `x:Class="DataGridValidation.MainWindow"` por `x:Class="MainWindow"`.  
  
 Para testar a validação, tente o seguinte:  
  
-   Na coluna ID do Curso, insira um valor não inteiro.  
  
-   Na coluna Data de Término, insira uma data anterior à Data de Início.  
  
-   Exclua o valor de ID do C, Data de Início ou Data de Término.  
  
-   Para desfazer um valor de célula inválido, coloque o cursor novamente na célula e pressione a tecla ESC.  
  
-   Para desfazer alterações em uma linha inteira quando a célula atual estiver no modo de edição, pressione a tecla ESC duas vezes.  
  
-   Quando um erro de validação ocorrer, mova o ponteiro do mouse sobre o indicador no cabeçalho da linha para ver a mensagem de erro associada.  
  
 [!code-csharp[DataGrid_Validation#FullCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.DataGrid>  
 [DataGrid](../../../../docs/framework/wpf/controls/datagrid.md)  
 [Associação de dados](../../../../docs/framework/wpf/data/data-binding-wpf.md)  
 [Implementar a validação de associação](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [Implementar a lógica de validação em objetos personalizados](../../../../docs/framework/wpf/data/how-to-implement-validation-logic-on-custom-objects.md)
