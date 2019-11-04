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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f6afb13a01075d3aa2d101100a0c3bfe31c6ee29
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460086"
---
# <a name="develop-windows-forms-controls-at-design-time"></a><span data-ttu-id="a0a77-102">Desenvolver Windows Forms controles em tempo de design</span><span class="sxs-lookup"><span data-stu-id="a0a77-102">Develop Windows Forms controls at design time</span></span>

<span data-ttu-id="a0a77-103">Para autores de controle, o .NET Framework fornece uma ampla variedade de tecnologia de criação de controle.</span><span class="sxs-lookup"><span data-stu-id="a0a77-103">For control authors, the .NET Framework provides a wealth of control authoring technology.</span></span> <span data-ttu-id="a0a77-104">Os autores não estão mais limitados a criar controles de composição que atuam como uma coleção de controles preexistentes.</span><span class="sxs-lookup"><span data-stu-id="a0a77-104">Authors are no longer limited to designing composite controls that act as a collection of preexisting controls.</span></span> <span data-ttu-id="a0a77-105">Por meio de herança, você pode criar seus próprios controles de com base em controles de composição preexistentes ou controles dos Windows Forms preexistentes.</span><span class="sxs-lookup"><span data-stu-id="a0a77-105">Through inheritance, you can create your own controls from preexisting composite controls or preexisting Windows Forms controls.</span></span> <span data-ttu-id="a0a77-106">Você também pode criar seus próprios controles que implementam pintura personalizada.</span><span class="sxs-lookup"><span data-stu-id="a0a77-106">You can also design your own controls that implement custom painting.</span></span> <span data-ttu-id="a0a77-107">Essas opções possibilitam muita flexibilidade no design e a funcionalidade da interface visual.</span><span class="sxs-lookup"><span data-stu-id="a0a77-107">These options enable a great deal of flexibility to the design and functionality of the visual interface.</span></span> <span data-ttu-id="a0a77-108">Para aproveitar esses recursos, familiarize-se com os conceitos de programação baseada em objeto.</span><span class="sxs-lookup"><span data-stu-id="a0a77-108">To take advantage of these features, you should be familiar with object-based programming concepts.</span></span>

> [!NOTE]
> <span data-ttu-id="a0a77-109">Não é necessário ter uma compreensão completa da herança, mas talvez seja útil consultar [noções básicas de herança (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="a0a77-109">It is not necessary to have a thorough understanding of inheritance, but you may find it useful to refer to [Inheritance basics (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>

<span data-ttu-id="a0a77-110">Caso queira criar controles personalizados para usar em Web Forms, consulte [Desenvolvendo Controles Personalizados ASP.NET Server](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a0a77-110">If you want to create custom controls to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a0a77-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="a0a77-111">In this section</span></span>

<span data-ttu-id="a0a77-112">[Walkthrough: Criando um controle composto](walkthrough-authoring-a-composite-control-with-visual-csharp.md)</span><span class="sxs-lookup"><span data-stu-id="a0a77-112">[Walkthrough: Authoring a Composite Control](walkthrough-authoring-a-composite-control-with-visual-csharp.md)</span></span>\
<span data-ttu-id="a0a77-113">Mostra como criar um controle de composição simples em C#.</span><span class="sxs-lookup"><span data-stu-id="a0a77-113">Shows how to create a simple composite control in C#.</span></span>

<span data-ttu-id="a0a77-114">[Walkthrough: herdar de um controle de Windows Forms](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)</span><span class="sxs-lookup"><span data-stu-id="a0a77-114">[Walkthrough: Inheriting from a Windows Forms Control](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)</span></span>\
<span data-ttu-id="a0a77-115">Mostra como criar um controle simples dos Windows Forms usando herança em C#.</span><span class="sxs-lookup"><span data-stu-id="a0a77-115">Shows how to create a simple Windows Forms control using inheritance in C#.</span></span>

<span data-ttu-id="a0a77-116">[Passo a passo: realizando tarefas comuns usando smart tags em controles dos Windows Forms](performing-common-tasks-using-smart-tags-on-wf-controls.md)</span><span class="sxs-lookup"><span data-stu-id="a0a77-116">[Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls](performing-common-tasks-using-smart-tags-on-wf-controls.md)</span></span>\
<span data-ttu-id="a0a77-117">Mostra como usar o recurso de smart tag em controles dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a0a77-117">Shows how to use the smart tag feature on Windows Forms controls.</span></span>

<span data-ttu-id="a0a77-118">[Walkthrough: Serializando coleções de tipos padrão com o DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)</span><span class="sxs-lookup"><span data-stu-id="a0a77-118">[Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)</span></span>\
<span data-ttu-id="a0a77-119">Mostra como usar o atributo <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> para serializar uma coleção.</span><span class="sxs-lookup"><span data-stu-id="a0a77-119">Shows how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> attribute to serialize a collection.</span></span>

<span data-ttu-id="a0a77-120">[Instruções passo a passo: depurando controles personalizados do Windows Forms no tempo de design](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)</span><span class="sxs-lookup"><span data-stu-id="a0a77-120">[Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)</span></span>\
<span data-ttu-id="a0a77-121">Mostra como depurar o comportamento de tempo de design de um controle dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a0a77-121">Shows how to debug the design-time behavior of a Windows Forms control.</span></span>

<span data-ttu-id="a0a77-122">[Passo a passo: criando um controle dos Windows Forms que aproveita os recursos de tempo de design do Visual Studio](creating-a-wf-control-design-time-features.md)</span><span class="sxs-lookup"><span data-stu-id="a0a77-122">[Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md)</span></span>\
<span data-ttu-id="a0a77-123">Mostra como integrar fortemente um controle de composição ao ambiente de design.</span><span class="sxs-lookup"><span data-stu-id="a0a77-123">Shows how to tightly integrate a composite control into the design environment.</span></span>

<span data-ttu-id="a0a77-124">[Como Criar Controles para o Windows Forms](how-to-author-controls-for-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="a0a77-124">[How to: Author Controls for Windows Forms](how-to-author-controls-for-windows-forms.md)</span></span>\
<span data-ttu-id="a0a77-125">Apresenta uma visão geral de considerações para implementar um controle dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a0a77-125">Provides an overview of considerations for implementing a Windows Forms control.</span></span>

<span data-ttu-id="a0a77-126">[Como criar controles de composição](how-to-author-composite-controls.md)</span><span class="sxs-lookup"><span data-stu-id="a0a77-126">[How to: Author Composite Controls](how-to-author-composite-controls.md)</span></span>\
<span data-ttu-id="a0a77-127">Mostra como criar um controle herdando de um controle de composição.</span><span class="sxs-lookup"><span data-stu-id="a0a77-127">Shows how to create a control by inheriting from a composite control.</span></span>

<span data-ttu-id="a0a77-128">[Como herdar da classe UserControl](how-to-inherit-from-the-usercontrol-class.md)</span><span class="sxs-lookup"><span data-stu-id="a0a77-128">[How to: Inherit from the UserControl Class](how-to-inherit-from-the-usercontrol-class.md)</span></span>\
<span data-ttu-id="a0a77-129">Fornece uma visão geral do procedimento para criar um controle de composição.</span><span class="sxs-lookup"><span data-stu-id="a0a77-129">Provides an overview of the procedure for creating a composite control.</span></span>

<span data-ttu-id="a0a77-130">[Como herdar de controles do Windows Forms existentes](how-to-inherit-from-existing-windows-forms-controls.md)</span><span class="sxs-lookup"><span data-stu-id="a0a77-130">[How to: Inherit from Existing Windows Forms Controls](how-to-inherit-from-existing-windows-forms-controls.md)</span></span>\
<span data-ttu-id="a0a77-131">Mostra como criar um controle estendido herdando da classe de controle <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="a0a77-131">Shows how to create an extended control by inheriting from the <xref:System.Windows.Forms.Button> control class.</span></span>

<span data-ttu-id="a0a77-132">[Como herdar da classe de controle](how-to-inherit-from-the-control-class.md)</span><span class="sxs-lookup"><span data-stu-id="a0a77-132">[How to: Inherit from the Control Class](how-to-inherit-from-the-control-class.md)</span></span>\
<span data-ttu-id="a0a77-133">Apresenta uma visão geral da criação de um controle estendido.</span><span class="sxs-lookup"><span data-stu-id="a0a77-133">Provides an overview of creating an extended control.</span></span>

<span data-ttu-id="a0a77-134">[Como alinhar um controle às bordas de formulários no tempo de design](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)</span><span class="sxs-lookup"><span data-stu-id="a0a77-134">[How to: Align a Control to the Edges of Forms at Design Time](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)</span></span>\
<span data-ttu-id="a0a77-135">Mostra como usar a propriedade <xref:System.Windows.Forms.Control.Dock%2A> para alinhar seu controle à borda do formulário que ele ocupa.</span><span class="sxs-lookup"><span data-stu-id="a0a77-135">Shows how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>

<span data-ttu-id="a0a77-136">[Como exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="a0a77-136">[How to: Display a Control in the Choose Toolbox Items Dialog Box](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span></span>\
<span data-ttu-id="a0a77-137">Mostra o procedimento para instalar seu controle de modo que ele apareça na caixa de diálogo **Personalizar caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="a0a77-137">Shows the procedure for installing your control so that it appears in the **Customize Toolbox** dialog box.</span></span>

<span data-ttu-id="a0a77-138">[Como: fornecer um bitmap de caixa de ferramentas para um controle](how-to-provide-a-toolbox-bitmap-for-a-control.md)</span><span class="sxs-lookup"><span data-stu-id="a0a77-138">[How to: Provide a Toolbox Bitmap for a Control](how-to-provide-a-toolbox-bitmap-for-a-control.md)</span></span>\
<span data-ttu-id="a0a77-139">Mostra como usar o <xref:System.Drawing.ToolboxBitmapAttribute> para exibir um ícone ao lado do seu controle personalizado na **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="a0a77-139">Shows how to use the <xref:System.Drawing.ToolboxBitmapAttribute> to display an icon next to your custom control in the **Toolbox**.</span></span>

<span data-ttu-id="a0a77-140">[Como testar o comportamento de tempo de execução de um UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)</span><span class="sxs-lookup"><span data-stu-id="a0a77-140">[How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)</span></span>\
<span data-ttu-id="a0a77-141">Mostra como usar o **Contêiner de Teste UserControl** para testar o comportamento de um controle de composição.</span><span class="sxs-lookup"><span data-stu-id="a0a77-141">Shows how to use the **UserControl Test Container** to test the behavior of a composite control.</span></span>

<span data-ttu-id="a0a77-142">[Erros de tempo de design no Designer de Formulários do Windows](design-time-errors-in-the-windows-forms-designer.md)</span><span class="sxs-lookup"><span data-stu-id="a0a77-142">[Design-Time Errors in the Windows Forms Designer](design-time-errors-in-the-windows-forms-designer.md)</span></span>\
<span data-ttu-id="a0a77-143">Explica o significado e o uso da lista de erros de tempo de design que aparece no Microsoft Visual Studio quando o carregamento do Designer de Formulários do Windows falha.</span><span class="sxs-lookup"><span data-stu-id="a0a77-143">Explains the meaning and use of the Design-Time Error List that appears in Microsoft Visual Studio when the Windows Forms designer fails to load.</span></span>

<span data-ttu-id="a0a77-144">[Solução de Problemas de Criação de Controle e de Componente](troubleshooting-control-and-component-authoring.md)</span><span class="sxs-lookup"><span data-stu-id="a0a77-144">[Troubleshooting Control and Component Authoring](troubleshooting-control-and-component-authoring.md)</span></span>\
<span data-ttu-id="a0a77-145">Mostra como diagnosticar e corrigir problemas comuns que podem ocorrer quando você criar um controle ou componente personalizado.</span><span class="sxs-lookup"><span data-stu-id="a0a77-145">Shows how to diagnose and fix common issues that can occur when you author a custom component or control.</span></span>

## <a name="reference"></a><span data-ttu-id="a0a77-146">Referência</span><span class="sxs-lookup"><span data-stu-id="a0a77-146">Reference</span></span>

- <xref:System.Windows.Forms.Control?displayProperty=nameWithType>

- <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>

## <a name="related-sections"></a><span data-ttu-id="a0a77-147">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="a0a77-147">Related sections</span></span>

<span data-ttu-id="a0a77-148">[Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework](developing-custom-windows-forms-controls.md)</span><span class="sxs-lookup"><span data-stu-id="a0a77-148">[Developing Custom Windows Forms Controls with the .NET Framework](developing-custom-windows-forms-controls.md)</span></span>\
<span data-ttu-id="a0a77-149">Discute como criar seus próprios controles personalizados com o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a0a77-149">Discusses how to create your own custom controls with the .NET Framework.</span></span>

<span data-ttu-id="a0a77-150">[Independência de linguagem e componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md)</span><span class="sxs-lookup"><span data-stu-id="a0a77-150">[Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md)</span></span>\
<span data-ttu-id="a0a77-151">Apresenta o Common Language Runtime, que foi projetado para simplificar a criação e uso de componentes.</span><span class="sxs-lookup"><span data-stu-id="a0a77-151">Introduces the common language runtime, which is designed to simplify the creation and use of components.</span></span> <span data-ttu-id="a0a77-152">Um aspecto importante dessa simplificação é melhor interoperabilidade entre componentes escritos usando diferentes linguagens de programação.</span><span class="sxs-lookup"><span data-stu-id="a0a77-152">An important aspect of this simplification is enhanced interoperability between components written using different programming languages.</span></span> <span data-ttu-id="a0a77-153">A CLS (Common Language Specification) possibilita criar ferramentas e componentes que funcionam com várias linguagens de programação.</span><span class="sxs-lookup"><span data-stu-id="a0a77-153">The Common Language Specification (CLS) makes it possible to create tools and components that work with multiple programming languages.</span></span>

<span data-ttu-id="a0a77-154">[Instruções passo a passo: preenchendo de forma automática a caixa de ferramentas com componentes personalizados](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)</span><span class="sxs-lookup"><span data-stu-id="a0a77-154">[Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)</span></span>\
<span data-ttu-id="a0a77-155">Descreve como habilitar seu componente ou controle para ser exibido na caixa de diálogo **Personalizar Caixa de Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="a0a77-155">Describes how to enable your component or control to be displayed in the **Customize Toolbox** dialog box.</span></span>
