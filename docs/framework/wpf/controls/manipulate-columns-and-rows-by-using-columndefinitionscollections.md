---
title: Como manipular colunas e linhas usando ColumnDefinitionsCollections e RowDefinitionsCollections
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Grid class
- Grid control [WPF], ColumnDefinitionCollection class
- Grid control [WPF], RowDefinitionCollection class
ms.assetid: bfc7160a-45f2-4e17-9961-df414dfb13c5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e87c5001a676bcda331d289c286cf6b3e87c136f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-manipulate-columns-and-rows-by-using-columndefinitionscollections-and-rowdefinitionscollections"></a>Como manipular colunas e linhas usando ColumnDefinitionsCollections e RowDefinitionsCollections
Este exemplo mostra como usar os métodos de <xref:System.Windows.Controls.ColumnDefinitionCollection> e <xref:System.Windows.Controls.RowDefinitionCollection> classes para realizar ações como adicionar, limpar ou contar o conteúdo de linhas ou colunas. Por exemplo, você pode <xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>, <xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A>, ou <xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A> os itens que são incluídos em um <xref:System.Windows.Controls.ColumnDefinition> ou <xref:System.Windows.Controls.RowDefinition>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um <xref:System.Windows.Controls.Grid> elemento com um <xref:System.Windows.FrameworkElement.Name%2A> de `grid1`. O <xref:System.Windows.Controls.Grid> contém um <xref:System.Windows.Controls.StackPanel> que contém <xref:System.Windows.Controls.Button> elementos, cada um controlado por um método diferente de coleção. Quando você clica em um <xref:System.Windows.Controls.Button>, ele ativa uma chamada de método no arquivo code-behind.  
  
 [!code-xaml[ColumnDefinitionsGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml#1)]  
  
 Este exemplo define uma série de métodos personalizados, cada um correspondendo a um <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento o [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivo. Você pode alterar o número de colunas e linhas de <xref:System.Windows.Controls.Grid> de diversas maneiras, que inclui a adição ou remoção de linhas e colunas; e contando o número total de linhas e colunas. Para evitar <xref:System.ArgumentOutOfRangeException> e <xref:System.ArgumentException> exceções, você pode usar a funcionalidade de verificação de erros que o <xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A> método fornece.  
  
 [!code-csharp[ColumnDefinitionsGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ColumnDefinitionsGrid#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ColumnDefinitionsGrid/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Controls.ColumnDefinitionCollection>  
 <xref:System.Windows.Controls.RowDefinitionCollection>
