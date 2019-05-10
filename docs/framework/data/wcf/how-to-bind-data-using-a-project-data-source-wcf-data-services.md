---
title: 'Como: Associar dados usando uma fonte de dados do projeto (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: 2477af0a-676f-44f7-b73d-e66208785509
ms.openlocfilehash: 69a0ec657f0a8cec34048776a4767cec23d091d9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645634"
---
# <a name="how-to-bind-data-using-a-project-data-source-wcf-data-services"></a>Como: Associar dados usando uma fonte de dados do projeto (WCF Data Services)

Você pode criar fontes de dados que são baseados nos objetos de dados gerados em um aplicativo de cliente do WCF Data Services. Quando você adiciona uma referência a um serviço de dados usando o **adicionar referência de serviço** caixa de diálogo, uma fonte de dados do projeto é criada junto com as classes de dados do cliente gerado. Uma fonte de dados é criada para cada conjunto de entidades que os dados de serviço expõe. Você pode criar formulários que exibem dados do serviço, arrastando esses itens de fonte de dados das **fontes de dados** janela no designer. Esses itens se tornam os controles que estão associados à fonte de dados. Durante a execução, esta fonte de dados está associada a uma instância da <xref:System.Data.Services.Client.DataServiceCollection%601> classe, que é preenchida com objetos que são retornados por uma consulta ao serviço de dados. Para obter mais informações, consulte [associando dados a controles](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).

 Os exemplos neste tópico usam o serviço de dados de exemplo Northwind e dados de cliente gerado automaticamente classes de serviço. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [início rápido do WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).

## <a name="use-a-project-data-source-in-a-wpf-window"></a>Usar uma fonte de dados do projeto em uma janela do WPF

1. No Visual Studio, em um projeto do WPF, adicione uma referência ao serviço de dados Northwind. Para obter mais informações, confira [Como: Adicionar uma referência de serviço de dados](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).

2. No **fontes de dados** janela, expanda o `Customers` nó no **NorthwindEntities** fonte de dados do projeto.

3. Clique o **CustomerID** item, selecione **ComboBox** na lista e arraste o **CustomerID** item do **clientes** nó para o Designer.

     Isso cria os seguintes elementos de objeto no arquivo XAML da janela:

    - Um <xref:System.Windows.Data.CollectionViewSource> elemento chamado `customersViewSource`. O <xref:System.Windows.FrameworkElement.DataContext%2A> propriedade de nível superior <xref:System.Windows.Controls.Grid> elemento de objeto é definido para esse novo <xref:System.Windows.Data.CollectionViewSource>.

    - Uma associação de dados <xref:System.Windows.Controls.ComboBox> chamado `CustomerID`.

    - Um <xref:System.Windows.Controls.Label>.

4. Arraste o **pedidos** propriedade de navegação para o designer.

     Isso cria os seguintes elementos de objeto adicionais no arquivo XAML da janela:

    - Um segundo <xref:System.Windows.Data.CollectionViewSource> elemento denominado `customersOrdersViewSource`, a origem da qual é o `customerViewSource`.

    - Uma associação de dados <xref:System.Windows.Controls.DataGrid> controle chamado `ordersDataGrid`.

5. (Opcional) Arraste itens adicionais do **clientes** nó para o designer.

6. Abra a página de código para o formulário e adicione o seguinte `using` instruções (`Imports` no Visual Basic):

     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersusingwpf)]

7. Na classe parcial que define o formulário, adicione o seguinte código que cria um <xref:System.Data.Objects.ObjectContext> da instância e define o `customerID` constante.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersdefinitionwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf2.xaml.vb#customersordersdefinitionwpf)]

8. No designer, selecione a janela.

    > [!NOTE]
    > Certifique-se de que você selecione a janela em si, em vez de selecionar o conteúdo que está dentro da janela. Se a janela for selecionada, o **nome** caixa de texto na parte superior do **propriedades** janela deve conter o nome da janela.

9. No **propriedades** janela, selecione a **eventos** botão.

10. Localizar o **Loaded** evento e, em seguida, clique duas vezes na lista suspensa lista ao lado desse evento.

     Visual Studio abre o arquivo code-behind da janela e gera um <xref:System.Windows.FrameworkElement.Loaded> manipulador de eventos.

11. Em recém-criado <xref:System.Windows.FrameworkElement.Loaded> manipulador de eventos, copie e cole o código a seguir.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersdatabindingwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf2.xaml.vb#customersordersdatabindingwpf)]

12. Esse código cria uma instância do <xref:System.Data.Services.Client.DataServiceCollection%601> para o `Customers` tipo com base na execução de uma consulta LINQ que retorna um <xref:System.Collections.Generic.IEnumerable%601> de `Customers` juntamente com relacionados `Orders` objetos do serviço de dados Northwind e associá-lo para o `customersViewSource`.

## <a name="use-a-project-data-source-in-a-windows-form"></a>Usar uma fonte de dados de projeto em um formulário do Windows

1. No **fontes de dados** janela, expanda o **clientes** nó no **NorthwindEntities** fonte de dados do projeto.

2. Clique o **CustomerID** item, selecione **ComboBox** na lista e arraste o **CustomerID** item do **clientes** nó para o Designer.

     Isso cria os seguintes controles no formulário:

    - Uma instância do <xref:System.Windows.Forms.BindingSource> chamado `customersBindingSource`.

    - Uma instância do <xref:System.Windows.Forms.BindingNavigator> chamado `customersBindingNavigator`. Você pode excluir esse controle, pois ele não será necessária.

    - Uma associação de dados <xref:System.Windows.Forms.ComboBox> chamado `CustomerID`.

    - Um <xref:System.Windows.Forms.Label>.

3. Arraste o **pedidos** propriedade de navegação para o formulário.

4. Isso cria o `ordersBindingSource` controlar com o <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriedade do controle definido como o `customersBindingSource` e o <xref:System.Windows.Forms.BindingSource.DataMember%2A> propriedade definida como `Customers`. Ele também cria o `ordersDataGridView` controle associado a dados no formulário, acompanhado de um controle de rótulo intitulado apropriadamente.

5. (Opcional) Arraste itens adicionais do **clientes** nó para o designer.

6. Abra a página de código para o formulário e adicione o seguinte `using` instruções (`Imports` no Visual Basic):

     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersusing)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersusing)]

7. Na classe parcial que define o formulário, adicione o seguinte código que cria um <xref:System.Data.Objects.ObjectContext> da instância e define o `customerID` constante.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdefinition)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdefinition)]

8. No designer de formulário, clique duas vezes no formulário.

     Isso abre a página de código para o formulário e cria o método que manipula o `Load` evento para o formulário.

9. No manipulador de eventos `Load`, copie e cole o código a seguir.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdatabinding)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdatabinding)]

10. Esse código cria uma instância do <xref:System.Data.Services.Client.DataServiceCollection%601> para o `Customers` tipo com base na execução de uma <xref:System.Data.Services.Client.DataServiceQuery%601> que retorna um <xref:System.Collections.Generic.IEnumerable%601> de `Customers` o Northwind dados de serviço e os associa a `customersBindingSource`.

## <a name="see-also"></a>Consulte também

- [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
- [Como: Associar dados aos elementos do Windows Presentation Foundation](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)
