---
title: Associação de dados
description: Saiba como usar a vinculação de dados no Windows Forms para exibir e fazer alterações em informações de uma fonte de dados em controles no formulário.
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
ms.openlocfilehash: 3dfce24147caf9b138916ca8dc3b7a9010439f58
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325543"
---
# <a name="windows-forms-data-binding"></a><span data-ttu-id="c8d46-103">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c8d46-103">Windows Forms Data Binding</span></span>
<span data-ttu-id="c8d46-104">A associação de dados no Windows Forms oferece os meios para exibir e realizar alterações nas informações de uma fonte de dados em controles no formulário.</span><span class="sxs-lookup"><span data-stu-id="c8d46-104">Data binding in Windows Forms gives you the means to display and make changes to information from a data source in controls on the form.</span></span> <span data-ttu-id="c8d46-105">É possível associar a fontes de dados tradicionais e a praticamente qualquer estrutura que contém dados.</span><span class="sxs-lookup"><span data-stu-id="c8d46-105">You can bind to both traditional data sources as well as almost any structure that contains data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c8d46-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c8d46-106">In This Section</span></span>  
 [<span data-ttu-id="c8d46-107">Associação de dados e o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c8d46-107">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)  
 <span data-ttu-id="c8d46-108">Fornece uma visão geral da associação de dados no Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c8d46-108">Provides an overview of data binding in Windows Forms.</span></span>  
  
 [<span data-ttu-id="c8d46-109">Fontes de dados com suporte do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c8d46-109">Data Sources Supported by Windows Forms</span></span>](data-sources-supported-by-windows-forms.md)  
 <span data-ttu-id="c8d46-110">Descreve as fontes de dados que podem ser usadas com o Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c8d46-110">Describes the data sources that can be used with Windows Forms.</span></span>  
  
 [<span data-ttu-id="c8d46-111">Interfaces relacionadas à associação de dados</span><span class="sxs-lookup"><span data-stu-id="c8d46-111">Interfaces Related to Data Binding</span></span>](interfaces-related-to-data-binding.md)  
 <span data-ttu-id="c8d46-112">Descreve várias das interfaces usadas com a associação de dados do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c8d46-112">Describes several of the interfaces used with Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="c8d46-113">Como: navegar por dados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c8d46-113">How to: Navigate Data in Windows Forms</span></span>](how-to-navigate-data-in-windows-forms.md)  
 <span data-ttu-id="c8d46-114">Mostra como navegar por itens em uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="c8d46-114">Shows how to navigate through items in a data source.</span></span>  
  
 [<span data-ttu-id="c8d46-115">Notificação de alteração na associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c8d46-115">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)  
 <span data-ttu-id="c8d46-116">Descreve os diferentes tipos de notificação de alteração para associação de dados do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c8d46-116">Describes different types of change notification for Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="c8d46-117">Como: implementar a interface INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="c8d46-117">How to: Implement the INotifyPropertyChanged Interface</span></span>](how-to-implement-the-inotifypropertychanged-interface.md)  
 <span data-ttu-id="c8d46-118">Mostra como implementar a <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span><span class="sxs-lookup"><span data-stu-id="c8d46-118">Shows how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="c8d46-119">A interface se comunica com um controle associado alterado pela propriedade em um objeto de negócios</span><span class="sxs-lookup"><span data-stu-id="c8d46-119">The interface  communicates to a bound control the property changes on a business object</span></span>  
  
 [<span data-ttu-id="c8d46-120">Como: aplicar o padrão PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="c8d46-120">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)  
 <span data-ttu-id="c8d46-121">Mostra como aplicar o padrão *PropertyName*Changed nas propriedades de um controle de usuário do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c8d46-121">Shows how to apply the *PropertyName*Changed pattern to properties of a Windows Forms user control.</span></span>  
  
 [<span data-ttu-id="c8d46-122">Como: implementar a interface ITypedList</span><span class="sxs-lookup"><span data-stu-id="c8d46-122">How to: Implement the ITypedList Interface</span></span>](how-to-implement-the-itypedlist-interface.md)  
 <span data-ttu-id="c8d46-123">Mostra como habilitar a descoberta do esquema para uma lista vinculável implementando a <xref:System.ComponentModel.ITypedList> interface.</span><span class="sxs-lookup"><span data-stu-id="c8d46-123">Shows how to enable discovery of the schema for a bindable list by implementing the <xref:System.ComponentModel.ITypedList> interface.</span></span>  
  
 [<span data-ttu-id="c8d46-124">Como: implementar a interface IListSource</span><span class="sxs-lookup"><span data-stu-id="c8d46-124">How to: Implement the IListSource Interface</span></span>](how-to-implement-the-ilistsource-interface.md)  
 <span data-ttu-id="c8d46-125">Mostra como implementar a <xref:System.ComponentModel.IListSource> interface para criar uma classe vinculável não implementa <xref:System.Collections.IList> , mas fornece uma lista de outro local.</span><span class="sxs-lookup"><span data-stu-id="c8d46-125">Shows how to implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class does not implement <xref:System.Collections.IList>, but provides a list from another location.</span></span>  
  
 [<span data-ttu-id="c8d46-126">Como: assegurar que vários controles associados à mesma fonte de dados permaneçam sincronizados</span><span class="sxs-lookup"><span data-stu-id="c8d46-126">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](multiple-controls-bound-to-data-source-synchronized.md)  
 <span data-ttu-id="c8d46-127">Mostra como lidar com o <xref:System.Windows.Forms.BindingSource.BindingComplete> evento para garantir que todos os controles vinculados a uma fonte de dados permaneçam sincronizados.</span><span class="sxs-lookup"><span data-stu-id="c8d46-127">Shows how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event to ensure all controls bound to a data source remain synchronized.</span></span>  
  
 [<span data-ttu-id="c8d46-128">Como: assegurar que a linha selecionada em uma tabela filho permaneça na posição correta</span><span class="sxs-lookup"><span data-stu-id="c8d46-128">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>](ensure-the-selected-row-in-a-child-table-correct.md)  
 <span data-ttu-id="c8d46-129">Mostra como garantir que a linha selecionada de uma tabela filho não seja alterada quando uma alteração for feita em um campo da tabela pai.</span><span class="sxs-lookup"><span data-stu-id="c8d46-129">Shows how to ensure the selected row of a child table does not change, when a change is made to a field of the parent table.</span></span>  
  
 <span data-ttu-id="c8d46-130">Consulte também [interfaces relacionadas à vinculação de dados](interfaces-related-to-data-binding.md), [como navegar em dados em Windows Forms](how-to-navigate-data-in-windows-forms.md)e [como criar um controle de ligação simples em um Windows Form](how-to-create-a-simple-bound-control-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="c8d46-130">Also see [Interfaces Related to Data Binding](interfaces-related-to-data-binding.md), [How to: Navigate Data in Windows Forms](how-to-navigate-data-in-windows-forms.md), and [How to: Create a Simple-Bound Control on a Windows Form](how-to-create-a-simple-bound-control-on-a-windows-form.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c8d46-131">Referência</span><span class="sxs-lookup"><span data-stu-id="c8d46-131">Reference</span></span>  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 <span data-ttu-id="c8d46-132">Descreve a classe que representa a associação entre um componente vinculável e uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="c8d46-132">Describes the class that represents the binding between a bindable component and a data source.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 <span data-ttu-id="c8d46-133">Descreve a classe que encapsula uma fonte de dados para associação aos controles.</span><span class="sxs-lookup"><span data-stu-id="c8d46-133">Describes the class that encapsulates a data source for binding to controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c8d46-134">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="c8d46-134">Related Sections</span></span>  
 [<span data-ttu-id="c8d46-135">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="c8d46-135">BindingSource Component</span></span>](./controls/bindingsource-component.md)  
 <span data-ttu-id="c8d46-136">Contém uma lista de tópicos que demonstram como usar o <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="c8d46-136">Contains a list of topics that demonstrate how to use the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="c8d46-137">Controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="c8d46-137">DataGridView Control</span></span>](./controls/datagridview-control-windows-forms.md)  
 <span data-ttu-id="c8d46-138">Fornece uma lista de tópicos que demonstram como usar um controle datagrid vinculável.</span><span class="sxs-lookup"><span data-stu-id="c8d46-138">Provides a list of topics that demonstrate how to use a bindable datagrid control.</span></span>  
  
 <span data-ttu-id="c8d46-139">Consulte também [acessando dados no Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="c8d46-139">Also see [Accessing Data in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span></span>
