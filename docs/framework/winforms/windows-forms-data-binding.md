---
title: "Associação de dados do Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 60a9f66fec64ceda71dd5b70211b897c84113429
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="windows-forms-data-binding"></a><span data-ttu-id="c93b0-102">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c93b0-102">Windows Forms Data Binding</span></span>
<span data-ttu-id="c93b0-103">A associação de dados no Windows Forms oferece os meios para exibir e realizar alterações nas informações de uma fonte de dados em controles no formulário.</span><span class="sxs-lookup"><span data-stu-id="c93b0-103">Data binding in Windows Forms gives you the means to display and make changes to information from a data source in controls on the form.</span></span> <span data-ttu-id="c93b0-104">É possível associar a fontes de dados tradicionais e a praticamente qualquer estrutura que contém dados.</span><span class="sxs-lookup"><span data-stu-id="c93b0-104">You can bind to both traditional data sources as well as almost any structure that contains data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c93b0-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c93b0-105">In This Section</span></span>  
 [<span data-ttu-id="c93b0-106">Associação de dados e o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c93b0-106">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 <span data-ttu-id="c93b0-107">Fornece uma visão geral da associação de dados no Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c93b0-107">Provides an overview of data binding in Windows Forms.</span></span>  
  
 [<span data-ttu-id="c93b0-108">Fontes de dados com suporte no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c93b0-108">Data Sources Supported by Windows Forms</span></span>](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 <span data-ttu-id="c93b0-109">Descreve as fontes de dados que podem ser usadas com o Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c93b0-109">Describes the data sources that can be used with Windows Forms.</span></span>  
  
 [<span data-ttu-id="c93b0-110">Interfaces relacionadas à associação de dados</span><span class="sxs-lookup"><span data-stu-id="c93b0-110">Interfaces Related to Data Binding</span></span>](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 <span data-ttu-id="c93b0-111">Descreve várias das interfaces usadas com a associação de dados do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c93b0-111">Describes several of the interfaces used with Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="c93b0-112">Como navegar por dados no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c93b0-112">How to: Navigate Data in Windows Forms</span></span>](../../../docs/framework/winforms/how-to-navigate-data-in-windows-forms.md)  
 <span data-ttu-id="c93b0-113">Mostra como navegar por itens em uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="c93b0-113">Shows how to navigate through items in a data source.</span></span>  
  
 [<span data-ttu-id="c93b0-114">Notificação de alteração na associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c93b0-114">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 <span data-ttu-id="c93b0-115">Descreve os diferentes tipos de notificação de alteração para associação de dados do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c93b0-115">Describes different types of change notification for Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="c93b0-116">Como implementar a interface INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="c93b0-116">How to: Implement the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 <span data-ttu-id="c93b0-117">Mostra como implementar a <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span><span class="sxs-lookup"><span data-stu-id="c93b0-117">Shows how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="c93b0-118">A interface se comunica com um controle associado alterado pela propriedade em um objeto de negócios</span><span class="sxs-lookup"><span data-stu-id="c93b0-118">The interface  communicates to a bound control the property changes on a business object</span></span>  
  
 [<span data-ttu-id="c93b0-119">Como aplicar o padrão PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="c93b0-119">How to: Apply the PropertyNameChanged Pattern</span></span>](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 <span data-ttu-id="c93b0-120">Mostra como aplicar o padrão *PropertyName*Changed nas propriedades de um controle de usuário do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c93b0-120">Shows how to apply the *PropertyName*Changed pattern to properties of a Windows Forms user control.</span></span>  
  
 [<span data-ttu-id="c93b0-121">Como implementar a interface ITypedList</span><span class="sxs-lookup"><span data-stu-id="c93b0-121">How to: Implement the ITypedList Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-itypedlist-interface.md)  
 <span data-ttu-id="c93b0-122">Mostra como habilitar a descoberta do esquema para obter uma lista associável Implementando o <xref:System.ComponentModel.ITypedList> interface.</span><span class="sxs-lookup"><span data-stu-id="c93b0-122">Shows how to enable discovery of the schema for a bindable list by implementing the <xref:System.ComponentModel.ITypedList> interface.</span></span>  
  
 [<span data-ttu-id="c93b0-123">Como implementar a interface IListSource</span><span class="sxs-lookup"><span data-stu-id="c93b0-123">How to: Implement the IListSource Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-ilistsource-interface.md)  
 <span data-ttu-id="c93b0-124">Mostra como implementar a <xref:System.ComponentModel.IListSource> não implementa a interface para criar uma classe associável <xref:System.Collections.IList>, mas fornece uma lista de outro local.</span><span class="sxs-lookup"><span data-stu-id="c93b0-124">Shows how to implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class does not implement <xref:System.Collections.IList>, but provides a list from another location.</span></span>  
  
 [<span data-ttu-id="c93b0-125">Como assegurar que vários controles associados à mesma fonte de dados permaneçam sincronizados</span><span class="sxs-lookup"><span data-stu-id="c93b0-125">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 <span data-ttu-id="c93b0-126">Mostra como tratar o <xref:System.Windows.Forms.BindingSource.BindingComplete> evento para garantir que todos os controles associados a uma fonte de dados permaneçam sincronizados.</span><span class="sxs-lookup"><span data-stu-id="c93b0-126">Shows how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event to ensure all controls bound to a data source remain synchronized.</span></span>  
  
 [<span data-ttu-id="c93b0-127">Como assegurar que a linha selecionada em uma tabela filho permaneça na posição correta</span><span class="sxs-lookup"><span data-stu-id="c93b0-127">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>](../../../docs/framework/winforms/ensure-the-selected-row-in-a-child-table-correct.md)  
 <span data-ttu-id="c93b0-128">Mostra como garantir que a linha selecionada de uma tabela filho não seja alterada quando uma alteração for feita em um campo da tabela pai.</span><span class="sxs-lookup"><span data-stu-id="c93b0-128">Shows how to ensure the selected row of a child table does not change, when a change is made to a field of the parent table.</span></span>  
  
 <span data-ttu-id="c93b0-129">Consulte também [Interfaces relacionadas à associação de dados](http://msdn.microsoft.com/library/41e17s4b\(v=vs.110\)), [Como navegar por dados no Windows Forms](http://msdn.microsoft.com/library/b63ha24w\(v=vs.110\)), [Como criar um controle associado simples em um Windows Form](http://msdn.microsoft.com/library/sw223a62\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="c93b0-129">Also see [Interfaces Related to Data Binding](http://msdn.microsoft.com/library/41e17s4b\(v=vs.110\)), [How to: Navigate Data in Windows Forms](http://msdn.microsoft.com/library/b63ha24w\(v=vs.110\)), [How to: Create a Simple-Bound Control on a Windows Form](http://msdn.microsoft.com/library/sw223a62\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c93b0-130">Referência</span><span class="sxs-lookup"><span data-stu-id="c93b0-130">Reference</span></span>  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 <span data-ttu-id="c93b0-131">Descreve a classe que representa a associação entre um componente vinculável e uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="c93b0-131">Describes the class that represents the binding between a bindable component and a data source.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 <span data-ttu-id="c93b0-132">Descreve a classe que encapsula uma fonte de dados para associação aos controles.</span><span class="sxs-lookup"><span data-stu-id="c93b0-132">Describes the class that encapsulates a data source for binding to controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c93b0-133">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="c93b0-133">Related Sections</span></span>  
 [<span data-ttu-id="c93b0-134">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="c93b0-134">BindingSource Component</span></span>](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 <span data-ttu-id="c93b0-135">Contém uma lista de tópicos que demonstram como usar o <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="c93b0-135">Contains a list of topics that demonstrate how to use the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="c93b0-136">Controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="c93b0-136">DataGridView Control</span></span>](../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 <span data-ttu-id="c93b0-137">Fornece uma lista de tópicos que demonstram como usar um controle datagrid vinculável.</span><span class="sxs-lookup"><span data-stu-id="c93b0-137">Provides a list of topics that demonstrate how to use a bindable datagrid control.</span></span>  
  
 <span data-ttu-id="c93b0-138">Consulte também [acessar dados no Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="c93b0-138">Also see [Accessing Data in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span></span>
