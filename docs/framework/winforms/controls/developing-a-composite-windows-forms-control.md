---
title: Desenvolvendo um controle dos Windows Forms composto
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
ms.openlocfilehash: bfbb9091d40652bdd1ae277f3a77feefbccbf080
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196457"
---
# <a name="developing-a-composite-windows-forms-control"></a><span data-ttu-id="9604c-102">Desenvolvendo um controle dos Windows Forms composto</span><span class="sxs-lookup"><span data-stu-id="9604c-102">Developing a Composite Windows Forms Control</span></span>
<span data-ttu-id="9604c-103">Você pode desenvolver um controle Windows Forms composto pela combinação de outros controles dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9604c-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="9604c-104">Controles de composição que derivam de <xref:System.Web.UI.UserControl> são chamados de controles de usuário.</span><span class="sxs-lookup"><span data-stu-id="9604c-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="9604c-105">A classe base, <xref:System.Windows.Forms.UserControl>, fornece o roteamento para os controles filho, garantindo assim que os controles filho podem receber foco de teclado.</span><span class="sxs-lookup"><span data-stu-id="9604c-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="9604c-106">Para obter um exemplo de um controle de usuário, consulte o <xref:System.Windows.Forms.UserControl> amostra em [como: Aplicar atributos em controles dos Windows Forms](how-to-apply-attributes-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="9604c-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="9604c-107">O designer de formulários do Windows no Visual Studio oferece suporte avançado do tempo de design para criação de controles de usuário.</span><span class="sxs-lookup"><span data-stu-id="9604c-107">The Windows Forms designer in Visual Studio provides rich design-time support for authoring user controls.</span></span>  
  
-   [<span data-ttu-id="9604c-108">Como: Exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas</span><span class="sxs-lookup"><span data-stu-id="9604c-108">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
  
-   [<span data-ttu-id="9604c-109">Passo a passo: Serializando coleções de tipos padrão com a DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="9604c-109">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)  
  
-   [<span data-ttu-id="9604c-110">Passo a passo: Herdando um controle do Windows Forms com Visual C#</span><span class="sxs-lookup"><span data-stu-id="9604c-110">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
  
-   [<span data-ttu-id="9604c-111">Como: Fornecer um bitmap da caixa de ferramentas para um controle</span><span class="sxs-lookup"><span data-stu-id="9604c-111">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
  
-   [<span data-ttu-id="9604c-112">Como: Herdar de controles do Windows Forms existentes</span><span class="sxs-lookup"><span data-stu-id="9604c-112">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)  
  
-   [<span data-ttu-id="9604c-113">Passo a passo: Depurando controles do Windows Forms no tempo de design</span><span class="sxs-lookup"><span data-stu-id="9604c-113">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
  
-   [<span data-ttu-id="9604c-114">Como: Herdar da classe Control</span><span class="sxs-lookup"><span data-stu-id="9604c-114">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)  
  
-   [<span data-ttu-id="9604c-115">Como: Testar o comportamento de tempo de execução de um UserControl</span><span class="sxs-lookup"><span data-stu-id="9604c-115">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
  
-   [<span data-ttu-id="9604c-116">Como: Alinhar um controle às bordas de formulários no tempo de design</span><span class="sxs-lookup"><span data-stu-id="9604c-116">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
  
-   [<span data-ttu-id="9604c-117">Como: Herdar da classe UserControl</span><span class="sxs-lookup"><span data-stu-id="9604c-117">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)  
  
-   [<span data-ttu-id="9604c-118">Como: Criar Controles para o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9604c-118">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)  
  
-   [<span data-ttu-id="9604c-119">Como: Criar controles compostos</span><span class="sxs-lookup"><span data-stu-id="9604c-119">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)  
  
-   [<span data-ttu-id="9604c-120">Passo a passo: Criar um controle composto com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9604c-120">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
  
-   [<span data-ttu-id="9604c-121">Passo a passo: Criando um controle composto com o Visual C#</span><span class="sxs-lookup"><span data-stu-id="9604c-121">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
  
-   [<span data-ttu-id="9604c-122">Passo a passo: Herdar de um controle do Windows Forms com Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9604c-122">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
  
-   [<span data-ttu-id="9604c-123">Passo a passo: Criar um controle do Windows Forms que aproveita os recursos de tempo de design do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9604c-123">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)  
  
-   [<span data-ttu-id="9604c-124">Como: Criar um controle de formulários do Windows que tira proveito dos recursos de tempo de Design</span><span class="sxs-lookup"><span data-stu-id="9604c-124">How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))  
  
## <a name="see-also"></a><span data-ttu-id="9604c-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9604c-125">See also</span></span>

- [<span data-ttu-id="9604c-126">Como: Aplicar atributos a controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9604c-126">How to: Apply Attributes in Windows Forms Controls</span></span>](how-to-apply-attributes-in-windows-forms-controls.md)
- [<span data-ttu-id="9604c-127">Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9604c-127">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="9604c-128">Variedades de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="9604c-128">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
