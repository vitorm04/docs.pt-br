---
title: "Visão geral do controle BindingNavigator (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DataNavigator
helpviewer_keywords:
- BindingNavigator control [Windows Forms], about BindingNavigator control
- records [Windows Forms], navigating on a form
- data [Windows Forms], navigating
- data navigation
ms.assetid: 4423eede-f8d1-4d02-822f-5bf8432680d0
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 921f8c7791620d51107fa2ff31a637094fc0c633
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="bindingnavigator-control-overview-windows-forms"></a><span data-ttu-id="944ed-102">Visão geral do controle BindingNavigator (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="944ed-102">BindingNavigator Control Overview (Windows Forms)</span></span>
<span data-ttu-id="944ed-103">Você pode usar o <xref:System.Windows.Forms.BindingNavigator> controle para criar um meio padronizado para que os usuários de pesquisa e alterar dados em um Windows Form.</span><span class="sxs-lookup"><span data-stu-id="944ed-103">You can use the <xref:System.Windows.Forms.BindingNavigator> control to create a standardized means for users to search and change data on a Windows Form.</span></span> <span data-ttu-id="944ed-104">Você usa com frequência <xref:System.Windows.Forms.BindingNavigator> com o <xref:System.Windows.Forms.BindingSource> componente para permitir que os usuários percorrer os registros de dados em um formulário e interagir com os registros.</span><span class="sxs-lookup"><span data-stu-id="944ed-104">You frequently use <xref:System.Windows.Forms.BindingNavigator> with the <xref:System.Windows.Forms.BindingSource> component to enable users to move through data records on a form and interact with the records.</span></span>  
  
## <a name="how-the-bindingnavigator-works"></a><span data-ttu-id="944ed-105">Como o BindingNavigator funciona</span><span class="sxs-lookup"><span data-stu-id="944ed-105">How the BindingNavigator Works</span></span>  
 <span data-ttu-id="944ed-106">O <xref:System.Windows.Forms.BindingNavigator> controle é composto de um <xref:System.Windows.Forms.ToolStrip> com uma série de <xref:System.Windows.Forms.ToolStripItem> objetos para a maioria das ações relacionadas a dados comuns: adicionar dados, a exclusão de dados e navegar por dados.</span><span class="sxs-lookup"><span data-stu-id="944ed-106">The <xref:System.Windows.Forms.BindingNavigator> control is composed of a <xref:System.Windows.Forms.ToolStrip> with a series of <xref:System.Windows.Forms.ToolStripItem> objects for most of the common data-related actions: adding data, deleting data, and navigating through data.</span></span> <span data-ttu-id="944ed-107">Por padrão, o <xref:System.Windows.Forms.BindingNavigator> controle contém esse botões padrão.</span><span class="sxs-lookup"><span data-stu-id="944ed-107">By default, the <xref:System.Windows.Forms.BindingNavigator> control contains these standard buttons.</span></span> <span data-ttu-id="944ed-108">Captura de tela a seguir mostra o <xref:System.Windows.Forms.BindingNavigator> controle em um formulário.</span><span class="sxs-lookup"><span data-stu-id="944ed-108">The following screen shot shows the <xref:System.Windows.Forms.BindingNavigator> control on a form.</span></span>  
  
 <span data-ttu-id="944ed-109">![Controle BindingNavigator](../../../../docs/framework/winforms/controls/media/cpdatacontainerctrl.gif "cpDataContainerCtrl")</span><span class="sxs-lookup"><span data-stu-id="944ed-109">![BindingNavigator Control](../../../../docs/framework/winforms/controls/media/cpdatacontainerctrl.gif "cpDataContainerCtrl")</span></span>  
  
 <span data-ttu-id="944ed-110">A tabela a seguir lista os controles e descreve suas funções.</span><span class="sxs-lookup"><span data-stu-id="944ed-110">The following table lists the controls and describes their functions.</span></span>  
  
|<span data-ttu-id="944ed-111">Controle</span><span class="sxs-lookup"><span data-stu-id="944ed-111">Control</span></span>|<span data-ttu-id="944ed-112">Função</span><span class="sxs-lookup"><span data-stu-id="944ed-112">Function</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="944ed-113"><xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A>botão</span><span class="sxs-lookup"><span data-stu-id="944ed-113"><xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A> button</span></span>|<span data-ttu-id="944ed-114">Insere uma nova linha na fonte de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="944ed-114">Inserts a new row into the underlying data source.</span></span>|  
|<span data-ttu-id="944ed-115"><xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A>botão</span><span class="sxs-lookup"><span data-stu-id="944ed-115"><xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button</span></span>|<span data-ttu-id="944ed-116">Exclui a linha atual da fonte de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="944ed-116">Deletes the current row from the underlying data source.</span></span>|  
|<span data-ttu-id="944ed-117"><xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A>botão</span><span class="sxs-lookup"><span data-stu-id="944ed-117"><xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button</span></span>|<span data-ttu-id="944ed-118">Move para o primeiro item da fonte de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="944ed-118">Moves to the first item in the underlying data source.</span></span>|  
|<span data-ttu-id="944ed-119"><xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A>botão</span><span class="sxs-lookup"><span data-stu-id="944ed-119"><xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A> button</span></span>|<span data-ttu-id="944ed-120">Move para o último item da fonte de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="944ed-120">Moves to the last item in the underlying data source.</span></span>|  
|<span data-ttu-id="944ed-121"><xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A>botão</span><span class="sxs-lookup"><span data-stu-id="944ed-121"><xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A> button</span></span>|<span data-ttu-id="944ed-122">Move para o próximo item da fonte de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="944ed-122">Moves to the next item in the underlying data source.</span></span>|  
|<span data-ttu-id="944ed-123"><xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A>botão</span><span class="sxs-lookup"><span data-stu-id="944ed-123"><xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A> button</span></span>|<span data-ttu-id="944ed-124">Move para o item anterior da fonte de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="944ed-124">Moves to the previous item in the underlying data source.</span></span>|  
|<span data-ttu-id="944ed-125"><xref:System.Windows.Forms.BindingNavigator.PositionItem%2A>caixa de texto</span><span class="sxs-lookup"><span data-stu-id="944ed-125"><xref:System.Windows.Forms.BindingNavigator.PositionItem%2A> text box</span></span>|<span data-ttu-id="944ed-126">Retorna a posição atual na fonte de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="944ed-126">Returns the current position within the underlying data source.</span></span>|  
|<span data-ttu-id="944ed-127"><xref:System.Windows.Forms.BindingNavigator.CountItem%2A>caixa de texto</span><span class="sxs-lookup"><span data-stu-id="944ed-127"><xref:System.Windows.Forms.BindingNavigator.CountItem%2A> text box</span></span>|<span data-ttu-id="944ed-128">Retorna o número total de itens na fonte de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="944ed-128">Returns the total number of items in the underlying data source.</span></span>|  
  
 <span data-ttu-id="944ed-129">Para cada controle na coleção, existe um membro correspondente do <xref:System.Windows.Forms.BindingSource> componente que fornece a mesma funcionalidade programaticamente.</span><span class="sxs-lookup"><span data-stu-id="944ed-129">For each control in this collection, there is a corresponding member of the <xref:System.Windows.Forms.BindingSource> component that programmatically provides the same functionality.</span></span> <span data-ttu-id="944ed-130">Por exemplo, o <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> botão corresponde à <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> método do <xref:System.Windows.Forms.BindingSource> componente, o <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> botão corresponde à <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> método e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="944ed-130">For example, the <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> method of the <xref:System.Windows.Forms.BindingSource> component, the <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> method, and so on.</span></span>  
  
 <span data-ttu-id="944ed-131">Se os botões padrão não são adequados para seu aplicativo, ou se você precisar de botões adicionais para dar suporte a outros tipos de funcionalidade, você pode fornecer sua própria <xref:System.Windows.Forms.ToolStrip> botões.</span><span class="sxs-lookup"><span data-stu-id="944ed-131">If the default buttons are not suited to your application, or if you require additional buttons to support other types of functionality, you can supply your own <xref:System.Windows.Forms.ToolStrip> buttons.</span></span> <span data-ttu-id="944ed-132">Consulte também [Como adicionar botões Carregar, Salvar e Cancelar ao controle BindingNavigator do Windows Forms](../../../../docs/framework/winforms/controls/load-save-and-cancel-bindingnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="944ed-132">Also see [How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control](../../../../docs/framework/winforms/controls/load-save-and-cancel-bindingnavigator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="944ed-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="944ed-133">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="944ed-134">Controle BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="944ed-134">BindingNavigator Control</span></span>](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)
