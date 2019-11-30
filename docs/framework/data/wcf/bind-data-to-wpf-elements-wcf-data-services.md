---
title: Como associar dados aos elementos do Windows Presentation Foundation (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
ms.openlocfilehash: b623dc10bfe1b723c62b2861b4142a138904e64a
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569337"
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a>Como associar dados aos elementos do Windows Presentation Foundation (WCF Data Services)
Com WCF Data Services, você pode associar elementos de Windows Presentation Foundation (WPF), como um <xref:System.Windows.Controls.ListBox> ou <xref:System.Windows.Controls.ComboBox> a uma instância de <xref:System.Data.Services.Client.DataServiceCollection%601>, que manipula os eventos gerados pelos controles para manter o <xref:System.Data.Services.Client.DataServiceContext> sincronizado com as alterações feitas nos controles. Para obter mais informações, consulte [associando dados a controles](binding-data-to-controls-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criados quando você conclui o guia de [início rápido do WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir é da página code-behind de uma página da linguagem XAML que define a janela `SalesOrders` no WPF. Quando a janela é carregada, um <xref:System.Data.Services.Client.DataServiceCollection%601> é criado com base no resultado de uma consulta que retorna clientes, filtrados por país/região. Todas as páginas deste resultado paginado são carregadas, juntamente com os pedidos relacionados, e associadas à propriedade <xref:System.Windows.FrameworkElement.DataContext%2A> do <xref:System.Windows.Controls.StackPanel> que é o controle do layout raiz da janela WPF. Para obter mais informações, consulte [carregando conteúdo adiado](loading-deferred-content-wcf-data-services.md).  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## <a name="example"></a>Exemplo  
 O XAML a seguir define a janela `SalesOrders` no WPF do exemplo anterior.  
  
 [!code-xaml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir é da página code-behind de uma página da linguagem XAML que define a janela `SalesOrders` no WPF. Quando a janela é carregada, um <xref:System.Data.Services.Client.DataServiceCollection%601> é criado com base no resultado de uma consulta que retorna clientes com objetos relacionados, filtrados por país/região. Esse resultado é associado à propriedade <xref:System.Windows.FrameworkElement.DataContext%2A> do <xref:System.Windows.Controls.StackPanel> que é o controle de layout raiz da janela WPF.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## <a name="example"></a>Exemplo  
 O XAML a seguir define a janela `SalesOrders` no WPF do exemplo anterior.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]
