---
title: 'Passo a passo: Executando tarefas comuns usando marcas inteligentes nos controles do Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 34c14c0afd9632b06947fd72e46ddbda070cfb0f
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015757"
---
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a><span data-ttu-id="c6d4f-102">Passo a passo: Executar tarefas comuns usando marcas inteligentes</span><span class="sxs-lookup"><span data-stu-id="c6d4f-102">Walkthrough: Perform Common Tasks Using Smart Tags</span></span>

<span data-ttu-id="c6d4f-103">Ao construir formulários e controles para o seu Aplicativo dos Windows Forms, há várias tarefas que serão executadas repetidamente.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="c6d4f-104">Estas são algumas das tarefas realizadas com frequência que você encontrará:</span><span class="sxs-lookup"><span data-stu-id="c6d4f-104">These are some of the commonly performed tasks you will encounter:</span></span>

- <span data-ttu-id="c6d4f-105">Adicionando ou removendo uma guia em <xref:System.Windows.Forms.TabControl>um.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>

- <span data-ttu-id="c6d4f-106">Encaixando um controle ao pai.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-106">Docking a control to its parent.</span></span>

- <span data-ttu-id="c6d4f-107">Alterando a orientação de <xref:System.Windows.Forms.SplitContainer> um controle.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="c6d4f-108">Para acelerar o desenvolvimento, muitos controles oferecem smart tags, que são menus contextuais que permitem executar tarefas comuns como essas em um único gesto no tempo de design.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="c6d4f-109">Essas tarefas são chamadas *verbos de marcas inteligentes*.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-109">These tasks are called *smart-tag verbs*.</span></span>

<span data-ttu-id="c6d4f-110">Smart tags permaneçam anexadas a uma instância de controle por todo seu tempo de vida no designer e sempre estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="c6d4f-111">Criar o projeto</span><span class="sxs-lookup"><span data-stu-id="c6d4f-111">Create the project</span></span>

<span data-ttu-id="c6d4f-112">A primeira etapa é criar o projeto e configurar o formulário.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-112">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="c6d4f-113">No Visual Studio, crie um projeto de aplicativo baseado no Windows chamado **SmartTagsExample**.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-113">In Visual Studio, create a Windows-based application project called **SmartTagsExample**.</span></span>

2. <span data-ttu-id="c6d4f-114">Selecione o formulário no **Designer de Formulários do Windows**.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-114">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-smart-tags"></a><span data-ttu-id="c6d4f-115">Usar marcas inteligentes</span><span class="sxs-lookup"><span data-stu-id="c6d4f-115">Use smart tags</span></span>

<span data-ttu-id="c6d4f-116">Smart tags sempre estão disponíveis no tempo de design nos controles que as oferecem.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-116">Smart tags are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="c6d4f-117">Arraste um <xref:System.Windows.Forms.TabControl> da **Caixa de Ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-117">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="c6d4f-118">Observe o glifo de marca inteligente (![glifo](./media/vs-winformsmttagglyph.gif)de marca inteligente) que aparece <xref:System.Windows.Forms.TabControl>no lado do.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-118">Note the smart-tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif)) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="c6d4f-119">Clique no glifo de marca inteligente.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-119">Click the smart-tag glyph.</span></span> <span data-ttu-id="c6d4f-120">No menu de atalho que aparece ao lado do glifo, selecione o item **Adicionar guia**.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-120">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="c6d4f-121">Observe que uma nova página da guia é adicionada ao <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-121">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="c6d4f-122">Arraste um <xref:System.Windows.Forms.TableLayoutPanel> controle da **caixa de ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-122">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="c6d4f-123">Clique no glifo de marca inteligente.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-123">Click the smart-tag glyph.</span></span> <span data-ttu-id="c6d4f-124">No menu de atalho que aparece ao lado do glifo, selecione o item **Adicionar coluna**.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-124">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="c6d4f-125">Observe que uma nova coluna é adicionada ao <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-125">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="c6d4f-126">Arraste um <xref:System.Windows.Forms.SplitContainer> controle da **caixa de ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-126">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="c6d4f-127">Clique no glifo de marca inteligente.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-127">Click the smart-tag glyph.</span></span> <span data-ttu-id="c6d4f-128">No menu de atalho que aparece ao lado do glifo, selecione o item **Orientação de divisor horizontal**.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-128">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="c6d4f-129">Observe que a <xref:System.Windows.Forms.SplitContainer> barra de divisão do controle agora é orientada horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="c6d4f-129">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6d4f-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6d4f-130">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
