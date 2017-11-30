---
title: 'Como: associar dados usando uma fonte de dados do projeto (WCF Data Services)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: 2477af0a-676f-44f7-b73d-e66208785509
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5b56fecef5ace38f728d8cc68df4dcfeb71bfedf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-data-using-a-project-data-source-wcf-data-services"></a>Como: associar dados usando uma fonte de dados do projeto (WCF Data Services)
Você pode criar fontes de dados que são baseados nos objetos de dados gerados em um [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] aplicativo cliente. Quando você adiciona uma referência a um serviço de dados usando o **adicionar referência de serviço** caixa de diálogo, uma fonte de dados do projeto é criada junto com as classes de dados do cliente gerado. Uma fonte de dados é criada para cada conjunto de entidades que o serviço de dados expõe. Você pode criar formulários que exibem dados do serviço ao arrastar esses itens de fonte de dados do **fontes de dados** janela no designer. Esses itens se tornam os controles que estão associados à fonte de dados. Durante a execução, essa fonte de dados está associada a uma instância do <xref:System.Data.Services.Client.DataServiceCollection%601> classe, que é preenchido com objetos que são retornados por uma consulta para o serviço de dados. Para obter mais informações, consulte [vinculação de dados a controles](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
 Os exemplos neste tópico usam o serviço de dados de exemplo Northwind e dados de cliente gerado automaticamente classes de serviço. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-use-a-project-data-source-in-a-wpf-window"></a>Para usar uma fonte de dados do projeto em uma janela WPF  
  
1.  Em um projeto WPF, adicione uma referência para o serviço de dados Northwind. Para obter mais informações, consulte [como: adicionar uma referência de serviço de dados](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).  
  
2.  No **fontes de dados** janela, expanda o `Customers` nó o **NorthwindEntities** fonte de dados do projeto.  
  
3.  Clique o **CustomerID** item, selecione **ComboBox** na lista e arraste o **CustomerID** item do **clientes** nó para o Designer.  
  
     Isso cria os seguintes elementos de objeto no arquivo XAML da janela:  
  
    -   Um <xref:System.Windows.Data.CollectionViewSource> elemento chamado `customersViewSource`. O <xref:System.Windows.FrameworkElement.DataContext%2A> propriedade de nível superior <xref:System.Windows.Controls.Grid> objeto é definido para esse novo <xref:System.Windows.Data.CollectionViewSource>.  
  
    -   Uma associação de dados <xref:System.Windows.Controls.ComboBox> chamado `CustomerID`.  
  
    -   Um <xref:System.Windows.Controls.Label>.  
  
4.  Arraste o **pedidos** propriedade de navegação para o designer.  
  
     Isso cria os seguintes elementos de objeto adicionais no arquivo XAML da janela:  
  
    -   Um segundo <xref:System.Windows.Data.CollectionViewSource> elemento chamado `customersOrdersViewSource`, a origem da qual é o `customerViewSource`.  
  
    -   Uma associação de dados <xref:System.Windows.Controls.DataGrid> controle chamado `ordersDataGrid`.  
  
5.  (Opcional) Arraste itens adicionais do **clientes** nó para o designer.  
  
6.  Abra a página de código para o formulário e adicione o seguinte `using` instruções (`Imports` no Visual Basic):  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersusingwpf)]  
  
7.  Na classe parcial que define o formulário, adicione o seguinte código que cria um <xref:System.Data.Objects.ObjectContext> instância e define o `customerID` constante.  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersdefinitionwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf2.xaml.vb#customersordersdefinitionwpf)]  
  
8.  No designer, selecione a janela.  
  
    > [!NOTE]
    >  Certifique-se de que você selecione a janela em si, em vez de selecionar o conteúdo que está dentro da janela. Se a janela for selecionada, o **nome** caixa de texto na parte superior do **propriedades** janela deve conter o nome da janela.  
  
9. No **propriedades** janela, selecione o **eventos** botão.  
  
10. Localizar o **Loaded** evento e, em seguida, clique duas vezes na lista suspensa lista ao lado desse evento.  
  
     O Visual Studio abre o arquivo de code-behind para a janela e gera um <xref:System.Windows.FrameworkElement.Loaded> manipulador de eventos.  
  
11. No recém-criado <xref:System.Windows.FrameworkElement.Loaded> manipulador de eventos, copie e cole o código a seguir.  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersdatabindingwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf2.xaml.vb#customersordersdatabindingwpf)]  
  
12. Esse código cria uma instância de <xref:System.Data.Services.Client.DataServiceCollection%601> para o `Customers` tipo com base na execução de uma consulta LINQ que retorna um <xref:System.Collections.Generic.IEnumerable%601> de `Customers` juntamente com relacionados `Orders` objetos do serviço de dados Northwind e associa-o para o `customersViewSource`.  
  
### <a name="to-use-a-project-data-source-in-a-windows-form"></a>Para usar uma fonte de dados do projeto em um Windows form  
  
1.  No **fontes de dados** janela, expanda o **clientes** nó o **NorthwindEntities** fonte de dados do projeto.  
  
2.  Clique o **CustomerID** item, selecione **ComboBox** na lista e arraste o **CustomerID** item do **clientes** nó para o Designer.  
  
     Isso cria os seguintes controles no formulário:  
  
    -   Uma instância de <xref:System.Windows.Forms.BindingSource> chamado `customersBindingSource`.  
  
    -   Uma instância de <xref:System.Windows.Forms.BindingNavigator> chamado `customersBindingNavigator`. Você pode excluir esse controle pois ele não será necessária.  
  
    -   Uma associação de dados <xref:System.Windows.Forms.ComboBox> chamado `CustomerID`.  
  
    -   Um <xref:System.Windows.Forms.Label>.  
  
3.  Arraste o **pedidos** propriedade de navegação para o formulário.  
  
4.  Isso cria o `ordersBindingSource` controlar com o <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriedade do controle definido como o `customersBindingSource` e <xref:System.Windows.Forms.BindingSource.DataMember%2A> propriedade definida como `Customers`. Ele também cria o `ordersDataGridView` controle associado a dados no formulário, acompanhado de um controle de rótulo intitulada adequadamente.  
  
5.  (Opcional) Arraste itens adicionais do **clientes** nó para o designer.  
  
6.  Abra a página de código para o formulário e adicione o seguinte `using` instruções (`Imports` no Visual Basic):  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersusing)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersusing)]  
  
7.  Na classe parcial que define o formulário, adicione o seguinte código que cria um <xref:System.Data.Objects.ObjectContext> instância e define o `customerID` constante.  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersdefinition)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersdefinition)]  
  
8.  No designer de formulário, clique duas vezes o formulário.  
  
     Isso abre a página de código para o formulário e cria o método que manipula o `Load` evento para o formulário.  
  
9. No manipulador de eventos `Load`, copie e cole o código a seguir.  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersdatabinding)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersdatabinding)]  
  
10. Esse código cria uma instância de <xref:System.Data.Services.Client.DataServiceCollection%601> para o `Customers` tipo com base na execução de um <xref:System.Data.Services.Client.DataServiceQuery%601> que retorna um <xref:System.Collections.Generic.IEnumerable%601> de `Customers` o Northwind dados de serviço e associa-o para o `customersBindingSource`.  
  
## <a name="see-also"></a>Consulte também  
 [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)  
 [How to: Bind Data to Windows Presentation Foundation Elements](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md) (Como associar dados aos elementos do Windows Presentation Foundation)
