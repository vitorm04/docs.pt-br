---
title: Desenvolvendo controles dos Windows Forms na hora de design
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls [Windows Forms]
- Windows Forms controls, creating
- controls [Windows Forms]
- controls [Windows Forms], creating
- user controls [Windows Forms]
- custom controls [Windows Forms]
ms.assetid: e5a8e088-7ec8-4fd9-bcb3-9078fd134829
ms.openlocfilehash: 641a6c1c99169c6836c33b3e84b2ae02aba298d2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972231"
---
# <a name="developing-windows-forms-controls-at-design-time"></a><span data-ttu-id="30efe-102">Desenvolvendo controles dos Windows Forms na hora de design</span><span class="sxs-lookup"><span data-stu-id="30efe-102">Developing Windows Forms Controls at Design Time</span></span>
<span data-ttu-id="30efe-103">Para autores de controle, o .NET Framework fornece uma ampla variedade de tecnologia de criação de controle.</span><span class="sxs-lookup"><span data-stu-id="30efe-103">For control authors, the .NET Framework provides a wealth of control authoring technology.</span></span> <span data-ttu-id="30efe-104">Os autores não estão mais limitados a criar controles de composição que atuam como uma coleção de controles preexistentes.</span><span class="sxs-lookup"><span data-stu-id="30efe-104">Authors are no longer limited to designing composite controls that act as a collection of preexisting controls.</span></span> <span data-ttu-id="30efe-105">Por meio de herança, você pode criar seus próprios controles de com base em controles de composição preexistentes ou controles dos Windows Forms preexistentes.</span><span class="sxs-lookup"><span data-stu-id="30efe-105">Through inheritance, you can create your own controls from preexisting composite controls or preexisting Windows Forms controls.</span></span> <span data-ttu-id="30efe-106">Você também pode criar seus próprios controles que implementam pintura personalizada.</span><span class="sxs-lookup"><span data-stu-id="30efe-106">You can also design your own controls that implement custom painting.</span></span> <span data-ttu-id="30efe-107">Essas opções possibilitam muita flexibilidade no design e a funcionalidade da interface visual.</span><span class="sxs-lookup"><span data-stu-id="30efe-107">These options enable a great deal of flexibility to the design and functionality of the visual interface.</span></span> <span data-ttu-id="30efe-108">Para aproveitar esses recursos, familiarize-se com os conceitos de programação baseada em objeto.</span><span class="sxs-lookup"><span data-stu-id="30efe-108">To take advantage of these features, you should be familiar with object-based programming concepts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30efe-109">Não é necessário ter uma compreensão completa de herança, mas talvez você ache útil consultar [Noções básicas de herança (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="30efe-109">It is not necessary to have a thorough understanding of inheritance, but you may find it useful to refer to [Inheritance basics (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="30efe-110">Caso queira criar controles personalizados para usar em Web Forms, consulte [Desenvolvendo Controles Personalizados ASP.NET Server](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="30efe-110">If you want to create custom controls to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="30efe-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="30efe-111">In This Section</span></span>  
 [<span data-ttu-id="30efe-112">Passo a passo: Criando um controle composto com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="30efe-112">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 <span data-ttu-id="30efe-113">Mostra como criar um controle de composição simples em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="30efe-113">Shows how to create a simple composite control in Visual Basic.</span></span>  
  
 [<span data-ttu-id="30efe-114">Passo a passo: Criando um controle composto com VisualC#</span><span class="sxs-lookup"><span data-stu-id="30efe-114">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 <span data-ttu-id="30efe-115">Mostra como criar um controle de composição simples em C#.</span><span class="sxs-lookup"><span data-stu-id="30efe-115">Shows how to create a simple composite control in C#.</span></span>  
  
 [<span data-ttu-id="30efe-116">Passo a passo: Herdando um controle de formulários do Windows com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="30efe-116">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 <span data-ttu-id="30efe-117">Mostra como criar um controle simples dos Windows Forms usando herança no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="30efe-117">Shows how to create a simple Windows Forms control using inheritance in Visual Basic.</span></span>  
  
 [<span data-ttu-id="30efe-118">Passo a passo: Herdando um controle de formulários do Windows com VisualC#</span><span class="sxs-lookup"><span data-stu-id="30efe-118">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 <span data-ttu-id="30efe-119">Mostra como criar um controle simples dos Windows Forms usando herança em C#.</span><span class="sxs-lookup"><span data-stu-id="30efe-119">Shows how to create a simple Windows Forms control using inheritance in C#.</span></span>  
  
 [<span data-ttu-id="30efe-120">Passo a passo: Realizando tarefas comuns usando Smart Tags no Windows, controles de formulários</span><span class="sxs-lookup"><span data-stu-id="30efe-120">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 <span data-ttu-id="30efe-121">Mostra como usar o recurso de smart tag em controles dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="30efe-121">Shows how to use the smart tag feature on Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="30efe-122">Passo a passo: Serializando coleções de tipos padrão com DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="30efe-122">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)  
 <span data-ttu-id="30efe-123">Mostra como usar o <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> atributo para serializar uma coleção.</span><span class="sxs-lookup"><span data-stu-id="30efe-123">Shows how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> attribute to serialize a collection.</span></span>  
  
 [<span data-ttu-id="30efe-124">Passo a passo: Depuração de controles personalizados do Windows Forms em tempo de design</span><span class="sxs-lookup"><span data-stu-id="30efe-124">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 <span data-ttu-id="30efe-125">Mostra como depurar o comportamento de tempo de design de um controle dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="30efe-125">Shows how to debug the design-time behavior of a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="30efe-126">Passo a passo: Criando um controle de formulários do Windows que tira proveito dos recursos de tempo de Design do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="30efe-126">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)  
 <span data-ttu-id="30efe-127">Mostra como integrar fortemente um controle de composição ao ambiente de design.</span><span class="sxs-lookup"><span data-stu-id="30efe-127">Shows how to tightly integrate a composite control into the design environment.</span></span>  
  
 [<span data-ttu-id="30efe-128">Como: Criar controles para Windows Forms</span><span class="sxs-lookup"><span data-stu-id="30efe-128">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)  
 <span data-ttu-id="30efe-129">Apresenta uma visão geral de considerações para implementar um controle dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="30efe-129">Provides an overview of considerations for implementing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="30efe-130">Como: Criar controles compostos</span><span class="sxs-lookup"><span data-stu-id="30efe-130">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)  
 <span data-ttu-id="30efe-131">Mostra como criar um controle herdando de um controle de composição.</span><span class="sxs-lookup"><span data-stu-id="30efe-131">Shows how to create a control by inheriting from a composite control.</span></span>  
  
 [<span data-ttu-id="30efe-132">Como: Herdar da classe UserControl</span><span class="sxs-lookup"><span data-stu-id="30efe-132">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)  
 <span data-ttu-id="30efe-133">Fornece uma visão geral do procedimento para criar um controle de composição.</span><span class="sxs-lookup"><span data-stu-id="30efe-133">Provides an overview of the procedure for creating a composite control.</span></span>  
  
 [<span data-ttu-id="30efe-134">Como: Herdar controles de formulários do Windows existentes</span><span class="sxs-lookup"><span data-stu-id="30efe-134">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)  
 <span data-ttu-id="30efe-135">Mostra como criar um controle estendido herdando a <xref:System.Windows.Forms.Button> classe de controle.</span><span class="sxs-lookup"><span data-stu-id="30efe-135">Shows how to create an extended control by inheriting from the <xref:System.Windows.Forms.Button> control class.</span></span>  
  
 [<span data-ttu-id="30efe-136">Como: Herdar da classe de controle</span><span class="sxs-lookup"><span data-stu-id="30efe-136">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)  
 <span data-ttu-id="30efe-137">Apresenta uma visão geral da criação de um controle estendido.</span><span class="sxs-lookup"><span data-stu-id="30efe-137">Provides an overview of creating an extended control.</span></span>  
  
 [<span data-ttu-id="30efe-138">Como: Alinhar um controle às bordas de formulários no tempo de Design</span><span class="sxs-lookup"><span data-stu-id="30efe-138">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 <span data-ttu-id="30efe-139">Mostra como usar o <xref:System.Windows.Forms.Control.Dock%2A> propriedade para alinhar o controle na borda da forma que ele ocupa.</span><span class="sxs-lookup"><span data-stu-id="30efe-139">Shows how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>  
  
 [<span data-ttu-id="30efe-140">Como: Exibir um controle na caixa de diálogo de itens de caixa de ferramentas de escolha</span><span class="sxs-lookup"><span data-stu-id="30efe-140">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 <span data-ttu-id="30efe-141">Mostra o procedimento para instalar seu controle de modo que ele apareça na caixa de diálogo **Personalizar caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="30efe-141">Shows the procedure for installing your control so that it appears in the **Customize Toolbox** dialog box.</span></span>  
  
 [<span data-ttu-id="30efe-142">Como: Fornecer um Bitmap da caixa de ferramentas para um controle</span><span class="sxs-lookup"><span data-stu-id="30efe-142">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 <span data-ttu-id="30efe-143">Mostra como usar o <xref:System.Drawing.ToolboxBitmapAttribute> para exibir um ícone ao lado de seu controle personalizado na **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="30efe-143">Shows how to use the <xref:System.Drawing.ToolboxBitmapAttribute> to display an icon next to your custom control in the **Toolbox**.</span></span>  
  
 [<span data-ttu-id="30efe-144">Como: Testar o comportamento de tempo de execução de um UserControl</span><span class="sxs-lookup"><span data-stu-id="30efe-144">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 <span data-ttu-id="30efe-145">Mostra como usar o **Contêiner de Teste UserControl** para testar o comportamento de um controle de composição.</span><span class="sxs-lookup"><span data-stu-id="30efe-145">Shows how to use the **UserControl Test Container** to test the behavior of a composite control.</span></span>  
  
 [<span data-ttu-id="30efe-146">Erros de tempo de design no Designer de Formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="30efe-146">Design-Time Errors in the Windows Forms Designer</span></span>](design-time-errors-in-the-windows-forms-designer.md)  
 <span data-ttu-id="30efe-147">Explica o significado e o uso da lista de erros de tempo de design que aparece no Microsoft Visual Studio quando o carregamento do Designer de Formulários do Windows falha.</span><span class="sxs-lookup"><span data-stu-id="30efe-147">Explains the meaning and use of the Design-Time Error List that appears in Microsoft Visual Studio when the Windows Forms designer fails to load.</span></span>  
  
 [<span data-ttu-id="30efe-148">Solução de problemas de criação de controle e de componente</span><span class="sxs-lookup"><span data-stu-id="30efe-148">Troubleshooting Control and Component Authoring</span></span>](troubleshooting-control-and-component-authoring.md)  
 <span data-ttu-id="30efe-149">Mostra como diagnosticar e corrigir problemas comuns que podem ocorrer quando você criar um controle ou componente personalizado.</span><span class="sxs-lookup"><span data-stu-id="30efe-149">Shows how to diagnose and fix common issues that can occur when you author a custom component or control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="30efe-150">Referência</span><span class="sxs-lookup"><span data-stu-id="30efe-150">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="30efe-151">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="30efe-151">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="30efe-152">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="30efe-152">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="30efe-153">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="30efe-153">Related Sections</span></span>  
 [<span data-ttu-id="30efe-154">Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="30efe-154">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)  
 <span data-ttu-id="30efe-155">Discute como criar seus próprios controles personalizados com o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="30efe-155">Discusses how to create your own custom controls with the .NET Framework.</span></span>  
  
 [<span data-ttu-id="30efe-156">Componentes de independência de linguagem e componentes independentes da linguagem</span><span class="sxs-lookup"><span data-stu-id="30efe-156">Language Independence and Language-Independent Components</span></span>](../../../standard/language-independence-and-language-independent-components.md)  
 <span data-ttu-id="30efe-157">Apresenta o Common Language Runtime, que foi projetado para simplificar a criação e uso de componentes.</span><span class="sxs-lookup"><span data-stu-id="30efe-157">Introduces the common language runtime, which is designed to simplify the creation and use of components.</span></span> <span data-ttu-id="30efe-158">Um aspecto importante dessa simplificação é melhor interoperabilidade entre componentes escritos usando diferentes linguagens de programação.</span><span class="sxs-lookup"><span data-stu-id="30efe-158">An important aspect of this simplification is enhanced interoperability between components written using different programming languages.</span></span> <span data-ttu-id="30efe-159">A CLS (Common Language Specification) possibilita criar ferramentas e componentes que funcionam com várias linguagens de programação.</span><span class="sxs-lookup"><span data-stu-id="30efe-159">The Common Language Specification (CLS) makes it possible to create tools and components that work with multiple programming languages.</span></span>  
  
 [<span data-ttu-id="30efe-160">Passo a passo: Preenchendo automaticamente a caixa de ferramentas com componentes personalizados</span><span class="sxs-lookup"><span data-stu-id="30efe-160">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 <span data-ttu-id="30efe-161">Descreve como habilitar seu componente ou controle para ser exibido na caixa de diálogo **Personalizar Caixa de Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="30efe-161">Describes how to enable your component or control to be displayed in the **Customize Toolbox** dialog box.</span></span>
