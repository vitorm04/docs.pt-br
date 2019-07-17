---
title: 'Como: Associar a uma fonte de dados ADO.NET'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to ADO.NET data sources
- ADO.NET data sources [WPF], binding to
- binding [WPF], to ADO.NET data sources
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
ms.openlocfilehash: 96f846db3f705972a4749460bf2c410483258572
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238423"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a>Como: Associar a uma fonte de dados ADO.NET

Este exemplo mostra como associar um [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> controle para o ADO.NET `DataSet`.

## <a name="example"></a>Exemplo

Neste exemplo, um objeto `OleDbConnection` é usado para se conectar à fonte de dados que é um arquivo `Access MDB` especificado na cadeia de conexão. Depois que a conexão é estabelecida, um objeto `OleDbDataAdapter` é criado. O objeto `OleDbDataAdapter` executa uma instrução do [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] de seleção para recuperar o conjunto de registros do banco de dados. Os resultados do comando [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] são armazenados em um `DataTable` do `DataSet` chamando o método `Fill` do `OleDbDataAdapter`. O `DataTable` nesse exemplo é chamado de `BookTable`. O exemplo, em seguida, define o <xref:System.Windows.FrameworkElement.DataContext%2A> propriedade do <xref:System.Windows.Controls.ListBox> para o `DataSet` objeto.

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

Pode, em seguida, ligamos a <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedade do <xref:System.Windows.Controls.ListBox> ao `BookTable` da `DataSet`:

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

`BookItemTemplate` é o <xref:System.Windows.DataTemplate> que define como os dados aparecem:

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

O `IntColorConverter` converte um `int` como uma cor. Com o uso desse conversor, a <xref:System.Windows.Controls.TextBlock.Background%2A> cor da terceira <xref:System.Windows.Controls.TextBlock> é exibido em verde se o valor de `NumPages` for menor que 350 e vermelho caso contrário. A implementação do conversor não é mostrada aqui.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Data.BindingListCollectionView>
- [Visão geral da vinculação de dados](data-binding-overview.md)
- [Tópicos de instruções](data-binding-how-to-topics.md)
