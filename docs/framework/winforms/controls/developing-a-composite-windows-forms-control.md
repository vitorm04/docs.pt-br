---
title: Desenvolvendo um controle dos Windows Forms composto
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
ms.openlocfilehash: 1d2c6419e19aee73717bed6cfc17782d2a3f5a4a
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442731"
---
# <a name="developing-a-composite-windows-forms-control"></a><span data-ttu-id="cfd2b-102">Desenvolvendo um controle dos Windows Forms composto</span><span class="sxs-lookup"><span data-stu-id="cfd2b-102">Developing a Composite Windows Forms Control</span></span>
<span data-ttu-id="cfd2b-103">Você pode desenvolver um controle Windows Forms composto pela combinação de outros controles dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="cfd2b-104">Controles de composição que derivam de <xref:System.Web.UI.UserControl> são chamados de controles de usuário.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="cfd2b-105">A classe base, <xref:System.Windows.Forms.UserControl>, fornece o roteamento para os controles filho, garantindo assim que os controles filho podem receber foco de teclado.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="cfd2b-106">Para obter um exemplo de um controle de usuário, consulte o <xref:System.Windows.Forms.UserControl> amostra em [como: Aplicar atributos em controles dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="cfd2b-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="cfd2b-107">O designer de formulários do Windows no Visual Studio oferece suporte avançado do tempo de design para criação de controles de usuário.</span><span class="sxs-lookup"><span data-stu-id="cfd2b-107">The Windows Forms designer in Visual Studio provides rich design-time support for authoring user controls.</span></span>  
  
-   [<span data-ttu-id="cfd2b-108">Como: Exibir um controle na caixa de diálogo de itens de caixa de ferramentas de escolha</span><span class="sxs-lookup"><span data-stu-id="cfd2b-108">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
  
-   [<span data-ttu-id="cfd2b-109">Passo a passo: Serializando coleções de tipos padrão com DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="cfd2b-109">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)  
  
-   [<span data-ttu-id="cfd2b-110">Passo a passo: Herdando um controle de formulários do Windows com VisualC#</span><span class="sxs-lookup"><span data-stu-id="cfd2b-110">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
  
-   [<span data-ttu-id="cfd2b-111">Como: Fornecer um Bitmap da caixa de ferramentas para um controle</span><span class="sxs-lookup"><span data-stu-id="cfd2b-111">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
  
-   [<span data-ttu-id="cfd2b-112">Como: Herdar controles de formulários do Windows existentes</span><span class="sxs-lookup"><span data-stu-id="cfd2b-112">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)  
  
-   [<span data-ttu-id="cfd2b-113">Passo a passo: Depuração de controles personalizados do Windows Forms em tempo de design</span><span class="sxs-lookup"><span data-stu-id="cfd2b-113">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
  
-   [<span data-ttu-id="cfd2b-114">Como: Herdar da classe de controle</span><span class="sxs-lookup"><span data-stu-id="cfd2b-114">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)  
  
-   [<span data-ttu-id="cfd2b-115">Como: Testar o comportamento de tempo de execução de um UserControl</span><span class="sxs-lookup"><span data-stu-id="cfd2b-115">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
  
-   [<span data-ttu-id="cfd2b-116">Como: Alinhar um controle às bordas de formulários no tempo de Design</span><span class="sxs-lookup"><span data-stu-id="cfd2b-116">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
  
-   [<span data-ttu-id="cfd2b-117">Como: Herdar da classe UserControl</span><span class="sxs-lookup"><span data-stu-id="cfd2b-117">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)  
  
-   [<span data-ttu-id="cfd2b-118">Como: Criar controles para Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cfd2b-118">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)  
  
-   [<span data-ttu-id="cfd2b-119">Como: Criar controles compostos</span><span class="sxs-lookup"><span data-stu-id="cfd2b-119">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)  
  
-   [<span data-ttu-id="cfd2b-120">Passo a passo: Criando um controle composto com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cfd2b-120">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
  
-   [<span data-ttu-id="cfd2b-121">Passo a passo: Criando um controle composto com VisualC#</span><span class="sxs-lookup"><span data-stu-id="cfd2b-121">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
  
-   [<span data-ttu-id="cfd2b-122">Passo a passo: Herdando um controle de formulários do Windows com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cfd2b-122">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
  
-   [<span data-ttu-id="cfd2b-123">Passo a passo: Criando um controle de formulários do Windows que tira proveito dos recursos de tempo de Design do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cfd2b-123">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)  
  
-   <span data-ttu-id="cfd2b-124">[Como: Criar um controle de formulários do Windows que tira proveito dos recursos de tempo de Design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="cfd2b-124">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfd2b-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cfd2b-125">See also</span></span>
- [<span data-ttu-id="cfd2b-126">Como: Aplicar atributos em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cfd2b-126">How to: Apply Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)
- [<span data-ttu-id="cfd2b-127">Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cfd2b-127">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="cfd2b-128">Variedades de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="cfd2b-128">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
