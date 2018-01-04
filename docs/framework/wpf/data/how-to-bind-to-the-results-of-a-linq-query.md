---
title: Como associar aos resultados de uma consulta LINQ
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad4969d80f7bd801ec738fa40e8b2d4ab9deefad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a>Como associar aos resultados de uma consulta LINQ
Este exemplo demonstra como executar uma consulta LINQ e associar aos resultados.  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo cria duas caixas de listagem. A primeira caixa de listagem contém três itens de lista.  
  
 [!code-xaml[LinqExample#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 Selecionar um item na primeira caixa de listagem invoca o manipulador de eventos a seguir. Neste exemplo, `Tasks` é uma coleção de objetos `Task`. A classe `Task` tem uma propriedade chamada `Priority`. Este manipulador de eventos executa uma consulta LINQ que retorna a coleção de `Task` objetos que têm o valor de prioridade selecionada e, em seguida, define como o <xref:System.Windows.FrameworkElement.DataContext%2A>:  
  
 [!code-csharp[LinqExample#Using](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 A segunda caixa de lista associado a essa coleção porque seu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> valor é definido como `{Binding}`. Como resultado, ele exibe a coleção retornada (com base no `myTaskTemplate` <xref:System.Windows.DataTemplate>).  
  
## <a name="see-also"></a>Consulte também  
 [Disponibilizar dados para associação em XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)  
 [Associar a uma coleção e exibir informações com base na seleção](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [Novidades no WPF versão 4.5](../../../../docs/framework/wpf/getting-started/whats-new.md)  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
