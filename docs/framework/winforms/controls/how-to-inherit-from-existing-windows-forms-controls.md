---
title: Como herdar de controles dos Windows Forms existentes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 063f5bb87b6348ee83573cf1506c9fabdaf651ee
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460570"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a><span data-ttu-id="9cd11-102">Como herdar de controles dos Windows Forms existentes</span><span class="sxs-lookup"><span data-stu-id="9cd11-102">How to: Inherit from Existing Windows Forms Controls</span></span>

<span data-ttu-id="9cd11-103">Se você quiser estender a funcionalidade de um controle existente, poderá criar um controle derivado de um controle existente por meio de herança.</span><span class="sxs-lookup"><span data-stu-id="9cd11-103">If you want to extend the functionality of an existing control, you can create a control derived from an existing control through inheritance.</span></span> <span data-ttu-id="9cd11-104">Ao herdar de um controle existente, você herda todas as funcionalidades e propriedades visuais desse controle.</span><span class="sxs-lookup"><span data-stu-id="9cd11-104">When inheriting from an existing control, you inherit all of the functionality and visual properties of that control.</span></span> <span data-ttu-id="9cd11-105">Por exemplo, se você estivesse criando um controle herdado de <xref:System.Windows.Forms.Button>, seu novo controle ficaria e agiria exatamente como um controle de <xref:System.Windows.Forms.Button> padrão.</span><span class="sxs-lookup"><span data-stu-id="9cd11-105">For example, if you were creating a control that inherited from <xref:System.Windows.Forms.Button>, your new control would look and act exactly like a standard <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="9cd11-106">Dessa forma, você poderia estender ou modificar a funcionalidade de seu novo controle por meio da implementação de métodos e propriedades personalizados.</span><span class="sxs-lookup"><span data-stu-id="9cd11-106">You could then extend or modify the functionality of your new control through the implementation of custom methods and properties.</span></span> <span data-ttu-id="9cd11-107">Em alguns controles, você também pode alterar a aparência visual do seu controle herdado substituindo seu método <xref:System.Windows.Forms.Control.OnPaint%2A>.</span><span class="sxs-lookup"><span data-stu-id="9cd11-107">In some controls, you can also change the visual appearance of your inherited control by overriding its <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

## <a name="to-create-an-inherited-control"></a><span data-ttu-id="9cd11-108">Criar um controle herdado</span><span class="sxs-lookup"><span data-stu-id="9cd11-108">To create an inherited control</span></span>

1. <span data-ttu-id="9cd11-109">No Visual Studio, crie um novo projeto de **aplicativo Windows Forms** .</span><span class="sxs-lookup"><span data-stu-id="9cd11-109">In Visual Studio, create a new **Windows Forms Application** project.</span></span>

1. <span data-ttu-id="9cd11-110">No menu **Projeto**, escolha **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="9cd11-110">From the **Project** menu, choose **Add New Item**.</span></span>

    <span data-ttu-id="9cd11-111">A caixa de diálogo **Adicionar Novo Item** é exibida.</span><span class="sxs-lookup"><span data-stu-id="9cd11-111">The **Add New Item** dialog box appears.</span></span>

1. <span data-ttu-id="9cd11-112">Na caixa de diálogo **Adicionar Novo Item**, clique duas vezes em **Controle personalizado**.</span><span class="sxs-lookup"><span data-stu-id="9cd11-112">In the **Add New Item** dialog box, double-click **Custom Control**.</span></span>

    <span data-ttu-id="9cd11-113">Um novo controle personalizado será adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="9cd11-113">A new custom control is added to your project.</span></span>

1. <span data-ttu-id="9cd11-114">Se você estiver usando:</span><span class="sxs-lookup"><span data-stu-id="9cd11-114">If you using:</span></span>

    - <span data-ttu-id="9cd11-115">Visual Basic, na parte superior do **Gerenciador de soluções**, clique em **Mostrar todos os arquivos**.</span><span class="sxs-lookup"><span data-stu-id="9cd11-115">Visual Basic, at the top of **Solution Explorer**, click **Show All Files**.</span></span> <span data-ttu-id="9cd11-116">Expanda CustomControl1.vb e abra CustomControl1.Designer.vb no Editor de Código.</span><span class="sxs-lookup"><span data-stu-id="9cd11-116">Expand CustomControl1.vb and then open CustomControl1.Designer.vb in the Code Editor.</span></span>
    - <span data-ttu-id="9cd11-117">C#, abra CustomControl1.cs no editor de código.</span><span class="sxs-lookup"><span data-stu-id="9cd11-117">C#, open CustomControl1.cs in the Code Editor.</span></span>

1. <span data-ttu-id="9cd11-118">Localize a declaração de classe, que herda de <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="9cd11-118">Locate the class declaration, which inherits from <xref:System.Windows.Forms.Control>.</span></span>

1. <span data-ttu-id="9cd11-119">Altere a classe base para o controle do qual você deseja herdar.</span><span class="sxs-lookup"><span data-stu-id="9cd11-119">Change the base class to the control that you want to inherit from.</span></span>

     <span data-ttu-id="9cd11-120">Por exemplo, se você quiser herdar de <xref:System.Windows.Forms.Button>, altere a declaração de classe para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9cd11-120">For example, if you want to inherit from <xref:System.Windows.Forms.Button>, change the class declaration to the following:</span></span>

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

1. <span data-ttu-id="9cd11-121">Se você estiver usando Visual Basic, salve e feche CustomControl1.Designer.vb.</span><span class="sxs-lookup"><span data-stu-id="9cd11-121">If you are using Visual Basic, save and close CustomControl1.Designer.vb.</span></span> <span data-ttu-id="9cd11-122">Abra CustomControl1.vb no Editor de Código.</span><span class="sxs-lookup"><span data-stu-id="9cd11-122">Open CustomControl1.vb in the Code Editor.</span></span>

1. <span data-ttu-id="9cd11-123">Implemente os métodos ou propriedades personalizados que o controle incorporará.</span><span class="sxs-lookup"><span data-stu-id="9cd11-123">Implement any custom methods or properties that your control will incorporate.</span></span>

1. <span data-ttu-id="9cd11-124">Se você quiser modificar a aparência gráfica do seu controle, substitua o método <xref:System.Windows.Forms.Control.OnPaint%2A>.</span><span class="sxs-lookup"><span data-stu-id="9cd11-124">If you want to modify the graphical appearance of your control, override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9cd11-125">A substituição de <xref:System.Windows.Forms.Control.OnPaint%2A> não permitirá que você modifique a aparência de todos os controles.</span><span class="sxs-lookup"><span data-stu-id="9cd11-125">Overriding <xref:System.Windows.Forms.Control.OnPaint%2A> will not allow you to modify the appearance of all controls.</span></span> <span data-ttu-id="9cd11-126">Esses controles que têm toda a pintura feita pelo Windows (por exemplo, <xref:System.Windows.Forms.TextBox>) nunca chamam o método <xref:System.Windows.Forms.Control.OnPaint%2A> e, portanto, nunca usarão o código personalizado.</span><span class="sxs-lookup"><span data-stu-id="9cd11-126">Those controls that have all of their painting done by Windows (for example, <xref:System.Windows.Forms.TextBox>) never call their <xref:System.Windows.Forms.Control.OnPaint%2A> method, and thus will never use the custom code.</span></span> <span data-ttu-id="9cd11-127">Consulte a documentação da ajuda para o controle específico que você deseja modificar para ver se o método de <xref:System.Windows.Forms.Control.OnPaint%2A> está disponível.</span><span class="sxs-lookup"><span data-stu-id="9cd11-127">Refer to the Help documentation for the particular control you want to modify to see if the <xref:System.Windows.Forms.Control.OnPaint%2A> method is available.</span></span> <span data-ttu-id="9cd11-128">Para obter uma lista de todos os controles do Windows Forms, consulte [Controles a serem usados no Windows Forms](controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="9cd11-128">For a list of all the Windows Form Controls, see [Controls to Use on Windows Forms](controls-to-use-on-windows-forms.md).</span></span> <span data-ttu-id="9cd11-129">Se um controle não tiver <xref:System.Windows.Forms.Control.OnPaint%2A> listado como um método de membro, você não poderá alterar sua aparência substituindo esse método.</span><span class="sxs-lookup"><span data-stu-id="9cd11-129">If a control does not have <xref:System.Windows.Forms.Control.OnPaint%2A> listed as a member method, you cannot alter its appearance by overriding this method.</span></span> <span data-ttu-id="9cd11-130">Para obter mais informações sobre pintura personalizada, consulte [Pintura e renderização de controle personalizado](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="9cd11-130">For more information about custom painting, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

    ```vb
    Protected Overrides Sub OnPaint(ByVal e As _
       System.Windows.Forms.PaintEventArgs)
       MyBase.OnPaint(e)
       ' Insert code to do custom painting.
       ' If you want to completely change the appearance of your control,
       ' do not call MyBase.OnPaint(e).
    End Sub
    ```

    ```csharp
    protected override void OnPaint(PaintEventArgs pe)
    {
       base.OnPaint(pe);
       // Insert code to do custom painting.
       // If you want to completely change the appearance of your control,
       // do not call base.OnPaint(pe).
    }
    ```

1. <span data-ttu-id="9cd11-131">Salve e teste seu controle.</span><span class="sxs-lookup"><span data-stu-id="9cd11-131">Save and test your control.</span></span>

## <a name="see-also"></a><span data-ttu-id="9cd11-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9cd11-132">See also</span></span>

- [<span data-ttu-id="9cd11-133">Variedades de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="9cd11-133">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="9cd11-134">Como herdar da classe de controle</span><span class="sxs-lookup"><span data-stu-id="9cd11-134">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="9cd11-135">Como herdar da classe UserControl</span><span class="sxs-lookup"><span data-stu-id="9cd11-135">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="9cd11-136">Como Criar Controles para o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9cd11-136">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="9cd11-137">Solucionando problemas de manipuladores de eventos herdados no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9cd11-137">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="9cd11-138">Walkthrough: herdar de um controle de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9cd11-138">Walkthrough: Inheriting from a Windows Forms Control</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
