---
title: Como adicionar detalhes de linha a um controle DataGrid
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: b6b0cc99c9833e514d2d52ecf139ab8e110f73e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555945"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a><span data-ttu-id="4d058-102">Como adicionar detalhes de linha a um controle DataGrid</span><span class="sxs-lookup"><span data-stu-id="4d058-102">How to: Add Row Details to a DataGrid Control</span></span>
<span data-ttu-id="4d058-103">Ao usar o <xref:System.Windows.Controls.DataGrid> controle, você pode personalizar a apresentação de dados com a adição de uma seção de detalhes da linha.</span><span class="sxs-lookup"><span data-stu-id="4d058-103">When using the <xref:System.Windows.Controls.DataGrid> control, you can customize the data presentation by adding a row details section.</span></span> <span data-ttu-id="4d058-104">Adicionar uma seção de detalhes de linha permite agrupar alguns dados em um modelo que fica opcionalmente visível ou recolhido.</span><span class="sxs-lookup"><span data-stu-id="4d058-104">Adding a row details section enables you to group some data in a template that is optionally visible or collapsed.</span></span> <span data-ttu-id="4d058-105">Por exemplo, você pode adicionar detalhes da linha para um <xref:System.Windows.Controls.DataGrid> que apresenta apenas um resumo dos dados para cada linha a <xref:System.Windows.Controls.DataGrid>, mas apresenta mais campos de dados quando o usuário seleciona uma linha.</span><span class="sxs-lookup"><span data-stu-id="4d058-105">For example, you can add row details to a <xref:System.Windows.Controls.DataGrid> that presents only a summary of the data for each row in the <xref:System.Windows.Controls.DataGrid>, but presents more data fields when the user selects a row.</span></span> <span data-ttu-id="4d058-106">Definir o modelo para a seção detalhes da linha de <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="4d058-106">You define the template for the row details section in the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property.</span></span> <span data-ttu-id="4d058-107">A ilustração a seguir mostra um exemplo de uma seção de detalhes da linha.</span><span class="sxs-lookup"><span data-stu-id="4d058-107">The following illustration shows an example of a row details section.</span></span>  
  
 <span data-ttu-id="4d058-108">![DataGrid mostrada com detalhes de linha](../../../../docs/framework/wpf/controls/media/ndp-rowdetails.png "NDP_RowDetails")</span><span class="sxs-lookup"><span data-stu-id="4d058-108">![DataGrid shown with row details](../../../../docs/framework/wpf/controls/media/ndp-rowdetails.png "NDP_RowDetails")</span></span>  
  
 <span data-ttu-id="4d058-109">Defina o modelo de detalhes de linha como XAML embutido ou como um recurso.</span><span class="sxs-lookup"><span data-stu-id="4d058-109">You define the row details template as either inline XAML or as a resource.</span></span> <span data-ttu-id="4d058-110">Ambas as abordagens são mostradas nos procedimentos a seguir.</span><span class="sxs-lookup"><span data-stu-id="4d058-110">Both approaches are shown in the following procedures.</span></span> <span data-ttu-id="4d058-111">Um modelo de dados adicionado como um recurso pode ser usado em todo o projeto sem recriar o modelo.</span><span class="sxs-lookup"><span data-stu-id="4d058-111">A data template that is added as a resource can be used throughout the project without re-creating the template.</span></span> <span data-ttu-id="4d058-112">Um modelo de dados que é adicionado como XAML embutido só é acessível pelo controle no qual ele está definido.</span><span class="sxs-lookup"><span data-stu-id="4d058-112">A data template that is added as inline XAML is only accessible from the control where it is defined.</span></span>  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a><span data-ttu-id="4d058-113">Para exibir detalhes de linha usando XAML embutido</span><span class="sxs-lookup"><span data-stu-id="4d058-113">To display row details by using inline XAML</span></span>  
  
1.  <span data-ttu-id="4d058-114">Criar um <xref:System.Windows.Controls.DataGrid> que exibe dados de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="4d058-114">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2.  <span data-ttu-id="4d058-115">No elemento <xref:System.Windows.Controls.DataGrid>, adicione um elemento <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="4d058-115">In the <xref:System.Windows.Controls.DataGrid> element, add a <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> element.</span></span>  
  
3.  <span data-ttu-id="4d058-116">Criar um <xref:System.Windows.DataTemplate> que define a aparência da seção de detalhes da linha.</span><span class="sxs-lookup"><span data-stu-id="4d058-116">Create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="4d058-117">O XAML a seguir mostra o <xref:System.Windows.Controls.DataGrid> e como definir o <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> embutido.</span><span class="sxs-lookup"><span data-stu-id="4d058-117">The following XAML shows the <xref:System.Windows.Controls.DataGrid> and how to define the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> inline.</span></span> <span data-ttu-id="4d058-118">O <xref:System.Windows.Controls.DataGrid> exibe três valores em cada linha e três valores mais quando a linha está selecionada.</span><span class="sxs-lookup"><span data-stu-id="4d058-118">The <xref:System.Windows.Controls.DataGrid> displays three values in each row and three more values when the row is selected.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     <span data-ttu-id="4d058-119">O código a seguir mostra a consulta que é usada para selecionar os dados que são exibidos no <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="4d058-119">The following code shows the query that is used to select the data that is displayed in the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="4d058-120">Neste exemplo, a consulta seleciona dados de uma entidade que contém informações de clientes.</span><span class="sxs-lookup"><span data-stu-id="4d058-120">In this example, the query selects data from an entity that contains customer information.</span></span>  
  
     [!code-csharp[DataGrid_RowDetails#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a><span data-ttu-id="4d058-121">Para exibir detalhes de linha usando um recurso</span><span class="sxs-lookup"><span data-stu-id="4d058-121">To display row details by using a resource</span></span>  
  
1.  <span data-ttu-id="4d058-122">Criar um <xref:System.Windows.Controls.DataGrid> que exibe dados de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="4d058-122">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2.  <span data-ttu-id="4d058-123">Adicionar um <xref:System.Windows.FrameworkElement.Resources%2A> elemento ao elemento raiz, como um <xref:System.Windows.Window> controle ou um <xref:System.Windows.Controls.Page> controlar ou adicionar um <xref:System.Windows.Application.Resources%2A> elemento para o <xref:System.Windows.Application> classe no arquivo App. XAML (ou Application).</span><span class="sxs-lookup"><span data-stu-id="4d058-123">Add a <xref:System.Windows.FrameworkElement.Resources%2A> element to the root element, such as a <xref:System.Windows.Window> control or a <xref:System.Windows.Controls.Page> control, or add a <xref:System.Windows.Application.Resources%2A> element to the <xref:System.Windows.Application> class in the App.xaml (or Application.xaml) file.</span></span>  
  
3.  <span data-ttu-id="4d058-124">O elemento de recursos, criar um <xref:System.Windows.DataTemplate> que define a aparência da seção de detalhes da linha.</span><span class="sxs-lookup"><span data-stu-id="4d058-124">In the resources element, create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="4d058-125">O XAML a seguir mostra o <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> definido no <xref:System.Windows.Application> classe.</span><span class="sxs-lookup"><span data-stu-id="4d058-125">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> defined in the <xref:System.Windows.Application> class.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4.  <span data-ttu-id="4d058-126">Sobre o <xref:System.Windows.DataTemplate>, defina o [diretiva X:Key](../../../../docs/framework/xaml-services/x-key-directive.md) para um valor que identifica exclusivamente o modelo de dados.</span><span class="sxs-lookup"><span data-stu-id="4d058-126">On the <xref:System.Windows.DataTemplate>, set the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) to a value that uniquely identifies the data template.</span></span>  
  
5.  <span data-ttu-id="4d058-127">No <xref:System.Windows.Controls.DataGrid> elemento, defina o <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> propriedade para o recurso definida nas etapas anteriores.</span><span class="sxs-lookup"><span data-stu-id="4d058-127">In the <xref:System.Windows.Controls.DataGrid> element, set the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property to the resource defined in the previous steps.</span></span> <span data-ttu-id="4d058-128">Atribua o recurso como um recurso estático.</span><span class="sxs-lookup"><span data-stu-id="4d058-128">Assign the resource as a static resource.</span></span>  
  
     <span data-ttu-id="4d058-129">O XAML a seguir mostra o <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> propriedade definida para o recurso do exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="4d058-129">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property set to the resource from the previous example.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a><span data-ttu-id="4d058-130">Para definir a visibilidade e evitar a rolagem horizontal para detalhes de linha</span><span class="sxs-lookup"><span data-stu-id="4d058-130">To set visibility and prevent horizontal scrolling for row details</span></span>  
  
1.  <span data-ttu-id="4d058-131">Se necessário, defina o <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> propriedade para um <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> valor.</span><span class="sxs-lookup"><span data-stu-id="4d058-131">If needed, set the <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> property to a <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> value.</span></span>  
  
     <span data-ttu-id="4d058-132">Por padrão, o valor é definido como <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span><span class="sxs-lookup"><span data-stu-id="4d058-132">By default, the value is set to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span></span> <span data-ttu-id="4d058-133">Você pode configurá-lo <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> para mostrar os detalhes de todas as linhas ou <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> para ocultar os detalhes de todas as linhas.</span><span class="sxs-lookup"><span data-stu-id="4d058-133">You can set it to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> to show the details for all of the rows or <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> to hide the details for all rows.</span></span>  
  
2.  <span data-ttu-id="4d058-134">Se necessário, defina o <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> propriedade `true` para impedir que a linha de detalhes de seção de rolagem horizontal.</span><span class="sxs-lookup"><span data-stu-id="4d058-134">If needed, set the <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> property to `true` to prevent the row details section from scrolling horizontally.</span></span>
