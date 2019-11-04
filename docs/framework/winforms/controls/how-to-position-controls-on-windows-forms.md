---
title: Como posicionar controles nos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Location
- Location.Y
- Location.X
helpviewer_keywords:
- controls [Windows Forms]
- controls [Windows Forms], moving
- snaplines
- controls [Windows Forms], positioning
ms.assetid: 4693977e-34a4-4f19-8221-68c3120c2b2b
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bb57d14397a4626e01c41dd687dfed7331282a10
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458333"
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="535cc-102">Como: posicionar controles em Windows Forms</span><span class="sxs-lookup"><span data-stu-id="535cc-102">How to: Position controls on Windows Forms</span></span>

<span data-ttu-id="535cc-103">Para posicionar controles, use o Designer de Formulários do Windows no Visual Studio ou especifique a propriedade <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="535cc-103">To position controls, use the Windows Forms Designer in Visual Studio or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="535cc-104">Posicionar um controle na superfície de design do Designer de Formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="535cc-104">Position a control on the design surface of the Windows Forms Designer</span></span>

<span data-ttu-id="535cc-105">No Visual Studio, arraste o controle para o local apropriado com o mouse.</span><span class="sxs-lookup"><span data-stu-id="535cc-105">In Visual Studio, drag the control to the appropriate location with the mouse.</span></span>

> [!NOTE]
> <span data-ttu-id="535cc-106">Selecione o controle e mova-o com as teclas de direção para posicioná-lo com mais precisão.</span><span class="sxs-lookup"><span data-stu-id="535cc-106">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="535cc-107">Além disso, as *guias de alinhamento* ajudam a posicionar os controles com precisão em seu formulário.</span><span class="sxs-lookup"><span data-stu-id="535cc-107">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="535cc-108">Para obter mais informações, consulte [Instruções passo a passo: organizando controles nos Windows Forms usando guias de alinhamento](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="535cc-108">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

## <a name="position-a-control-using-the-properties-window"></a><span data-ttu-id="535cc-109">Posicionar um controle usando o janela Propriedades</span><span class="sxs-lookup"><span data-stu-id="535cc-109">Position a control using the Properties window</span></span>

1. <span data-ttu-id="535cc-110">No Visual Studio, selecione o controle que você deseja posicionar.</span><span class="sxs-lookup"><span data-stu-id="535cc-110">In Visual Studio, select the control you want to position.</span></span>

2. <span data-ttu-id="535cc-111">Na janela **Propriedades** , insira valores para a propriedade <xref:System.Windows.Forms.Control.Location%2A>, separados por uma vírgula, para posicionar o controle dentro de seu contêiner.</span><span class="sxs-lookup"><span data-stu-id="535cc-111">In the **Properties** window, enter values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>

   <span data-ttu-id="535cc-112">O primeiro número (X) é a distância entre a borda esquerda do contêiner; o segundo número (Y) é a distância entre a borda superior da área do recipiente, medida em pixels.</span><span class="sxs-lookup"><span data-stu-id="535cc-112">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>

   > [!NOTE]
   > <span data-ttu-id="535cc-113">Você pode expandir a propriedade <xref:System.Windows.Forms.Control.Location%2A> para digitar os valores **X** e **Y** individualmente.</span><span class="sxs-lookup"><span data-stu-id="535cc-113">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>

## <a name="position-a-control-programmatically"></a><span data-ttu-id="535cc-114">Posicionar um controle programaticamente</span><span class="sxs-lookup"><span data-stu-id="535cc-114">Position a control programmatically</span></span>

1. <span data-ttu-id="535cc-115">Defina a propriedade <xref:System.Windows.Forms.Control.Location%2A> do controle como uma <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="535cc-115">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. <span data-ttu-id="535cc-116">Altere a coordenada X do local do controle usando o <xref:System.Windows.Forms.Control.Left%2A> subpropriedade.</span><span class="sxs-lookup"><span data-stu-id="535cc-116">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a><span data-ttu-id="535cc-117">Incrementar o local de um controle programaticamente</span><span class="sxs-lookup"><span data-stu-id="535cc-117">Increment a control's location programmatically</span></span>

<span data-ttu-id="535cc-118">Defina o <xref:System.Windows.Forms.Control.Left%2A> subpropriedade para incrementar a coordenada X do controle.</span><span class="sxs-lookup"><span data-stu-id="535cc-118">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>

```vb
Button1.Left += 200
```

```csharp
button1.Left += 200;
```

```cpp
button1->Left += 200;
```

> [!NOTE]
> <span data-ttu-id="535cc-119">Use a propriedade <xref:System.Windows.Forms.Control.Location%2A> para definir as posições X e Y de um controle simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="535cc-119">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="535cc-120">Para definir uma posição individualmente, use o <xref:System.Windows.Forms.Control.Left%2A> do controle (**X**) ou <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subpropriedade.</span><span class="sxs-lookup"><span data-stu-id="535cc-120">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="535cc-121">Não tente definir implicitamente as coordenadas X e Y da estrutura de <xref:System.Drawing.Point> que representa o local do botão, pois essa estrutura contém uma cópia das coordenadas do botão.</span><span class="sxs-lookup"><span data-stu-id="535cc-121">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="535cc-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="535cc-122">See also</span></span>

- [<span data-ttu-id="535cc-123">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="535cc-123">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="535cc-124">Instruções passo a passo: organizando controles no Windows Forms usando guias de alinhamento</span><span class="sxs-lookup"><span data-stu-id="535cc-124">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="535cc-125">Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="535cc-125">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="535cc-126">Passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="535cc-126">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="535cc-127">Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles</span><span class="sxs-lookup"><span data-stu-id="535cc-127">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="535cc-128">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="535cc-128">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="535cc-129">Controles dos Windows Forms por função</span><span class="sxs-lookup"><span data-stu-id="535cc-129">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- <span data-ttu-id="535cc-130">[Como configurar o local da tela dos Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="535cc-130">[How to: Set the Screen Location of Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span></span>
