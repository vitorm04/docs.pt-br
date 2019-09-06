---
title: 'Como: Herdar de controles do Windows Forms existentes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fcf95e08296f5a8ec5a386ac614482c034e72c8b
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373244"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a><span data-ttu-id="e509b-102">Como: Herdar de controles do Windows Forms existentes</span><span class="sxs-lookup"><span data-stu-id="e509b-102">How to: Inherit from Existing Windows Forms Controls</span></span>

<span data-ttu-id="e509b-103">Se você quiser estender a funcionalidade de um controle existente, poderá criar um controle derivado de um controle existente por meio de herança.</span><span class="sxs-lookup"><span data-stu-id="e509b-103">If you want to extend the functionality of an existing control, you can create a control derived from an existing control through inheritance.</span></span> <span data-ttu-id="e509b-104">Ao herdar de um controle existente, você herda todas as funcionalidades e propriedades visuais desse controle.</span><span class="sxs-lookup"><span data-stu-id="e509b-104">When inheriting from an existing control, you inherit all of the functionality and visual properties of that control.</span></span> <span data-ttu-id="e509b-105">Por exemplo, se você estivesse criando um controle herdado de <xref:System.Windows.Forms.Button>, seu novo controle ficaria e agiria exatamente como um controle <xref:System.Windows.Forms.Button> padrão.</span><span class="sxs-lookup"><span data-stu-id="e509b-105">For example, if you were creating a control that inherited from <xref:System.Windows.Forms.Button>, your new control would look and act exactly like a standard <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="e509b-106">Dessa forma, você poderia estender ou modificar a funcionalidade de seu novo controle por meio da implementação de métodos e propriedades personalizados.</span><span class="sxs-lookup"><span data-stu-id="e509b-106">You could then extend or modify the functionality of your new control through the implementation of custom methods and properties.</span></span> <span data-ttu-id="e509b-107">Em alguns controles, você também pode alterar a aparência visual do seu controle herdado substituindo <xref:System.Windows.Forms.Control.OnPaint%2A> seu método.</span><span class="sxs-lookup"><span data-stu-id="e509b-107">In some controls, you can also change the visual appearance of your inherited control by overriding its <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

## <a name="to-create-an-inherited-control"></a><span data-ttu-id="e509b-108">Criar um controle herdado</span><span class="sxs-lookup"><span data-stu-id="e509b-108">To create an inherited control</span></span>

1. <span data-ttu-id="e509b-109">No Visual Studio, crie um novo projeto de **aplicativo Windows Forms** .</span><span class="sxs-lookup"><span data-stu-id="e509b-109">In Visual Studio, create a new **Windows Forms Application** project.</span></span>

1. <span data-ttu-id="e509b-110">No menu **Projeto**, escolha **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="e509b-110">From the **Project** menu, choose **Add New Item**.</span></span>

    <span data-ttu-id="e509b-111">A caixa de diálogo **Adicionar Novo Item** é exibida.</span><span class="sxs-lookup"><span data-stu-id="e509b-111">The **Add New Item** dialog box appears.</span></span>

1. <span data-ttu-id="e509b-112">Na caixa de diálogo **Adicionar Novo Item**, clique duas vezes em **Controle personalizado**.</span><span class="sxs-lookup"><span data-stu-id="e509b-112">In the **Add New Item** dialog box, double-click **Custom Control**.</span></span>

    <span data-ttu-id="e509b-113">Um novo controle personalizado será adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="e509b-113">A new custom control is added to your project.</span></span>

1. <span data-ttu-id="e509b-114">Se você estiver usando:</span><span class="sxs-lookup"><span data-stu-id="e509b-114">If you using:</span></span>

    - <span data-ttu-id="e509b-115">Visual Basic, na parte superior do **Gerenciador de soluções**, clique em **Mostrar todos os arquivos**.</span><span class="sxs-lookup"><span data-stu-id="e509b-115">Visual Basic, at the top of **Solution Explorer**, click **Show All Files**.</span></span> <span data-ttu-id="e509b-116">Expanda CustomControl1.vb e abra CustomControl1.Designer.vb no Editor de Código.</span><span class="sxs-lookup"><span data-stu-id="e509b-116">Expand CustomControl1.vb and then open CustomControl1.Designer.vb in the Code Editor.</span></span>
    - <span data-ttu-id="e509b-117">C#, abra CustomControl1.cs no editor de código.</span><span class="sxs-lookup"><span data-stu-id="e509b-117">C#, open CustomControl1.cs in the Code Editor.</span></span>

1. <span data-ttu-id="e509b-118">Localize a declaração de classe que herda de <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="e509b-118">Locate the class declaration, which inherits from <xref:System.Windows.Forms.Control>.</span></span>

1. <span data-ttu-id="e509b-119">Altere a classe base para o controle do qual você deseja herdar.</span><span class="sxs-lookup"><span data-stu-id="e509b-119">Change the base class to the control that you want to inherit from.</span></span>

     <span data-ttu-id="e509b-120">Por exemplo, se você quiser herdar de <xref:System.Windows.Forms.Button>, altere a declaração de classe para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e509b-120">For example, if you want to inherit from <xref:System.Windows.Forms.Button>, change the class declaration to the following:</span></span>

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

1. <span data-ttu-id="e509b-121">Se você estiver usando Visual Basic, salve e feche CustomControl1.Designer.vb.</span><span class="sxs-lookup"><span data-stu-id="e509b-121">If you are using Visual Basic, save and close CustomControl1.Designer.vb.</span></span> <span data-ttu-id="e509b-122">Abra CustomControl1.vb no Editor de Código.</span><span class="sxs-lookup"><span data-stu-id="e509b-122">Open CustomControl1.vb in the Code Editor.</span></span>

1. <span data-ttu-id="e509b-123">Implemente os métodos ou propriedades personalizados que o controle incorporará.</span><span class="sxs-lookup"><span data-stu-id="e509b-123">Implement any custom methods or properties that your control will incorporate.</span></span>

1. <span data-ttu-id="e509b-124">Se você quiser modificar a aparência gráfica do seu controle, substitua o <xref:System.Windows.Forms.Control.OnPaint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="e509b-124">If you want to modify the graphical appearance of your control, override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e509b-125">A <xref:System.Windows.Forms.Control.OnPaint%2A> substituição não permitirá que você modifique a aparência de todos os controles.</span><span class="sxs-lookup"><span data-stu-id="e509b-125">Overriding <xref:System.Windows.Forms.Control.OnPaint%2A> will not allow you to modify the appearance of all controls.</span></span> <span data-ttu-id="e509b-126">Esses controles que têm toda a pintura feita pelo Windows (por exemplo, <xref:System.Windows.Forms.TextBox>) nunca chamam seu <xref:System.Windows.Forms.Control.OnPaint%2A> método e, portanto, nunca usarão o código personalizado.</span><span class="sxs-lookup"><span data-stu-id="e509b-126">Those controls that have all of their painting done by Windows (for example, <xref:System.Windows.Forms.TextBox>) never call their <xref:System.Windows.Forms.Control.OnPaint%2A> method, and thus will never use the custom code.</span></span> <span data-ttu-id="e509b-127">Consulte a documentação da ajuda para o controle específico que você deseja modificar para ver se o <xref:System.Windows.Forms.Control.OnPaint%2A> método está disponível.</span><span class="sxs-lookup"><span data-stu-id="e509b-127">Refer to the Help documentation for the particular control you want to modify to see if the <xref:System.Windows.Forms.Control.OnPaint%2A> method is available.</span></span> <span data-ttu-id="e509b-128">Para obter uma lista de todos os controles do Windows Forms, consulte [Controles a serem usados no Windows Forms](controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e509b-128">For a list of all the Windows Form Controls, see [Controls to Use on Windows Forms](controls-to-use-on-windows-forms.md).</span></span> <span data-ttu-id="e509b-129">Se um controle não estiver <xref:System.Windows.Forms.Control.OnPaint%2A> listado como um método de membro, você não poderá alterar sua aparência substituindo esse método.</span><span class="sxs-lookup"><span data-stu-id="e509b-129">If a control does not have <xref:System.Windows.Forms.Control.OnPaint%2A> listed as a member method, you cannot alter its appearance by overriding this method.</span></span> <span data-ttu-id="e509b-130">Para obter mais informações sobre pintura personalizada, consulte [Pintura e renderização de controle personalizado](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="e509b-130">For more information about custom painting, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

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

1. <span data-ttu-id="e509b-131">Salve e teste seu controle.</span><span class="sxs-lookup"><span data-stu-id="e509b-131">Save and test your control.</span></span>

## <a name="see-also"></a><span data-ttu-id="e509b-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e509b-132">See also</span></span>

- [<span data-ttu-id="e509b-133">Variedades de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="e509b-133">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="e509b-134">Como: Herdar da classe de controle</span><span class="sxs-lookup"><span data-stu-id="e509b-134">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="e509b-135">Como: Herdar da classe UserControl</span><span class="sxs-lookup"><span data-stu-id="e509b-135">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="e509b-136">Como: Controles de autor para Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e509b-136">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="e509b-137">Solucionando problemas de manipuladores de eventos herdados no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e509b-137">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="e509b-138">Passo a passo: Herdar de um controle de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e509b-138">Walkthrough: Inheriting from a Windows Forms Control</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
