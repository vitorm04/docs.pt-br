---
title: Componente BindingSource
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [Windows Forms], Windows Forms
- Windows Forms, data binding control
- BindingSource component [Windows Forms]
ms.assetid: 3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 08b55bc2bd5af78eb6c3d0f5adce3ec39d288a9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="bindingsource-component"></a><span data-ttu-id="19e3c-102">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="19e3c-102">BindingSource Component</span></span>
<span data-ttu-id="19e3c-103">Encapsula uma fonte de dados para associação aos controles.</span><span class="sxs-lookup"><span data-stu-id="19e3c-103">Encapsulates a data source for binding to controls.</span></span>  
  
 <span data-ttu-id="19e3c-104">O <xref:System.Windows.Forms.BindingSource> componente tem duas finalidades.</span><span class="sxs-lookup"><span data-stu-id="19e3c-104">The <xref:System.Windows.Forms.BindingSource> component serves two purposes.</span></span> <span data-ttu-id="19e3c-105">Primeiro, ele fornece uma camada de indireção ao associar os controles em um formulário de dados.</span><span class="sxs-lookup"><span data-stu-id="19e3c-105">First, it provides a layer of indirection when binding the controls on a form to data.</span></span> <span data-ttu-id="19e3c-106">Isso é feito pela associação a <xref:System.Windows.Forms.BindingSource> componente para sua fonte de dados e, em seguida, associar os controles no formulário para o <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="19e3c-106">This is accomplished by binding the <xref:System.Windows.Forms.BindingSource> component to your data source, and then binding the controls on your form to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="19e3c-107">Toda a interação adicional com os dados, incluindo navegar, classificação, filtragem e atualização, é feita com chamadas para o <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="19e3c-107">All further interaction with the data, including navigating, sorting, filtering, and updating, is accomplished with calls to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <span data-ttu-id="19e3c-108">Segundo, o <xref:System.Windows.Forms.BindingSource> componente pode agir como uma fonte de dados fortemente tipados.</span><span class="sxs-lookup"><span data-stu-id="19e3c-108">Second, the <xref:System.Windows.Forms.BindingSource> component can act as a strongly typed data source.</span></span> <span data-ttu-id="19e3c-109">Adicionar um tipo para o <xref:System.Windows.Forms.BindingSource> componente com o <xref:System.Windows.Forms.BindingSource.Add%2A> método cria uma lista desse tipo.</span><span class="sxs-lookup"><span data-stu-id="19e3c-109">Adding a type to the <xref:System.Windows.Forms.BindingSource> component with the <xref:System.Windows.Forms.BindingSource.Add%2A> method creates a list of that type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="19e3c-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="19e3c-110">In This Section</span></span>  
 [<span data-ttu-id="19e3c-111">Visão geral do componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="19e3c-111">BindingSource Component Overview</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 <span data-ttu-id="19e3c-112">Apresenta os conceitos gerais do <xref:System.Windows.Forms.BindingSource> componente, que permite que você associe uma fonte de dados a um controle.</span><span class="sxs-lookup"><span data-stu-id="19e3c-112">Introduces the general concepts of the <xref:System.Windows.Forms.BindingSource> component, which allows you to bind a data source to a control.</span></span>  
  
 [<span data-ttu-id="19e3c-113">Como associar controles dos Windows Forms a valores de banco de dados DBNull</span><span class="sxs-lookup"><span data-stu-id="19e3c-113">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-windows-forms-controls-to-dbnull-database-values.md)  
 <span data-ttu-id="19e3c-114">Mostra como tratar uma <xref:System.DBNull> valor da fonte de dados usando o <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="19e3c-114">Shows how to handle a <xref:System.DBNull> value from the data source using the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="19e3c-115">Como classificar e filtrar dados ADO.NET com o componente BindingSource dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="19e3c-115">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)  
 <span data-ttu-id="19e3c-116">Demonstra como usar o <xref:System.Windows.Forms.BindingSource> componente para aplicar classificações e filtros para dados exibidos.</span><span class="sxs-lookup"><span data-stu-id="19e3c-116">Demonstrates using the <xref:System.Windows.Forms.BindingSource> component to apply sorts and filters to displayed data.</span></span>  
  
 [<span data-ttu-id="19e3c-117">Como associar a um serviço Web usando o BindingSource do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="19e3c-117">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource.md)  
 <span data-ttu-id="19e3c-118">Mostra como usar o <xref:System.Windows.Forms.BindingSource> componente para vincular a um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="19e3c-118">Shows how to use the <xref:System.Windows.Forms.BindingSource> component to bind to a Web service.</span></span>  
  
 [<span data-ttu-id="19e3c-119">Como identificar erros e exceções que ocorram na associação de dados</span><span class="sxs-lookup"><span data-stu-id="19e3c-119">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 <span data-ttu-id="19e3c-120">Demonstra como usar o <xref:System.Windows.Forms.BindingSource> componente para manipular normalmente erros que ocorrem em uma operação de associação de dados.</span><span class="sxs-lookup"><span data-stu-id="19e3c-120">Demonstrates using the <xref:System.Windows.Forms.BindingSource> component to gracefully handle errors that occur in a data binding operation.</span></span>  
  
 [<span data-ttu-id="19e3c-121">Como associar um controle do Windows Forms a um tipo</span><span class="sxs-lookup"><span data-stu-id="19e3c-121">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 <span data-ttu-id="19e3c-122">Demonstra como usar um <xref:System.Windows.Forms.BindingSource> componente para vincular a um tipo.</span><span class="sxs-lookup"><span data-stu-id="19e3c-122">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind to a type.</span></span>  
  
 [<span data-ttu-id="19e3c-123">Como associar um controle do Windows Forms a um objeto de alocador</span><span class="sxs-lookup"><span data-stu-id="19e3c-123">How to: Bind a Windows Forms Control to a Factory Object</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-factory-object.md)  
 <span data-ttu-id="19e3c-124">Demonstra como usar um <xref:System.Windows.Forms.BindingSource> componente para vincular a um objeto de fábrica ou método.</span><span class="sxs-lookup"><span data-stu-id="19e3c-124">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind to a factory object or method.</span></span>  
  
 [<span data-ttu-id="19e3c-125">Como personalizar a adição de item com o BindingSource dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="19e3c-125">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)  
 <span data-ttu-id="19e3c-126">Demonstra como usar um <xref:System.Windows.Forms.BindingSource> componente para criar novos itens e adicioná-los a uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="19e3c-126">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to create new items and add them to a data source.</span></span>  
  
 [<span data-ttu-id="19e3c-127">Como acionar notificações de alteração usando o método BindingSource ResetItem</span><span class="sxs-lookup"><span data-stu-id="19e3c-127">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)  
 <span data-ttu-id="19e3c-128">Demonstra como usar um <xref:System.Windows.Forms.BindingSource> componente para gerar eventos de notificação de alteração para fontes de dados que não oferecem suporte a notificação de alteração.</span><span class="sxs-lookup"><span data-stu-id="19e3c-128">Demonstrates using a <xref:System.Windows.Forms.BindingSource> component to raise change-notification events for data sources that do not support change notification.</span></span>  
  
 [<span data-ttu-id="19e3c-129">Como gerar notificações de alteração usando um BindingSource e a interface INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="19e3c-129">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](../../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 <span data-ttu-id="19e3c-130">Demonstra como usar um tipo que herda o <xref:System.ComponentModel.INotifyPropertyChanged> com um <xref:System.Windows.Forms.BindingSource> controle.</span><span class="sxs-lookup"><span data-stu-id="19e3c-130">Demonstrates how to use a type that inherits from the <xref:System.ComponentModel.INotifyPropertyChanged> with a <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
 [<span data-ttu-id="19e3c-131">Como refletir atualizações feitas na fonte de dados em um controle do Windows Forms com o BindingSource</span><span class="sxs-lookup"><span data-stu-id="19e3c-131">How to: Reflect Data Source Updates in a Windows Forms Control with the BindingSource</span></span>](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)  
 <span data-ttu-id="19e3c-132">Demonstra como responder a alterações na fonte de dados usando o <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="19e3c-132">Demonstrates how to respond to changes in the data source using the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="19e3c-133">Como compartilhar dados associados entre formulários usando o componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="19e3c-133">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 <span data-ttu-id="19e3c-134">Mostra como usar o <xref:System.Windows.Forms.BindingSource> para associar várias formas à mesma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="19e3c-134">Shows how to use the <xref:System.Windows.Forms.BindingSource> to bind multiple forms to the same data source.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="19e3c-135">Referência</span><span class="sxs-lookup"><span data-stu-id="19e3c-135">Reference</span></span>  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="19e3c-136">Fornece documentação de referência para o <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="19e3c-136">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <xref:System.Windows.Forms.BindingNavigator>  
 <span data-ttu-id="19e3c-137">Fornece documentação de referência para o <xref:System.Windows.Forms.BindingNavigator> controle.</span><span class="sxs-lookup"><span data-stu-id="19e3c-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="19e3c-138">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="19e3c-138">Related Sections</span></span>  
 [<span data-ttu-id="19e3c-139">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="19e3c-139">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 <span data-ttu-id="19e3c-140">Contém links para tópicos que descrevem a arquitetura de associação de dados do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="19e3c-140">Contains links to topics describing the Windows Forms data binding architecture.</span></span>  
  
 <span data-ttu-id="19e3c-141">Consulte também [Associar controles a dados no Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="19e3c-141">Also see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>
