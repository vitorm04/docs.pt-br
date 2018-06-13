---
title: Como associar a uma fonte de dados ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to ADO.NET data sources
- ADO.NET data sources [WPF], binding to
- binding [WPF], to ADO.NET data sources
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
ms.openlocfilehash: c9e16b9fd100eb9aec7bee2f94307aa80371d5ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556855"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a><span data-ttu-id="adb2b-102">Como associar a uma fonte de dados ADO.NET</span><span class="sxs-lookup"><span data-stu-id="adb2b-102">How to: Bind to an ADO.NET Data Source</span></span>
<span data-ttu-id="adb2b-103">Este exemplo mostra como associar um [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> o controle para um [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="adb2b-103">This example shows how to bind a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> control to an [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="adb2b-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="adb2b-104">Example</span></span>  
 <span data-ttu-id="adb2b-105">Neste exemplo, um objeto `OleDbConnection` é usado para se conectar à fonte de dados que é um arquivo `Access MDB` especificado na cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="adb2b-105">In this example, an `OleDbConnection` object is used to connect to the data source which is an `Access MDB` file that is specified in the connection string.</span></span> <span data-ttu-id="adb2b-106">Depois que a conexão é estabelecida, um objeto `OleDbDataAdpater` é criado.</span><span class="sxs-lookup"><span data-stu-id="adb2b-106">After the connection is established, an `OleDbDataAdpater` object is created.</span></span> <span data-ttu-id="adb2b-107">O objeto `OleDbDataAdpater` executa uma instrução do [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] de seleção para recuperar o conjunto de registros do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="adb2b-107">The `OleDbDataAdpater` object executes a select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] statement to retrieve the recordset from the database.</span></span> <span data-ttu-id="adb2b-108">Os resultados do comando [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] são armazenados em um `DataTable` do `DataSet` chamando o método `Fill` do `OleDbDataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="adb2b-108">The results from the [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] command are stored in a `DataTable` of the `DataSet` by calling the `Fill` method of the `OleDbDataAdapter`.</span></span> <span data-ttu-id="adb2b-109">O `DataTable` nesse exemplo é chamado de `BookTable`.</span><span class="sxs-lookup"><span data-stu-id="adb2b-109">The `DataTable` in this example is named `BookTable`.</span></span> <span data-ttu-id="adb2b-110">O exemplo define o <xref:System.Windows.FrameworkElement.DataContext%2A> propriedade o <xref:System.Windows.Controls.ListBox> para o `DataSet` objeto.</span><span class="sxs-lookup"><span data-stu-id="adb2b-110">The example then sets the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the <xref:System.Windows.Controls.ListBox> to the `DataSet` object.</span></span>  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="adb2b-111">Podemos, em seguida, associar a <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriedade o <xref:System.Windows.Controls.ListBox> para `BookTable` do `DataSet`:</span><span class="sxs-lookup"><span data-stu-id="adb2b-111">We can then bind the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to `BookTable` of the `DataSet`:</span></span>  
  
 [!code-xaml[ADODataSet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="adb2b-112">`BookItemTemplate` é o <xref:System.Windows.DataTemplate> que define como os dados aparecem:</span><span class="sxs-lookup"><span data-stu-id="adb2b-112">`BookItemTemplate` is the <xref:System.Windows.DataTemplate> that defines how the data appears:</span></span>  
  
 [!code-xaml[ADODataSet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]  
  
 <span data-ttu-id="adb2b-113">O `IntColorConverter` converte um `int` como uma cor.</span><span class="sxs-lookup"><span data-stu-id="adb2b-113">The `IntColorConverter` converts an `int` to a color.</span></span> <span data-ttu-id="adb2b-114">Com o uso deste conversor, o <xref:System.Windows.Controls.TextBlock.Background%2A> cor da terceira <xref:System.Windows.Controls.TextBlock> aparece verde se o valor de `NumPages` é menor que 350 e vermelho caso contrário.</span><span class="sxs-lookup"><span data-stu-id="adb2b-114">With the use of this converter, the <xref:System.Windows.Controls.TextBlock.Background%2A> color of the third <xref:System.Windows.Controls.TextBlock> appears green if the value of `NumPages` is less than 350 and red otherwise.</span></span> <span data-ttu-id="adb2b-115">A implementação do conversor não é mostrada aqui.</span><span class="sxs-lookup"><span data-stu-id="adb2b-115">The implementation of the converter is not shown here.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adb2b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="adb2b-116">See Also</span></span>  
 <xref:System.Windows.Data.BindingListCollectionView>  
 [<span data-ttu-id="adb2b-117">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="adb2b-117">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="adb2b-118">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="adb2b-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
