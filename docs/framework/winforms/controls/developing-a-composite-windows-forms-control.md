---
title: Desenvolvendo um controle dos Windows Forms composto
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
ms.openlocfilehash: dc038e5a1858025007ef737397521bfea1b93b97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="developing-a-composite-windows-forms-control"></a><span data-ttu-id="ca4de-102">Desenvolvendo um controle dos Windows Forms composto</span><span class="sxs-lookup"><span data-stu-id="ca4de-102">Developing a Composite Windows Forms Control</span></span>
<span data-ttu-id="ca4de-103">Você pode desenvolver um controle Windows Forms composto combinando outros controles de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="ca4de-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="ca4de-104">Controles compostos que derivam de <xref:System.Web.UI.UserControl> são chamados de controles de usuário.</span><span class="sxs-lookup"><span data-stu-id="ca4de-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="ca4de-105">A classe base, <xref:System.Windows.Forms.UserControl>, fornece o teclado do roteamento para os controles filho, garantindo que os controles filho podem receber foco.</span><span class="sxs-lookup"><span data-stu-id="ca4de-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="ca4de-106">Para obter um exemplo de um controle de usuário, consulte o <xref:System.Windows.Forms.UserControl> exemplo em [como: aplicar atributos em controles dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="ca4de-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="ca4de-107">O designer de formulários do Windows no [!INCLUDE[vsprvsext](../../../../includes/vsprvsext-md.md)] oferece vasto suporte de tempo de design para a criação de controles de usuário.</span><span class="sxs-lookup"><span data-stu-id="ca4de-107">The Windows Forms designer in [!INCLUDE[vsprvsext](../../../../includes/vsprvsext-md.md)] provides rich design-time support for authoring user controls.</span></span>  
  
-   <span data-ttu-id="ca4de-108">[Como exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ca4de-108">[How to: Display a Control in the Choose Toolbox Items Dialog Box](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ca4de-109">[Passo a passo: serializando coleções de tipos padrão com DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ca4de-109">[Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ca4de-110">[Passo a passo: Herdando um Windows Forms controle com o Visual C#](http://msdn.microsoft.com/library/09476da0-8d4c-4a4c-b969-649519dfb438))</span><span class="sxs-lookup"><span data-stu-id="ca4de-110">[Walkthrough: Inheriting from a Windows Forms Control with Visual C#](http://msdn.microsoft.com/library/09476da0-8d4c-4a4c-b969-649519dfb438))</span></span>  
  
-   <span data-ttu-id="ca4de-111">[Como fornecer um bitmap da caixa de ferramentas para um controle](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ca4de-111">[How to: Provide a Toolbox Bitmap for a Control](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ca4de-112">[Como herdar de controles dos Windows Forms existentes](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ca4de-112">[How to: Inherit from Existing Windows Forms Controls](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ca4de-113">[Passo a passo: depurando controles personalizados dos Windows Forms em tempo de Design](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ca4de-113">[Walkthrough: Debugging Custom Windows Forms Controls at Design Time](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ca4de-114">[Como herdar da classe de controle](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ca4de-114">[How to: Inherit from the Control Class](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ca4de-115">[Como testar o comportamento de tempo de execução de um UserControl](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ca4de-115">[How to: Test the Run-Time Behavior of a UserControl](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ca4de-116">[Como alinhar um controle às bordas de formulários no tempo de design](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ca4de-116">[How to: Align a Control to the Edges of Forms at Design Time](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ca4de-117">[Como herdar da classe UserControl](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ca4de-117">[How to: Inherit from the UserControl Class](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ca4de-118">[Como Criar Controles para o Windows Forms](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ca4de-118">[How to: Author Controls for Windows Forms](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ca4de-119">[Como criar controles de composição](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ca4de-119">[How to: Author Composite Controls](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ca4de-120">[Passo a passo: criando um controle de composição com o Visual Basic](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ca4de-120">[Walkthrough: Authoring a Composite Control with Visual Basic](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ca4de-121">[Passo a passo: Criando um controle composto com o Visual C#](http://msdn.microsoft.com/library/f88481a8-c746-4a36-9479-374ce5f2e91f))</span><span class="sxs-lookup"><span data-stu-id="ca4de-121">[Walkthrough: Authoring a Composite Control with Visual C#](http://msdn.microsoft.com/library/f88481a8-c746-4a36-9479-374ce5f2e91f))</span></span>  
  
-   <span data-ttu-id="ca4de-122">[Passo a passo: herdando um controle dos Windows Forms com Visual Basic](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ca4de-122">[Walkthrough: Inheriting from a Windows Forms Control with Visual Basic](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ca4de-123">[Como criar um controle dos Windows Forms que aproveita recursos de tempo de design](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ca4de-123">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="ca4de-124">[Como criar um controle dos Windows Forms que aproveita recursos de tempo de design](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))</span><span class="sxs-lookup"><span data-stu-id="ca4de-124">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca4de-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca4de-125">See Also</span></span>  
 [<span data-ttu-id="ca4de-126">Como aplicar atributos a controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ca4de-126">How to: Apply Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)  
 [<span data-ttu-id="ca4de-127">Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ca4de-127">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="ca4de-128">Variedades de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="ca4de-128">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
