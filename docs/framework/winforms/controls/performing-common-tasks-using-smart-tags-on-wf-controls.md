---
title: 'Passo a passo: Executando tarefas comuns usando marcas inteligentes nos controles do Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: 1cc854d735ba88a301d6e2f6a83fe5c8bf881380
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211412"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a><span data-ttu-id="63f20-102">Passo a passo: Executando tarefas comuns usando marcas inteligentes nos controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="63f20-102">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>

<span data-ttu-id="63f20-103">Ao construir formulários e controles para o seu Aplicativo dos Windows Forms, há várias tarefas que serão executadas repetidamente.</span><span class="sxs-lookup"><span data-stu-id="63f20-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="63f20-104">Estas são algumas das tarefas realizadas com frequência que você encontrará:</span><span class="sxs-lookup"><span data-stu-id="63f20-104">These are some of the commonly performed tasks you will encounter:</span></span>

- <span data-ttu-id="63f20-105">Adicionando ou removendo uma guia em um <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="63f20-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>

- <span data-ttu-id="63f20-106">Encaixando um controle ao pai.</span><span class="sxs-lookup"><span data-stu-id="63f20-106">Docking a control to its parent.</span></span>

- <span data-ttu-id="63f20-107">Alterando a orientação de um <xref:System.Windows.Forms.SplitContainer> controle.</span><span class="sxs-lookup"><span data-stu-id="63f20-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="63f20-108">Para acelerar o desenvolvimento, muitos controles oferecem smart tags, que são menus contextuais que permitem executar tarefas comuns como essas em um único gesto no tempo de design.</span><span class="sxs-lookup"><span data-stu-id="63f20-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="63f20-109">Essas tarefas são chamadas *verbos de marcas inteligentes*.</span><span class="sxs-lookup"><span data-stu-id="63f20-109">These tasks are called *smart-tag verbs*.</span></span>

<span data-ttu-id="63f20-110">Smart tags permaneçam anexadas a uma instância de controle por todo seu tempo de vida no designer e sempre estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="63f20-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

<span data-ttu-id="63f20-111">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="63f20-111">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="63f20-112">Criação de um projeto dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="63f20-112">Creating a Windows Forms project</span></span>

- <span data-ttu-id="63f20-113">Usando smart tags</span><span class="sxs-lookup"><span data-stu-id="63f20-113">Using smart tags</span></span>

- <span data-ttu-id="63f20-114">Habilitar e desabilitar smart tags</span><span class="sxs-lookup"><span data-stu-id="63f20-114">Enabling and Disabling Smart Tags</span></span>

<span data-ttu-id="63f20-115">Ao terminar, você terá um entendimento da função desempenhada por esses importantes recursos de layout.</span><span class="sxs-lookup"><span data-stu-id="63f20-115">When you are finished, you will have an understanding of the role played by these important layout features.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="63f20-116">Criar o projeto</span><span class="sxs-lookup"><span data-stu-id="63f20-116">Create the project</span></span>

<span data-ttu-id="63f20-117">A primeira etapa é criar o projeto e configurar o formulário.</span><span class="sxs-lookup"><span data-stu-id="63f20-117">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="63f20-118">No Visual Studio, crie um projeto de aplicativo baseado no Windows chamado "SmartTagsExample" (**arquivo** > **New** > **projeto**  >  **Visual C#**  ou **Visual Basic** > **área de trabalho clássica** > **Windows Forms Aplicativo**).</span><span class="sxs-lookup"><span data-stu-id="63f20-118">In Visual Studio, create a Windows-based application project called "SmartTagsExample" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="63f20-119">Selecione o formulário no **Designer de Formulários do Windows**.</span><span class="sxs-lookup"><span data-stu-id="63f20-119">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-smart-tags"></a><span data-ttu-id="63f20-120">Usar marcas inteligentes</span><span class="sxs-lookup"><span data-stu-id="63f20-120">Use smart tags</span></span>

<span data-ttu-id="63f20-121">Smart tags sempre estão disponíveis no tempo de design nos controles que as oferecem.</span><span class="sxs-lookup"><span data-stu-id="63f20-121">Smart tags are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="63f20-122">Arraste um <xref:System.Windows.Forms.TabControl> da **Caixa de Ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="63f20-122">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="63f20-123">Observe o glifo de marca inteligente (![glifo de Smart Tag](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) que aparece no lado do <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="63f20-123">Note the smart-tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="63f20-124">Clique no glifo de marca inteligente.</span><span class="sxs-lookup"><span data-stu-id="63f20-124">Click the smart-tag glyph.</span></span> <span data-ttu-id="63f20-125">No menu de atalho que aparece ao lado do glifo, selecione o item **Adicionar guia**.</span><span class="sxs-lookup"><span data-stu-id="63f20-125">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="63f20-126">Observe que uma nova página de guia é adicionada para o <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="63f20-126">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="63f20-127">Arraste uma <xref:System.Windows.Forms.TableLayoutPanel> controlar do **caixa de ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="63f20-127">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="63f20-128">Clique no glifo de marca inteligente.</span><span class="sxs-lookup"><span data-stu-id="63f20-128">Click the smart-tag glyph.</span></span> <span data-ttu-id="63f20-129">No menu de atalho que aparece ao lado do glifo, selecione o item **Adicionar coluna**.</span><span class="sxs-lookup"><span data-stu-id="63f20-129">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="63f20-130">Observe que uma nova coluna é adicionada para o <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="63f20-130">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="63f20-131">Arraste uma <xref:System.Windows.Forms.SplitContainer> controlar do **caixa de ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="63f20-131">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="63f20-132">Clique no glifo de marca inteligente.</span><span class="sxs-lookup"><span data-stu-id="63f20-132">Click the smart-tag glyph.</span></span> <span data-ttu-id="63f20-133">No menu de atalho que aparece ao lado do glifo, selecione o item **Orientação de divisor horizontal**.</span><span class="sxs-lookup"><span data-stu-id="63f20-133">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="63f20-134">Observe que o <xref:System.Windows.Forms.SplitContainer> barra divisora do controle é agora orientado horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="63f20-134">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="63f20-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63f20-135">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
- <span data-ttu-id="63f20-136">[Passo a passo: Adicionar marcas inteligentes a um componente do Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171829(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="63f20-136">[Walkthrough: Adding Smart Tags to a Windows Forms Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171829(v=vs.120))</span></span>
