---
title: 'Como: Manipular colunas e linhas usando ColumnDefinitionsCollections e RowDefinitionsCollections'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Grid class
- Grid control [WPF], ColumnDefinitionCollection class
- Grid control [WPF], RowDefinitionCollection class
ms.assetid: bfc7160a-45f2-4e17-9961-df414dfb13c5
ms.openlocfilehash: f316cced076223edba1d39c9cfb21b9a504b9eee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62017664"
---
# <a name="how-to-manipulate-columns-and-rows-by-using-columndefinitionscollections-and-rowdefinitionscollections"></a><span data-ttu-id="365de-102">Como: Manipular colunas e linhas usando ColumnDefinitionsCollections e RowDefinitionsCollections</span><span class="sxs-lookup"><span data-stu-id="365de-102">How to: Manipulate Columns and Rows by Using ColumnDefinitionsCollections and RowDefinitionsCollections</span></span>
<span data-ttu-id="365de-103">Este exemplo mostra como usar os métodos de <xref:System.Windows.Controls.ColumnDefinitionCollection> e <xref:System.Windows.Controls.RowDefinitionCollection> classes para realizar ações como adicionar, limpar ou contar o conteúdo de linhas ou colunas.</span><span class="sxs-lookup"><span data-stu-id="365de-103">This example shows how to use the methods in the <xref:System.Windows.Controls.ColumnDefinitionCollection> and <xref:System.Windows.Controls.RowDefinitionCollection> classes to perform actions like adding, clearing, or counting the contents of rows or columns.</span></span> <span data-ttu-id="365de-104">Por exemplo, você pode <xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>, <xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A>, ou <xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A> os itens que são incluídos em uma <xref:System.Windows.Controls.ColumnDefinition> ou <xref:System.Windows.Controls.RowDefinition>.</span><span class="sxs-lookup"><span data-stu-id="365de-104">For example, you can <xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>, <xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A>, or <xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A> the items that are included in a <xref:System.Windows.Controls.ColumnDefinition> or <xref:System.Windows.Controls.RowDefinition>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="365de-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="365de-105">Example</span></span>  
 <span data-ttu-id="365de-106">O exemplo a seguir cria uma <xref:System.Windows.Controls.Grid> elemento com um <xref:System.Windows.FrameworkElement.Name%2A> de `grid1`.</span><span class="sxs-lookup"><span data-stu-id="365de-106">The following example creates a <xref:System.Windows.Controls.Grid> element with a <xref:System.Windows.FrameworkElement.Name%2A> of `grid1`.</span></span> <span data-ttu-id="365de-107">O <xref:System.Windows.Controls.Grid> contém uma <xref:System.Windows.Controls.StackPanel> que contém <xref:System.Windows.Controls.Button> elementos, cada um controlado por um método diferente de coleção.</span><span class="sxs-lookup"><span data-stu-id="365de-107">The <xref:System.Windows.Controls.Grid> contains a <xref:System.Windows.Controls.StackPanel> that holds <xref:System.Windows.Controls.Button> elements, each controlled by a different collection method.</span></span> <span data-ttu-id="365de-108">Quando você clica em um <xref:System.Windows.Controls.Button>, ele ativa uma chamada de método no arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="365de-108">When you click a <xref:System.Windows.Controls.Button>, it activates a method call in the code-behind file.</span></span>  
  
 [!code-xaml[ColumnDefinitionsGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="365de-109">Este exemplo define uma série de métodos personalizados, cada um correspondendo a um <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivo.</span><span class="sxs-lookup"><span data-stu-id="365de-109">This example defines a series of custom methods, each corresponding to a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event in the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="365de-110">Você pode alterar o número de colunas e linhas no <xref:System.Windows.Controls.Grid> de diversas maneiras, o que inclui a adição ou remoção de linhas e colunas; e a contagem do número total de linhas e colunas.</span><span class="sxs-lookup"><span data-stu-id="365de-110">You can change the number of columns and rows in the <xref:System.Windows.Controls.Grid> in several ways, which includes adding or removing rows and columns; and counting the total number of rows and columns.</span></span> <span data-ttu-id="365de-111">Para evitar <xref:System.ArgumentOutOfRangeException> e <xref:System.ArgumentException> exceções, você pode usar a funcionalidade de verificação de erros que o <xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A> método fornece.</span><span class="sxs-lookup"><span data-stu-id="365de-111">To prevent <xref:System.ArgumentOutOfRangeException> and <xref:System.ArgumentException> exceptions, you can use the error-checking functionality that the <xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A> method provides.</span></span>  
  
 [!code-csharp[ColumnDefinitionsGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ColumnDefinitionsGrid#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ColumnDefinitionsGrid/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="365de-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="365de-112">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.ColumnDefinitionCollection>
- <xref:System.Windows.Controls.RowDefinitionCollection>
