---
title: Executar tarefas comuns usando ações de designer em controles
ms.date: 02/13/2019
helpviewer_keywords:
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 342741b9ce032b1b8ec50a6c689d9109d12f5b3b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634879"
---
# <a name="walkthrough-perform-common-tasks-using-designer-actions"></a><span data-ttu-id="b5f91-102">Walkthrough: executar tarefas comuns usando ações de designer</span><span class="sxs-lookup"><span data-stu-id="b5f91-102">Walkthrough: Perform common tasks using designer actions</span></span>

<span data-ttu-id="b5f91-103">À medida que você constrói formulários e controles para seu aplicativo Windows Forms, há muitas tarefas que você executará repetidamente.</span><span class="sxs-lookup"><span data-stu-id="b5f91-103">As you construct forms and controls for your Windows Forms application, there are many tasks you'll perform repeatedly.</span></span> <span data-ttu-id="b5f91-104">A lista a seguir mostra algumas das tarefas executadas com frequência que você virá:</span><span class="sxs-lookup"><span data-stu-id="b5f91-104">The following list shows some of the commonly performed tasks you'll come across:</span></span>

- <span data-ttu-id="b5f91-105">Adicionar ou remover uma guia em um <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="b5f91-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>
- <span data-ttu-id="b5f91-106">Encaixando um controle ao pai.</span><span class="sxs-lookup"><span data-stu-id="b5f91-106">Docking a control to its parent.</span></span>
- <span data-ttu-id="b5f91-107">Alterar a orientação de um controle de <xref:System.Windows.Forms.SplitContainer>.</span><span class="sxs-lookup"><span data-stu-id="b5f91-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="b5f91-108">Para agilizar o desenvolvimento, muitos controles oferecem ações de designer, que são menus sensíveis ao contexto que permitem executar tarefas comuns como essas em um único gesto no tempo de design.</span><span class="sxs-lookup"><span data-stu-id="b5f91-108">To speed development, many controls offer designer actions, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="b5f91-109">Essas tarefas são chamadas de *verbos de ações do designer*.</span><span class="sxs-lookup"><span data-stu-id="b5f91-109">These tasks are called *designer actions verbs*.</span></span>

<span data-ttu-id="b5f91-110">As ações do designer permanecem anexadas a uma instância de controle durante seu tempo de vida no designer e estão sempre disponíveis.</span><span class="sxs-lookup"><span data-stu-id="b5f91-110">Designer actions remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="b5f91-111">Criar o projeto</span><span class="sxs-lookup"><span data-stu-id="b5f91-111">Create the project</span></span>

<span data-ttu-id="b5f91-112">A primeira etapa é criar o projeto e configurar o formulário.</span><span class="sxs-lookup"><span data-stu-id="b5f91-112">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="b5f91-113">No Visual Studio, crie um projeto de aplicativo baseado no Windows chamado **DesignerActionsExample**.</span><span class="sxs-lookup"><span data-stu-id="b5f91-113">In Visual Studio, create a Windows-based application project called **DesignerActionsExample**.</span></span>

2. <span data-ttu-id="b5f91-114">Selecione o formulário no **Designer de Formulários do Windows**.</span><span class="sxs-lookup"><span data-stu-id="b5f91-114">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-designer-actions"></a><span data-ttu-id="b5f91-115">Usar ações do designer</span><span class="sxs-lookup"><span data-stu-id="b5f91-115">Use designer actions</span></span>

<span data-ttu-id="b5f91-116">As ações do designer estão sempre disponíveis em tempo de design em controles que as oferecem.</span><span class="sxs-lookup"><span data-stu-id="b5f91-116">Designer actions are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="b5f91-117">Arraste um <xref:System.Windows.Forms.TabControl> da **Caixa de Ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="b5f91-117">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="b5f91-118">Observe o glifo ações do designer (![seta preta pequena](./media/designer-actions-glyph.gif)) que aparece no lado do <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="b5f91-118">Note the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="b5f91-119">Clique no glifo ações do designer.</span><span class="sxs-lookup"><span data-stu-id="b5f91-119">Click the designer actions glyph.</span></span> <span data-ttu-id="b5f91-120">No menu de atalho que aparece ao lado do glifo, selecione o item **Adicionar guia**.</span><span class="sxs-lookup"><span data-stu-id="b5f91-120">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="b5f91-121">Observe que uma nova página da guia é adicionada à <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="b5f91-121">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="b5f91-122">Arraste um controle de <xref:System.Windows.Forms.TableLayoutPanel> da **caixa de ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="b5f91-122">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="b5f91-123">Clique no glifo ações do designer.</span><span class="sxs-lookup"><span data-stu-id="b5f91-123">Click the designer actions glyph.</span></span> <span data-ttu-id="b5f91-124">No menu de atalho que aparece ao lado do glifo, selecione o item **Adicionar coluna**.</span><span class="sxs-lookup"><span data-stu-id="b5f91-124">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="b5f91-125">Observe que uma nova coluna é adicionada ao controle de <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="b5f91-125">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="b5f91-126">Arraste um controle de <xref:System.Windows.Forms.SplitContainer> da **caixa de ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="b5f91-126">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="b5f91-127">Clique no glifo ações do designer.</span><span class="sxs-lookup"><span data-stu-id="b5f91-127">Click the designer actions glyph.</span></span> <span data-ttu-id="b5f91-128">No menu de atalho que aparece ao lado do glifo, selecione o item de **orientação de divisor horizontal** .</span><span class="sxs-lookup"><span data-stu-id="b5f91-128">In the shortcut menu that appears next to the glyph, select the **Horizontal Splitter Orientation** item.</span></span> <span data-ttu-id="b5f91-129">Observe que a barra de divisão do controle de <xref:System.Windows.Forms.SplitContainer> agora é orientada horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="b5f91-129">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5f91-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="b5f91-130">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
