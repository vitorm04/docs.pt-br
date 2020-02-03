---
title: Desenvolver um controle composto
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
ms.openlocfilehash: d80564c71dad57ce9145fbedd45a1396df1ddfec
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746021"
---
# <a name="develop-a-composite-windows-forms-control"></a><span data-ttu-id="32480-102">Desenvolver um controle de Windows Forms de composição</span><span class="sxs-lookup"><span data-stu-id="32480-102">Develop a composite Windows Forms control</span></span>

<span data-ttu-id="32480-103">Você pode desenvolver um controle de Windows Forms de composição combinando outros controles de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="32480-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="32480-104">Os controles compostos que derivam de <xref:System.Web.UI.UserControl> são chamados de controles de usuário.</span><span class="sxs-lookup"><span data-stu-id="32480-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="32480-105">A classe base, <xref:System.Windows.Forms.UserControl>, fornece o roteamento de teclado para os controles filho, garantindo assim que os controles filho possam receber o foco.</span><span class="sxs-lookup"><span data-stu-id="32480-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="32480-106">Para obter um exemplo de um controle de usuário, consulte o exemplo de <xref:System.Windows.Forms.UserControl> em [como aplicar atributos em controles de Windows Forms](how-to-apply-attributes-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="32480-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](how-to-apply-attributes-in-windows-forms-controls.md).</span></span>

<span data-ttu-id="32480-107">O designer de Windows Forms no Visual Studio fornece suporte avançado ao tempo de design para a criação de controles de usuário.</span><span class="sxs-lookup"><span data-stu-id="32480-107">The Windows Forms designer in Visual Studio provides rich design-time support for authoring user controls.</span></span>

- [<span data-ttu-id="32480-108">Como exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas</span><span class="sxs-lookup"><span data-stu-id="32480-108">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)

- [<span data-ttu-id="32480-109">Passo a passo: serializando coleções de tipos padrão com DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="32480-109">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)

- [<span data-ttu-id="32480-110">Instruções passo a passo: herança de um controle do Windows Forms com Visual C#</span><span class="sxs-lookup"><span data-stu-id="32480-110">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)

- [<span data-ttu-id="32480-111">Como fornecer um bitmap da caixa de ferramentas para um controle</span><span class="sxs-lookup"><span data-stu-id="32480-111">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)

- [<span data-ttu-id="32480-112">Como herdar de controles dos Windows Forms existentes</span><span class="sxs-lookup"><span data-stu-id="32480-112">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)

- [<span data-ttu-id="32480-113">Passo a passo: depurando controles personalizados dos Windows Forms em tempo de Design</span><span class="sxs-lookup"><span data-stu-id="32480-113">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)

- [<span data-ttu-id="32480-114">Como herdar da classe de controle</span><span class="sxs-lookup"><span data-stu-id="32480-114">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)

- [<span data-ttu-id="32480-115">Como testar o comportamento de tempo de execução de um UserControl</span><span class="sxs-lookup"><span data-stu-id="32480-115">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)

- [<span data-ttu-id="32480-116">Como alinhar um controle às bordas de formulários no tempo de design</span><span class="sxs-lookup"><span data-stu-id="32480-116">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)

- [<span data-ttu-id="32480-117">Como herdar da classe UserControl</span><span class="sxs-lookup"><span data-stu-id="32480-117">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)

- [<span data-ttu-id="32480-118">Como Criar Controles para o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="32480-118">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)

- [<span data-ttu-id="32480-119">Como criar controles de composição</span><span class="sxs-lookup"><span data-stu-id="32480-119">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)

- [<span data-ttu-id="32480-120">Passo a passo: criando um controle de composição com o Visual C#</span><span class="sxs-lookup"><span data-stu-id="32480-120">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)

- [<span data-ttu-id="32480-121">Instruções passo a passo: criando um controle do Windows Forms que aproveita os recursos de tempo de design do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="32480-121">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)

- <span data-ttu-id="32480-122">[Como criar um controle dos Windows Forms que aproveita recursos de tempo de design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="32480-122">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span></span>

## <a name="see-also"></a><span data-ttu-id="32480-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32480-123">See also</span></span>

- [<span data-ttu-id="32480-124">Como aplicar atributos a controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="32480-124">How to: Apply Attributes in Windows Forms Controls</span></span>](how-to-apply-attributes-in-windows-forms-controls.md)
- [<span data-ttu-id="32480-125">Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="32480-125">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="32480-126">Variedades de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="32480-126">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
