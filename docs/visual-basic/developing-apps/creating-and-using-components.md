---
title: Criando e usando componentes no Visual Basic
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- components [Visual Basic]
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 03929dd0dbb81a9efee5b69ede78ff0b4ab4d380
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="creating-and-using-components-in-visual-basic"></a><span data-ttu-id="7fe69-102">Criando e usando componentes no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7fe69-102">Creating and Using Components in Visual Basic</span></span>
<span data-ttu-id="7fe69-103">Um *componente* é uma classe que implementa a interface <xref:System.ComponentModel.IComponent?displayProperty=fullName> ou que deriva direta ou indiretamente de uma classe que implementa <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="7fe69-103">A *component* is a class that implements the <xref:System.ComponentModel.IComponent?displayProperty=fullName> interface or that derives directly or indirectly from a class that implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="7fe69-104">Um componente [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] é um objeto que é reutilizável, pode interagir com outros objetos e fornece controle sobre recursos externos e suporte ao tempo de design.</span><span class="sxs-lookup"><span data-stu-id="7fe69-104">A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] component is an object that is reusable, can interact with other objects, and provides control over external resources and design-time support.</span></span>  
  
 <span data-ttu-id="7fe69-105">Um recurso importante dos componentes é que eles são projetáveis, o que significa que uma classe que é um componente pode ser usada no ambiente de desenvolvimento integrado do [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7fe69-105">An important feature of components is that they are designable, which means that a class that is a component can be used in the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Integrated Development Environment.</span></span> <span data-ttu-id="7fe69-106">Um componente pode ser adicionado à Caixa de Ferramentas, arrastado e solto em um formulário e manipulado em uma superfície de design.</span><span class="sxs-lookup"><span data-stu-id="7fe69-106">A component can be added to the Toolbox, dragged and dropped onto a form, and manipulated on a design surface.</span></span> <span data-ttu-id="7fe69-107">Observe que o suporte ao tempo de design de base para componentes é incorporado no [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]; um desenvolvedor de componentes não precisa fazer nenhum trabalho adicional para aproveitar a funcionalidade de base do tempo de design.</span><span class="sxs-lookup"><span data-stu-id="7fe69-107">Notice that base design-time support for components is built into the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]; a component developer does not have to do any additional work to take advantage of the base design-time functionality.</span></span>  
  
 <span data-ttu-id="7fe69-108">Um *controle* é semelhante a um componente, pois ambos são projetáveis.</span><span class="sxs-lookup"><span data-stu-id="7fe69-108">A *control* is similar to a component, as both are designable.</span></span> <span data-ttu-id="7fe69-109">No entanto, um controle fornece uma interface do usuário, enquanto que um componente não.</span><span class="sxs-lookup"><span data-stu-id="7fe69-109">However, a control provides a user interface, while a component does not.</span></span> <span data-ttu-id="7fe69-110">Um controle deve derivar de uma das classes de controle base: <xref:System.Windows.Forms.Control> ou <xref:System.Web.UI.Control>.</span><span class="sxs-lookup"><span data-stu-id="7fe69-110">A control must derive from one of the base control classes: <xref:System.Windows.Forms.Control> or <xref:System.Web.UI.Control>.</span></span>  
  
## <a name="when-to-create-a-component"></a><span data-ttu-id="7fe69-111">Quando criar um componente</span><span class="sxs-lookup"><span data-stu-id="7fe69-111">When to Create a Component</span></span>  
 <span data-ttu-id="7fe69-112">Se sua classe for ser usada em uma superfície de design (como o Designer do Windows Forms ou do Web Forms), mas não tiver uma interface do usuário, ela deverá ser um componente e implementar <xref:System.ComponentModel.IComponent> ou derivar de uma classe que implementa, direta ou indiretamente, <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="7fe69-112">If your class will be used on a design surface (such as the Windows Forms or Web Forms Designer) but has no user interface, it should be a component and implement <xref:System.ComponentModel.IComponent>, or derive from a class that directly or indirectly implements <xref:System.ComponentModel.IComponent>.</span></span>  
  
 <span data-ttu-id="7fe69-113">As classes <xref:System.ComponentModel.Component> e <xref:System.ComponentModel.MarshalByValueComponent> são implementações base da interface <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="7fe69-113">The <xref:System.ComponentModel.Component> and <xref:System.ComponentModel.MarshalByValueComponent> classes are base implementations of the <xref:System.ComponentModel.IComponent> interface.</span></span> <span data-ttu-id="7fe69-114">A principal diferença entre essas classes é que o marshaling da classe <xref:System.ComponentModel.Component> é realizado por referência, enquanto o marshaling de <xref:System.ComponentModel.IComponent> é realizado por valor.</span><span class="sxs-lookup"><span data-stu-id="7fe69-114">The main difference between these classes is that the <xref:System.ComponentModel.Component> class is marshaled by reference, while <xref:System.ComponentModel.IComponent> is marshaled by value.</span></span> <span data-ttu-id="7fe69-115">A lista a seguir fornece diretrizes amplas para os implementadores.</span><span class="sxs-lookup"><span data-stu-id="7fe69-115">The following list provides broad guidelines for implementers.</span></span>  
  
-   <span data-ttu-id="7fe69-116">Se o seu componente precisar ter o marshaling realizado por referência, derive de <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="7fe69-116">If your component needs to be marshaled by reference, derive from <xref:System.ComponentModel.Component>.</span></span>  
  
-   <span data-ttu-id="7fe69-117">Se o seu componente precisar ter o marshaling realizado por valor, derive de <xref:System.ComponentModel.MarshalByValueComponent>.</span><span class="sxs-lookup"><span data-stu-id="7fe69-117">If your component needs to be marshaled by value, derive from <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
-   <span data-ttu-id="7fe69-118">Se o seu componente não puder derivar de uma das implementações de base devido a herança única, implemente <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="7fe69-118">If your component cannot derive from one of the base implementations due to single inheritance, implement <xref:System.ComponentModel.IComponent>.</span></span>  
  
 <span data-ttu-id="7fe69-119">Para obter mais informações sobre o suporte ao tempo de design, consulte [Atributos de tempo de design para componentes](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3) e [Estendendo o suporte ao tempo de design](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).</span><span class="sxs-lookup"><span data-stu-id="7fe69-119">For more information about design-time support, see [Design-Time Attributes for Components](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3) and [Extending Design-Time Support](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).</span></span>  
  
## <a name="component-classes"></a><span data-ttu-id="7fe69-120">Classes de componentes</span><span class="sxs-lookup"><span data-stu-id="7fe69-120">Component Classes</span></span>  
 <span data-ttu-id="7fe69-121">O namespace <xref:System.ComponentModel> fornece classes que são usadas para implementar o comportamento de tempo de design e tempo de execução de componentes e controles.</span><span class="sxs-lookup"><span data-stu-id="7fe69-121">The <xref:System.ComponentModel> namespace provides classes that are used to implement the run-time and design-time behavior of components and controls.</span></span> <span data-ttu-id="7fe69-122">Este namespace inclui as classes e interfaces base para implementar atributos e conversores de tipo, associar a fontes de dados e licenciar componentes.</span><span class="sxs-lookup"><span data-stu-id="7fe69-122">This namespace includes the base classes and interfaces for implementing attributes and type converters, binding to data sources, and licensing components.</span></span>  
  
 <span data-ttu-id="7fe69-123">As classes de componente principais são:</span><span class="sxs-lookup"><span data-stu-id="7fe69-123">The core component classes are:</span></span>  
  
-   <span data-ttu-id="7fe69-124"><xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="7fe69-124"><xref:System.ComponentModel.Component>.</span></span> <span data-ttu-id="7fe69-125">Uma implementação base para a interface <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="7fe69-125">A base implementation for the <xref:System.ComponentModel.IComponent> interface.</span></span> <span data-ttu-id="7fe69-126">Essa classe habilita o compartilhamento de objeto entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7fe69-126">This class enables object sharing between applications.</span></span>  
  
-   <span data-ttu-id="7fe69-127"><xref:System.ComponentModel.MarshalByValueComponent>.</span><span class="sxs-lookup"><span data-stu-id="7fe69-127"><xref:System.ComponentModel.MarshalByValueComponent>.</span></span> <span data-ttu-id="7fe69-128">Uma implementação base para a interface <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="7fe69-128">A base implementation for the <xref:System.ComponentModel.IComponent> interface.</span></span>  
  
-   <span data-ttu-id="7fe69-129"><xref:System.ComponentModel.Container>.</span><span class="sxs-lookup"><span data-stu-id="7fe69-129"><xref:System.ComponentModel.Container>.</span></span> <span data-ttu-id="7fe69-130">A implementação base para a interface <xref:System.ComponentModel.IContainer>.</span><span class="sxs-lookup"><span data-stu-id="7fe69-130">The base implementation for the <xref:System.ComponentModel.IContainer> interface.</span></span> <span data-ttu-id="7fe69-131">Essa classe encapsula zero ou mais componentes.</span><span class="sxs-lookup"><span data-stu-id="7fe69-131">This class encapsulates zero or more components.</span></span>  
  
 <span data-ttu-id="7fe69-132">Algumas das classes usadas para licenciamento de componentes são:</span><span class="sxs-lookup"><span data-stu-id="7fe69-132">Some of the classes used for component licensing are:</span></span>  
  
-   <span data-ttu-id="7fe69-133"><xref:System.ComponentModel.License>.</span><span class="sxs-lookup"><span data-stu-id="7fe69-133"><xref:System.ComponentModel.License>.</span></span> <span data-ttu-id="7fe69-134">A classe base abstrata para todas as licenças.</span><span class="sxs-lookup"><span data-stu-id="7fe69-134">The abstract base class for all licenses.</span></span> <span data-ttu-id="7fe69-135">Uma licença é concedida a uma instância específica de um componente.</span><span class="sxs-lookup"><span data-stu-id="7fe69-135">A license is granted to a specific instance of a component.</span></span>  
  
-   <span data-ttu-id="7fe69-136"><xref:System.ComponentModel.LicenseManager>.</span><span class="sxs-lookup"><span data-stu-id="7fe69-136"><xref:System.ComponentModel.LicenseManager>.</span></span> <span data-ttu-id="7fe69-137">Fornece propriedades e métodos para adicionar uma licença a um componente e gerenciar um <xref:System.ComponentModel.LicenseProvider>.</span><span class="sxs-lookup"><span data-stu-id="7fe69-137">Provides properties and methods to add a license to a component and to manage a <xref:System.ComponentModel.LicenseProvider>.</span></span>  
  
-   <span data-ttu-id="7fe69-138"><xref:System.ComponentModel.LicenseProvider>.</span><span class="sxs-lookup"><span data-stu-id="7fe69-138"><xref:System.ComponentModel.LicenseProvider>.</span></span> <span data-ttu-id="7fe69-139">A classe base abstrata para implementar um provedor de licença.</span><span class="sxs-lookup"><span data-stu-id="7fe69-139">The abstract base class for implementing a license provider.</span></span>  
  
-   <span data-ttu-id="7fe69-140"><xref:System.ComponentModel.LicenseProviderAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7fe69-140"><xref:System.ComponentModel.LicenseProviderAttribute>.</span></span> <span data-ttu-id="7fe69-141">Especifica a classe <xref:System.ComponentModel.LicenseProvider> a ser usada com uma classe.</span><span class="sxs-lookup"><span data-stu-id="7fe69-141">Specifies the <xref:System.ComponentModel.LicenseProvider> class to use with a class.</span></span>  
  
 <span data-ttu-id="7fe69-142">Classes normalmente usadas para descrever e persistir componentes.</span><span class="sxs-lookup"><span data-stu-id="7fe69-142">Classes commonly used for describing and persisting components.</span></span>  
  
-   <span data-ttu-id="7fe69-143"><xref:System.ComponentModel.TypeDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="7fe69-143"><xref:System.ComponentModel.TypeDescriptor>.</span></span> <span data-ttu-id="7fe69-144">Fornece informações sobre as características de um componente, como atributos, propriedades e eventos.</span><span class="sxs-lookup"><span data-stu-id="7fe69-144">Provides information about the characteristics for a component, such as its attributes, properties, and events.</span></span>  
  
-   <span data-ttu-id="7fe69-145"><xref:System.ComponentModel.EventDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="7fe69-145"><xref:System.ComponentModel.EventDescriptor>.</span></span> <span data-ttu-id="7fe69-146">Fornece informações sobre um evento.</span><span class="sxs-lookup"><span data-stu-id="7fe69-146">Provides information about an event.</span></span>  
  
-   <span data-ttu-id="7fe69-147"><xref:System.ComponentModel.PropertyDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="7fe69-147"><xref:System.ComponentModel.PropertyDescriptor>.</span></span> <span data-ttu-id="7fe69-148">Fornece informações sobre uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="7fe69-148">Provides information about a property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7fe69-149">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="7fe69-149">Related Sections</span></span>  
 [<span data-ttu-id="7fe69-150">Classe versus componente versus controle</span><span class="sxs-lookup"><span data-stu-id="7fe69-150">Class vs. Component vs. Control</span></span>](http://msdn.microsoft.com/library/db8b842e-44d9-40cc-a0f8-70fd189632c3)  
 <span data-ttu-id="7fe69-151">Define *componente* e *controle* e discute as diferenças entre eles e as classes.</span><span class="sxs-lookup"><span data-stu-id="7fe69-151">Defines *component* and *control*, and discusses the differences between them and classes.</span></span>  
  
 [<span data-ttu-id="7fe69-152">Criação de componentes</span><span class="sxs-lookup"><span data-stu-id="7fe69-152">Component Authoring</span></span>](http://msdn.microsoft.com/library/4a5a5e49-0378-4a31-83bc-24da0f1a727d)  
 <span data-ttu-id="7fe69-153">Roteiro para uma introdução aos componentes.</span><span class="sxs-lookup"><span data-stu-id="7fe69-153">Roadmap for getting started with components.</span></span>  
  
 [<span data-ttu-id="7fe69-154">Instruções passo a passo para criação de componentes</span><span class="sxs-lookup"><span data-stu-id="7fe69-154">Component Authoring Walkthroughs</span></span>](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 <span data-ttu-id="7fe69-155">Links para tópicos que fornecem instruções passo a passo para programação de componentes.</span><span class="sxs-lookup"><span data-stu-id="7fe69-155">Links to topics that provide step-by-step instruction for component programming.</span></span>  
  
 [<span data-ttu-id="7fe69-156">Classes de componentes</span><span class="sxs-lookup"><span data-stu-id="7fe69-156">Component Classes</span></span>](http://msdn.microsoft.com/library/ce2e5647-e673-4c2b-8125-ffebbd9d71bc)  
 <span data-ttu-id="7fe69-157">Descreve o que torna uma classe um componente, as maneiras de expor a funcionalidade do componente, como controlar o acesso a componentes e controlar como instâncias de componentes são criadas.</span><span class="sxs-lookup"><span data-stu-id="7fe69-157">Describes what makes a class a component, ways to expose component functionality, controlling access to components, and controlling how component instances are created.</span></span>  
  
 [<span data-ttu-id="7fe69-158">Solução de problemas de criação de controle e de componente</span><span class="sxs-lookup"><span data-stu-id="7fe69-158">Troubleshooting Control and Component Authoring</span></span>](../../framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 <span data-ttu-id="7fe69-159">Explica como corrigir problemas comuns.</span><span class="sxs-lookup"><span data-stu-id="7fe69-159">Explains how to fix common problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fe69-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7fe69-160">See Also</span></span>  
 <span data-ttu-id="7fe69-161">[Como acessar o suporte a tempo de design no Windows Forms](http://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09) </span><span class="sxs-lookup"><span data-stu-id="7fe69-161">[How to: Access Design-Time Support in Windows Forms](http://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09) </span></span>  
 <span data-ttu-id="7fe69-162">[Como estender a aparência e o comportamento dos controles no modo de design](http://msdn.microsoft.com/library/68f85054-2253-47f5-a4f2-3f1ac8c9f27b) </span><span class="sxs-lookup"><span data-stu-id="7fe69-162">[How to: Extend the Appearance and Behavior of Controls in Design Mode](http://msdn.microsoft.com/library/68f85054-2253-47f5-a4f2-3f1ac8c9f27b) </span></span>  
 [<span data-ttu-id="7fe69-163">Como realizar uma inicialização personalizada para controles no modo de design</span><span class="sxs-lookup"><span data-stu-id="7fe69-163">How to: Perform Custom Initialization for Controls in Design Mode</span></span>](http://msdn.microsoft.com/library/914eaa03-092f-4556-9160-b8a2a40641d9)

