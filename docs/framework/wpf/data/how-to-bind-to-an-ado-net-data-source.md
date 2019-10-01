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
ms.openlocfilehash: dbe34cba8f01320fbf37beea65ed95656e09395c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697140"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a>Como: Associar a uma fonte de dados ADO.NET

Este exemplo mostra como associar um controle [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> a um ADO.NET `DataSet`.

## <a name="example"></a>Exemplo

Neste exemplo, um objeto `OleDbConnection` é usado para se conectar à fonte de dados que é um arquivo `Access MDB` especificado na cadeia de conexão. Depois que a conexão é estabelecida, um objeto `OleDbDataAdapter` é criado. O objeto `OleDbDataAdapter` executa uma instrução SELECT linguagem SQL (SQL) para recuperar o conjunto de registros do banco de dados. Os resultados do comando SQL são armazenados em um `DataTable` do `DataSet` chamando o método `Fill` do `OleDbDataAdapter`. O `DataTable` nesse exemplo é chamado de `BookTable`. Em seguida, o exemplo define a propriedade <xref:System.Windows.FrameworkElement.DataContext%2A> do <xref:System.Windows.Controls.ListBox> para o objeto `DataSet`.

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

Em seguida, podemos associar a propriedade <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> do <xref:System.Windows.Controls.ListBox> a `BookTable` do `DataSet`:

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

`BookItemTemplate` é o <xref:System.Windows.DataTemplate> que define como os dados são exibidos:

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

O `IntColorConverter` converte um `int` como uma cor. Com o uso desse conversor, a cor <xref:System.Windows.Controls.TextBlock.Background%2A> do terceiro <xref:System.Windows.Controls.TextBlock> aparece verde se o valor de `NumPages` for menor que 350 e vermelho caso contrário. A implementação do conversor não é mostrada aqui.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Data.BindingListCollectionView>
- [Visão geral da vinculação de dados](data-binding-overview.md)
- [Tópicos de instruções](data-binding-how-to-topics.md)
