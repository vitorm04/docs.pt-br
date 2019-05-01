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
# <a name="how-to-manipulate-columns-and-rows-by-using-columndefinitionscollections-and-rowdefinitionscollections"></a>Como: Manipular colunas e linhas usando ColumnDefinitionsCollections e RowDefinitionsCollections
Este exemplo mostra como usar os métodos de <xref:System.Windows.Controls.ColumnDefinitionCollection> e <xref:System.Windows.Controls.RowDefinitionCollection> classes para realizar ações como adicionar, limpar ou contar o conteúdo de linhas ou colunas. Por exemplo, você pode <xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>, <xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A>, ou <xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A> os itens que são incluídos em uma <xref:System.Windows.Controls.ColumnDefinition> ou <xref:System.Windows.Controls.RowDefinition>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma <xref:System.Windows.Controls.Grid> elemento com um <xref:System.Windows.FrameworkElement.Name%2A> de `grid1`. O <xref:System.Windows.Controls.Grid> contém uma <xref:System.Windows.Controls.StackPanel> que contém <xref:System.Windows.Controls.Button> elementos, cada um controlado por um método diferente de coleção. Quando você clica em um <xref:System.Windows.Controls.Button>, ele ativa uma chamada de método no arquivo code-behind.  
  
 [!code-xaml[ColumnDefinitionsGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml#1)]  
  
 Este exemplo define uma série de métodos personalizados, cada um correspondendo a um <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivo. Você pode alterar o número de colunas e linhas no <xref:System.Windows.Controls.Grid> de diversas maneiras, o que inclui a adição ou remoção de linhas e colunas; e a contagem do número total de linhas e colunas. Para evitar <xref:System.ArgumentOutOfRangeException> e <xref:System.ArgumentException> exceções, você pode usar a funcionalidade de verificação de erros que o <xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A> método fornece.  
  
 [!code-csharp[ColumnDefinitionsGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ColumnDefinitionsGrid#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ColumnDefinitionsGrid/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.ColumnDefinitionCollection>
- <xref:System.Windows.Controls.RowDefinitionCollection>
