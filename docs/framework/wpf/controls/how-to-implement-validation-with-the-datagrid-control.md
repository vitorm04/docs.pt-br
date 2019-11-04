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
ms.openlocfilehash: 401949aa4bea924b458a91dc00c454c97aff4895
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458459"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>Como implementar validação com o controle DataGrid
O controle de <xref:System.Windows.Controls.DataGrid> permite que você execute a validação no nível de célula e de linha. Com a validação no nível da célula, você valida propriedades individuais de um objeto com associação de dados quando um usuário atualiza um valor. Com a validação no nível da linha, você valida objetos de dados inteiros quando um usuário confirma alterações em uma linha. Você também pode fornecer comentários visuais personalizados para erros de validação ou usar os comentários visuais padrão que o controle de <xref:System.Windows.Controls.DataGrid> fornece.  
  
 Os procedimentos a seguir descrevem como aplicar regras de validação a <xref:System.Windows.Controls.DataGrid> associações e personalizar os comentários visuais.  
  
### <a name="to-validate-individual-cell-values"></a>Para validar valores de células individuais  
  
- Especifique uma ou mais regras de validação para a associação usada com uma coluna. Isso é semelhante à validação de dados em controles simples, conforme descrito em [Visão geral da associação de dados](../data/data-binding-overview.md).  
  
     O exemplo a seguir mostra um controle <xref:System.Windows.Controls.DataGrid> com quatro colunas associadas a propriedades diferentes de um objeto comercial. Três das colunas especificam o <xref:System.Windows.Controls.ExceptionValidationRule> definindo a propriedade <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> como `true`.  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Quando um usuário insere um valor inválido (como um número não inteiro na coluna de ID do Curso), uma borda vermelha aparece em torno da célula. É possível alterar esses comentários de validação padrão conforme descrito no procedimento a seguir.  
  
### <a name="to-customize-cell-validation-feedback"></a>Para personalizar os comentários de validação de célula  
  
- Defina a propriedade <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> da coluna como um estilo apropriado para o controle de edição da coluna. Como os controles de edição são criados em tempo de execução, você não pode usar a propriedade <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> anexada como faria com controles simples.  
  
     O exemplo a seguir atualiza o exemplo anterior adicionando um estilo de erro compartilhado pelas três colunas com regras de validação. Quando um usuário insere um valor inválido, o estilo altera a cor da tela de fundo da célula e adiciona uma dica de ferramenta. Observe o uso de um gatilho para determinar se há um erro de validação. Isso é necessário porque atualmente não há um modelo de erro dedicado para células.  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Você pode implementar uma personalização mais ampla substituindo o <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> usado pela coluna.  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>Para validar vários valores em uma única linha  
  
1. Implemente uma subclasse <xref:System.Windows.Controls.ValidationRule> que verifica várias propriedades do objeto de dados vinculado. Na implementação do método de <xref:System.Windows.Controls.ValidationRule.Validate%2A>, converta o valor do parâmetro `value` em uma instância <xref:System.Windows.Data.BindingGroup>. Em seguida, você pode acessar o objeto de dados por meio da propriedade <xref:System.Windows.Data.BindingGroup.Items%2A>.  
  
     O exemplo a seguir demonstra esse processo para validar se o valor da propriedade `StartDate` para um objeto `Course` é anterior ao valor de sua propriedade `EndDate`.  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2. Adicione a regra de validação à coleção de <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType>. A propriedade <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> fornece acesso direto à propriedade <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> de uma instância <xref:System.Windows.Data.BindingGroup> que agrupa todas as associações usadas pelo controle.  
  
     O exemplo a seguir define a propriedade <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> em XAML. A propriedade <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> é definida como <xref:System.Windows.Controls.ValidationStep.UpdatedValue> para que a validação ocorra somente depois que o objeto de dados associado for atualizado.  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Quando um usuário especificar uma data de término anterior à data de início, um ponto de exclamação vermelho (!) será exibido no cabeçalho da linha. É possível alterar esses comentários de validação padrão conforme descrito no procedimento a seguir.  
  
### <a name="to-customize-row-validation-feedback"></a>Para personalizar os comentários de validação de linha  
  
- Definir a propriedade <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType>. Essa propriedade permite que você personalize comentários de validação de linha para controles de <xref:System.Windows.Controls.DataGrid> individuais. Você também pode afetar vários controles usando um estilo de linha implícito para definir a propriedade <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType>.  
  
     O exemplo a seguir substitui os comentários de validação de linha padrão por um indicador mais visível. Quando um usuário insere um valor inválido, um círculo vermelho com um ponto de exclamação branco aparece no cabeçalho da linha. Isso ocorre para erros de validação de linha e de célula. A mensagem de erro associada é exibida em uma dica de ferramenta.  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir fornece uma demonstração completa da validação de linha e de célula. A classe `Course` fornece um objeto de dados de exemplo que implementa <xref:System.ComponentModel.IEditableObject> para dar suporte a transações. O controle de <xref:System.Windows.Controls.DataGrid> interage com <xref:System.ComponentModel.IEditableObject> para permitir que os usuários revertam as alterações pressionando ESC.  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.DataGrid>
- [DataGrid](datagrid.md)
- [Associação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Implementar a validação de associação](../data/how-to-implement-binding-validation.md)
- [Implementar a lógica de validação em objetos personalizados](../data/how-to-implement-validation-logic-on-custom-objects.md)
