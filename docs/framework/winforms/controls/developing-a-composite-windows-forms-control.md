---
title: Desenvolvendo um controle dos Windows Forms composto
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
ms.openlocfilehash: 9ccbf3de3f5c65b99a06c29ffce4c96896d11fae
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015950"
---
# <a name="develop-a-composite-windows-forms-control"></a><span data-ttu-id="cdc69-102">Desenvolver um controle de Windows Forms de composição</span><span class="sxs-lookup"><span data-stu-id="cdc69-102">Develop a composite Windows Forms control</span></span>

<span data-ttu-id="cdc69-103">Você pode desenvolver um controle de Windows Forms de composição combinando outros controles de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="cdc69-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="cdc69-104">Os controles compostos que derivam de são chamados de controles de <xref:System.Web.UI.UserControl> usuário.</span><span class="sxs-lookup"><span data-stu-id="cdc69-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="cdc69-105">A classe base, <xref:System.Windows.Forms.UserControl>, fornece roteamento de teclado para os controles filho, garantindo assim que os controles filho possam receber o foco.</span><span class="sxs-lookup"><span data-stu-id="cdc69-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="cdc69-106">Para obter um exemplo de controle de usuário, consulte <xref:System.Windows.Forms.UserControl> o exemplo [em como: Aplicar atributos em controles](how-to-apply-attributes-in-windows-forms-controls.md)de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="cdc69-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](how-to-apply-attributes-in-windows-forms-controls.md).</span></span>

<span data-ttu-id="cdc69-107">O designer de Windows Forms no Visual Studio fornece suporte avançado ao tempo de design para a criação de controles de usuário.</span><span class="sxs-lookup"><span data-stu-id="cdc69-107">The Windows Forms designer in Visual Studio provides rich design-time support for authoring user controls.</span></span>

- [<span data-ttu-id="cdc69-108">Como: Exibir um controle na caixa de diálogo escolher itens da Toolbox</span><span class="sxs-lookup"><span data-stu-id="cdc69-108">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)

- [<span data-ttu-id="cdc69-109">Passo a passo: Serializando coleções de tipos padrão com o DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="cdc69-109">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)

- [<span data-ttu-id="cdc69-110">Passo a passo: Herdar de um controle de Windows Forms com o VisualC#</span><span class="sxs-lookup"><span data-stu-id="cdc69-110">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)

- [<span data-ttu-id="cdc69-111">Como: Fornecer um bitmap de caixa de ferramentas para um controle</span><span class="sxs-lookup"><span data-stu-id="cdc69-111">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)

- [<span data-ttu-id="cdc69-112">Como: Herdar de controles de Windows Forms existentes</span><span class="sxs-lookup"><span data-stu-id="cdc69-112">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)

- [<span data-ttu-id="cdc69-113">Passo a passo: Depuração de controles personalizados do Windows Forms em tempo de design</span><span class="sxs-lookup"><span data-stu-id="cdc69-113">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)

- [<span data-ttu-id="cdc69-114">Como: Herdar da classe de controle</span><span class="sxs-lookup"><span data-stu-id="cdc69-114">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)

- [<span data-ttu-id="cdc69-115">Como: Testar o comportamento de tempo de execução de um UserControl</span><span class="sxs-lookup"><span data-stu-id="cdc69-115">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)

- [<span data-ttu-id="cdc69-116">Como: Alinhar um controle às bordas dos formulários no tempo de design</span><span class="sxs-lookup"><span data-stu-id="cdc69-116">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)

- [<span data-ttu-id="cdc69-117">Como: Herdar da classe UserControl</span><span class="sxs-lookup"><span data-stu-id="cdc69-117">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)

- [<span data-ttu-id="cdc69-118">Como: Controles de autor para Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cdc69-118">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)

- [<span data-ttu-id="cdc69-119">Como: Controles de composição de autor</span><span class="sxs-lookup"><span data-stu-id="cdc69-119">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)

- [<span data-ttu-id="cdc69-120">Passo a passo: Criando um controle composto com VisualC#</span><span class="sxs-lookup"><span data-stu-id="cdc69-120">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)

- [<span data-ttu-id="cdc69-121">Passo a passo: Criando um controle de Windows Forms que aproveita os recursos de tempo de design do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cdc69-121">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)

- <span data-ttu-id="cdc69-122">[Como: Criar um controle de Windows Forms que aproveita os recursos de tempo de design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="cdc69-122">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span></span>

## <a name="see-also"></a><span data-ttu-id="cdc69-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdc69-123">See also</span></span>

- [<span data-ttu-id="cdc69-124">Como: Aplicar atributos em controles de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cdc69-124">How to: Apply Attributes in Windows Forms Controls</span></span>](how-to-apply-attributes-in-windows-forms-controls.md)
- [<span data-ttu-id="cdc69-125">Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cdc69-125">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="cdc69-126">Variedades de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="cdc69-126">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
