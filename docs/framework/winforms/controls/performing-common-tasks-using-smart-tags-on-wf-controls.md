---
title: 'Instruções passo a passo: realizando tarefas comuns usando smart tags em controles dos Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: d1c69d2e9e89e0a4fed767216e8743a0ac9ac81d
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44201797"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a><span data-ttu-id="356fa-102">Instruções passo a passo: realizando tarefas comuns usando smart tags em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="356fa-102">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>
<span data-ttu-id="356fa-103">Ao construir formulários e controles para o seu Aplicativo dos Windows Forms, há várias tarefas que serão executadas repetidamente.</span><span class="sxs-lookup"><span data-stu-id="356fa-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="356fa-104">Estas são algumas das tarefas realizadas com frequência que você encontrará:</span><span class="sxs-lookup"><span data-stu-id="356fa-104">These are some of the commonly performed tasks you will encounter:</span></span>  
  
-   <span data-ttu-id="356fa-105">Adicionando ou removendo uma guia em um <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="356fa-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>  
  
-   <span data-ttu-id="356fa-106">Encaixando um controle ao pai.</span><span class="sxs-lookup"><span data-stu-id="356fa-106">Docking a control to its parent.</span></span>  
  
-   <span data-ttu-id="356fa-107">Alterando a orientação de um <xref:System.Windows.Forms.SplitContainer> controle.</span><span class="sxs-lookup"><span data-stu-id="356fa-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>  
  
 <span data-ttu-id="356fa-108">Para acelerar o desenvolvimento, muitos controles oferecem smart tags, que são menus contextuais que permitem executar tarefas comuns como essas em um único gesto no tempo de design.</span><span class="sxs-lookup"><span data-stu-id="356fa-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="356fa-109">Essas tarefas são chamadas *verbos de marcas inteligentes*.</span><span class="sxs-lookup"><span data-stu-id="356fa-109">These tasks are called *smart-tag verbs*.</span></span>  
  
 <span data-ttu-id="356fa-110">Smart tags permaneçam anexadas a uma instância de controle por todo seu tempo de vida no designer e sempre estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="356fa-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>  
  
 <span data-ttu-id="356fa-111">As tarefas ilustradas neste passo a passo incluem:</span><span class="sxs-lookup"><span data-stu-id="356fa-111">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="356fa-112">Criação de um projeto dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="356fa-112">Creating a Windows Forms project</span></span>  
  
-   <span data-ttu-id="356fa-113">Usando smart tags</span><span class="sxs-lookup"><span data-stu-id="356fa-113">Using smart tags</span></span>  
  
-   <span data-ttu-id="356fa-114">Habilitar e desabilitar smart tags</span><span class="sxs-lookup"><span data-stu-id="356fa-114">Enabling and Disabling Smart Tags</span></span>  
  
 <span data-ttu-id="356fa-115">Ao terminar, você terá um entendimento da função desempenhada por esses importantes recursos de layout.</span><span class="sxs-lookup"><span data-stu-id="356fa-115">When you are finished, you will have an understanding of the role played by these important layout features.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="356fa-116">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="356fa-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="356fa-117">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="356fa-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="356fa-118">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="356fa-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="356fa-119">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="356fa-119">Creating the Project</span></span>  
 <span data-ttu-id="356fa-120">A primeira etapa é criar o projeto e configurar o formulário.</span><span class="sxs-lookup"><span data-stu-id="356fa-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="356fa-121">Para criar o projeto</span><span class="sxs-lookup"><span data-stu-id="356fa-121">To create the project</span></span>  
  
1.  <span data-ttu-id="356fa-122">Criar um projeto de aplicativo baseado no Windows chamado "SmartTagsExample" (**arquivo** > **New** > **projeto**  >   **Visual c#** ou **Visual Basic** > **área de trabalho clássica** > **aplicativo de formulários do Windows**).</span><span class="sxs-lookup"><span data-stu-id="356fa-122">Create a Windows-based application project called "SmartTagsExample" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="356fa-123">Selecione o formulário no **Designer de Formulários do Windows**.</span><span class="sxs-lookup"><span data-stu-id="356fa-123">Select the form in the **Windows Forms Designer**.</span></span>  
  
## <a name="using-smart-tags"></a><span data-ttu-id="356fa-124">Usando Smart Tags</span><span class="sxs-lookup"><span data-stu-id="356fa-124">Using Smart Tags</span></span>  
 <span data-ttu-id="356fa-125">Smart tags sempre estão disponíveis no tempo de design nos controles que as oferecem.</span><span class="sxs-lookup"><span data-stu-id="356fa-125">Smart tags are always available at design time on controls that offer them.</span></span>  
  
#### <a name="to-use-smart-tags"></a><span data-ttu-id="356fa-126">Usar smart tags</span><span class="sxs-lookup"><span data-stu-id="356fa-126">To use smart tags</span></span>  
  
1.  <span data-ttu-id="356fa-127">Arraste um <xref:System.Windows.Forms.TabControl> da **Caixa de Ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="356fa-127">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="356fa-128">Observe o glifo de marca inteligente (![glifo de Smart Tag](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) que aparece no lado do <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="356fa-128">Note the smart-tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
2.  <span data-ttu-id="356fa-129">Clique no glifo de marca inteligente.</span><span class="sxs-lookup"><span data-stu-id="356fa-129">Click the smart-tag glyph.</span></span> <span data-ttu-id="356fa-130">No menu de atalho que aparece ao lado do glifo, selecione o item **Adicionar guia**.</span><span class="sxs-lookup"><span data-stu-id="356fa-130">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="356fa-131">Observe que uma nova página de guia é adicionada para o <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="356fa-131">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
3.  <span data-ttu-id="356fa-132">Arraste uma <xref:System.Windows.Forms.TableLayoutPanel> controlar do **caixa de ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="356fa-132">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
4.  <span data-ttu-id="356fa-133">Clique no glifo de marca inteligente.</span><span class="sxs-lookup"><span data-stu-id="356fa-133">Click the smart-tag glyph.</span></span> <span data-ttu-id="356fa-134">No menu de atalho que aparece ao lado do glifo, selecione o item **Adicionar coluna**.</span><span class="sxs-lookup"><span data-stu-id="356fa-134">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="356fa-135">Observe que uma nova coluna é adicionada para o <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="356fa-135">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
5.  <span data-ttu-id="356fa-136">Arraste uma <xref:System.Windows.Forms.SplitContainer> controlar do **caixa de ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="356fa-136">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>  
  
6.  <span data-ttu-id="356fa-137">Clique no glifo de marca inteligente.</span><span class="sxs-lookup"><span data-stu-id="356fa-137">Click the smart-tag glyph.</span></span> <span data-ttu-id="356fa-138">No menu de atalho que aparece ao lado do glifo, selecione o item **Orientação de divisor horizontal**.</span><span class="sxs-lookup"><span data-stu-id="356fa-138">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="356fa-139">Observe que o <xref:System.Windows.Forms.SplitContainer> barra divisora do controle é agora orientado horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="356fa-139">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="356fa-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="356fa-140">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 <xref:System.Windows.Forms.TabControl>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.ComponentModel.Design.DesignerActionList>  
 [<span data-ttu-id="356fa-141">Instruções passo a passo: adicionando smart tags a um componente dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="356fa-141">Walkthrough: Adding Smart Tags to a Windows Forms Component</span></span>](https://msdn.microsoft.com/library/a6814169-fa7d-4527-808c-637ca5c95f63)
