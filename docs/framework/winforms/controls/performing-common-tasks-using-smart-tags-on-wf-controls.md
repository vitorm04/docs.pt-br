---
title: Tarefas comuns de desempenho usando marcas inteligentes em controles
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 826313d0a89410f62c034a5fba4dee32e90a1750
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744265"
---
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a><span data-ttu-id="f170e-102">Walkthrough: executar tarefas comuns usando marcas inteligentes</span><span class="sxs-lookup"><span data-stu-id="f170e-102">Walkthrough: Perform Common Tasks Using Smart Tags</span></span>

<span data-ttu-id="f170e-103">Ao construir formulários e controles para o seu Aplicativo dos Windows Forms, há várias tarefas que serão executadas repetidamente.</span><span class="sxs-lookup"><span data-stu-id="f170e-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="f170e-104">Estas são algumas das tarefas realizadas com frequência que você encontrará:</span><span class="sxs-lookup"><span data-stu-id="f170e-104">These are some of the commonly performed tasks you will encounter:</span></span>

- <span data-ttu-id="f170e-105">Adicionar ou remover uma guia em um <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="f170e-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>

- <span data-ttu-id="f170e-106">Encaixando um controle ao pai.</span><span class="sxs-lookup"><span data-stu-id="f170e-106">Docking a control to its parent.</span></span>

- <span data-ttu-id="f170e-107">Alterar a orientação de um controle de <xref:System.Windows.Forms.SplitContainer>.</span><span class="sxs-lookup"><span data-stu-id="f170e-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="f170e-108">Para acelerar o desenvolvimento, muitos controles oferecem smart tags, que são menus contextuais que permitem executar tarefas comuns como essas em um único gesto no tempo de design.</span><span class="sxs-lookup"><span data-stu-id="f170e-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="f170e-109">Essas tarefas são chamadas *verbos de marcas inteligentes*.</span><span class="sxs-lookup"><span data-stu-id="f170e-109">These tasks are called *smart-tag verbs*.</span></span>

<span data-ttu-id="f170e-110">Smart tags permaneçam anexadas a uma instância de controle por todo seu tempo de vida no designer e sempre estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="f170e-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="f170e-111">Criar o projeto</span><span class="sxs-lookup"><span data-stu-id="f170e-111">Create the project</span></span>

<span data-ttu-id="f170e-112">A primeira etapa é criar o projeto e configurar o formulário.</span><span class="sxs-lookup"><span data-stu-id="f170e-112">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="f170e-113">No Visual Studio, crie um projeto de aplicativo baseado no Windows chamado **SmartTagsExample**.</span><span class="sxs-lookup"><span data-stu-id="f170e-113">In Visual Studio, create a Windows-based application project called **SmartTagsExample**.</span></span>

2. <span data-ttu-id="f170e-114">Selecione o formulário no **Designer de Formulários do Windows**.</span><span class="sxs-lookup"><span data-stu-id="f170e-114">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-smart-tags"></a><span data-ttu-id="f170e-115">Usar marcas inteligentes</span><span class="sxs-lookup"><span data-stu-id="f170e-115">Use smart tags</span></span>

<span data-ttu-id="f170e-116">Smart tags sempre estão disponíveis no tempo de design nos controles que as oferecem.</span><span class="sxs-lookup"><span data-stu-id="f170e-116">Smart tags are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="f170e-117">Arraste um <xref:System.Windows.Forms.TabControl> da **Caixa de Ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="f170e-117">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="f170e-118">Observe o glifo de marca inteligente (![glifo de marca inteligente](./media/vs-winformsmttagglyph.gif)) que aparece no lado do <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="f170e-118">Note the smart-tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif)) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="f170e-119">Clique no glifo de marca inteligente.</span><span class="sxs-lookup"><span data-stu-id="f170e-119">Click the smart-tag glyph.</span></span> <span data-ttu-id="f170e-120">No menu de atalho que aparece ao lado do glifo, selecione o item **Adicionar guia**.</span><span class="sxs-lookup"><span data-stu-id="f170e-120">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="f170e-121">Observe que uma nova página da guia é adicionada à <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="f170e-121">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="f170e-122">Arraste um controle de <xref:System.Windows.Forms.TableLayoutPanel> da **caixa de ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="f170e-122">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="f170e-123">Clique no glifo de marca inteligente.</span><span class="sxs-lookup"><span data-stu-id="f170e-123">Click the smart-tag glyph.</span></span> <span data-ttu-id="f170e-124">No menu de atalho que aparece ao lado do glifo, selecione o item **Adicionar coluna**.</span><span class="sxs-lookup"><span data-stu-id="f170e-124">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="f170e-125">Observe que uma nova coluna é adicionada ao controle de <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="f170e-125">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="f170e-126">Arraste um controle de <xref:System.Windows.Forms.SplitContainer> da **caixa de ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="f170e-126">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="f170e-127">Clique no glifo de marca inteligente.</span><span class="sxs-lookup"><span data-stu-id="f170e-127">Click the smart-tag glyph.</span></span> <span data-ttu-id="f170e-128">No menu de atalho que aparece ao lado do glifo, selecione o item **Orientação de divisor horizontal**.</span><span class="sxs-lookup"><span data-stu-id="f170e-128">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="f170e-129">Observe que a barra de divisão do controle de <xref:System.Windows.Forms.SplitContainer> agora é orientada horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="f170e-129">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="f170e-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="f170e-130">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
