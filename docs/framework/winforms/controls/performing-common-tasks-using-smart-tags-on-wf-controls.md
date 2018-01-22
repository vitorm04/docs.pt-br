---
title: "Instruções passo a passo: realizando tarefas comuns usando smart tags em controles dos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2fb4e8bf710e55be0a817a4154dfbce114db191
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a><span data-ttu-id="d76d4-102">Instruções passo a passo: realizando tarefas comuns usando smart tags em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d76d4-102">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>
<span data-ttu-id="d76d4-103">Ao construir formulários e controles para o seu Aplicativo dos Windows Forms, há várias tarefas que serão executadas repetidamente.</span><span class="sxs-lookup"><span data-stu-id="d76d4-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="d76d4-104">Estas são algumas das tarefas realizadas com frequência que você encontrará:</span><span class="sxs-lookup"><span data-stu-id="d76d4-104">These are some of the commonly performed tasks you will encounter:</span></span>  
  
-   <span data-ttu-id="d76d4-105">Adição ou remoção de uma guia em um <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="d76d4-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>  
  
-   <span data-ttu-id="d76d4-106">Encaixando um controle ao pai.</span><span class="sxs-lookup"><span data-stu-id="d76d4-106">Docking a control to its parent.</span></span>  
  
-   <span data-ttu-id="d76d4-107">Alterar a orientação de um <xref:System.Windows.Forms.SplitContainer> controle.</span><span class="sxs-lookup"><span data-stu-id="d76d4-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>  
  
 <span data-ttu-id="d76d4-108">Para acelerar o desenvolvimento, muitos controles oferecem smart tags, que são menus contextuais que permitem executar tarefas comuns como essas em um único gesto no tempo de design.</span><span class="sxs-lookup"><span data-stu-id="d76d4-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="d76d4-109">Essas tarefas são chamadas *verbos de marcas inteligentes*.</span><span class="sxs-lookup"><span data-stu-id="d76d4-109">These tasks are called *smart-tag verbs*.</span></span>  
  
 <span data-ttu-id="d76d4-110">Smart tags permaneçam anexadas a uma instância de controle por todo seu tempo de vida no designer e sempre estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d76d4-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>  
  
 <span data-ttu-id="d76d4-111">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="d76d4-111">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="d76d4-112">Criação de um projeto dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d76d4-112">Creating a Windows Forms project</span></span>  
  
-   <span data-ttu-id="d76d4-113">Usando smart tags</span><span class="sxs-lookup"><span data-stu-id="d76d4-113">Using smart tags</span></span>  
  
-   <span data-ttu-id="d76d4-114">Habilitar e desabilitar smart tags</span><span class="sxs-lookup"><span data-stu-id="d76d4-114">Enabling and Disabling Smart Tags</span></span>  
  
 <span data-ttu-id="d76d4-115">Ao terminar, você terá um entendimento da função desempenhada por esses importantes recursos de layout.</span><span class="sxs-lookup"><span data-stu-id="d76d4-115">When you are finished, you will have an understanding of the role played by these important layout features.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d76d4-116">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="d76d4-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d76d4-117">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="d76d4-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d76d4-118">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="d76d4-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="d76d4-119">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="d76d4-119">Creating the Project</span></span>  
 <span data-ttu-id="d76d4-120">A primeira etapa é criar o projeto e configurar o formulário.</span><span class="sxs-lookup"><span data-stu-id="d76d4-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="d76d4-121">Para criar o projeto</span><span class="sxs-lookup"><span data-stu-id="d76d4-121">To create the project</span></span>  
  
1.  <span data-ttu-id="d76d4-122">Crie um projeto de aplicativo do Windows chamado “SmartTagsExample”.</span><span class="sxs-lookup"><span data-stu-id="d76d4-122">Create a Windows-based application project called "SmartTagsExample".</span></span> <span data-ttu-id="d76d4-123">Para obter detalhes, consulte [Como criar um projeto de aplicativo do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="d76d4-123">For details, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="d76d4-124">Selecione o formulário no **Designer de Formulários do Windows**.</span><span class="sxs-lookup"><span data-stu-id="d76d4-124">Select the form in the **Windows Forms Designer**.</span></span>  
  
## <a name="using-smart-tags"></a><span data-ttu-id="d76d4-125">Usando Smart Tags</span><span class="sxs-lookup"><span data-stu-id="d76d4-125">Using Smart Tags</span></span>  
 <span data-ttu-id="d76d4-126">Smart tags sempre estão disponíveis no tempo de design nos controles que as oferecem.</span><span class="sxs-lookup"><span data-stu-id="d76d4-126">Smart tags are always available at design time on controls that offer them.</span></span>  
  
#### <a name="to-use-smart-tags"></a><span data-ttu-id="d76d4-127">Usar smart tags</span><span class="sxs-lookup"><span data-stu-id="d76d4-127">To use smart tags</span></span>  
  
1.  <span data-ttu-id="d76d4-128">Arraste um <xref:System.Windows.Forms.TabControl> da **Caixa de Ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="d76d4-128">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="d76d4-129">Observe o símbolo de marca inteligente (![marca inteligente](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) que aparece no lado do <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="d76d4-129">Note the smart-tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
2.  <span data-ttu-id="d76d4-130">Clique no glifo de marca inteligente.</span><span class="sxs-lookup"><span data-stu-id="d76d4-130">Click the smart-tag glyph.</span></span> <span data-ttu-id="d76d4-131">No menu de atalho que aparece ao lado do glifo, selecione o item **Adicionar guia**.</span><span class="sxs-lookup"><span data-stu-id="d76d4-131">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="d76d4-132">Observe que uma página da guia novo é adicionada para o <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="d76d4-132">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
3.  <span data-ttu-id="d76d4-133">Arraste um <xref:System.Windows.Forms.TableLayoutPanel> controlar do **caixa de ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="d76d4-133">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
4.  <span data-ttu-id="d76d4-134">Clique no glifo de marca inteligente.</span><span class="sxs-lookup"><span data-stu-id="d76d4-134">Click the smart-tag glyph.</span></span> <span data-ttu-id="d76d4-135">No menu de atalho que aparece ao lado do glifo, selecione o item **Adicionar coluna**.</span><span class="sxs-lookup"><span data-stu-id="d76d4-135">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="d76d4-136">Observe que uma nova coluna é adicionada para o <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="d76d4-136">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
5.  <span data-ttu-id="d76d4-137">Arraste um <xref:System.Windows.Forms.SplitContainer> controlar do **caixa de ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="d76d4-137">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>  
  
6.  <span data-ttu-id="d76d4-138">Clique no glifo de marca inteligente.</span><span class="sxs-lookup"><span data-stu-id="d76d4-138">Click the smart-tag glyph.</span></span> <span data-ttu-id="d76d4-139">No menu de atalho que aparece ao lado do glifo, selecione o item **Orientação de divisor horizontal**.</span><span class="sxs-lookup"><span data-stu-id="d76d4-139">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="d76d4-140">Observe que o <xref:System.Windows.Forms.SplitContainer> barra de divisão do controle agora está orientado na horizontal.</span><span class="sxs-lookup"><span data-stu-id="d76d4-140">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d76d4-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d76d4-141">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 <xref:System.Windows.Forms.TabControl>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.ComponentModel.Design.DesignerActionList>  
 [<span data-ttu-id="d76d4-142">Instruções passo a passo: adicionando smart tags a um componente dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d76d4-142">Walkthrough: Adding Smart Tags to a Windows Forms Component</span></span>](http://msdn.microsoft.com/library/a6814169-fa7d-4527-808c-637ca5c95f63)
