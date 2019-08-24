---
title: 'Como: Posicionar controles nos Windows Forms'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1cc2cb4c749b7290a6edf914a8e6a697006ef43c
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987079"
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="4629b-102">Como: Posicionar controles em Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4629b-102">How to: Position controls on Windows Forms</span></span>

<span data-ttu-id="4629b-103">Para posicionar controles, use o designer de formulários do Windows no Visual Studio ou especifique <xref:System.Windows.Forms.Control.Location%2A> a propriedade.</span><span class="sxs-lookup"><span data-stu-id="4629b-103">To position controls, use the Windows Forms Designer in Visual Studio or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="4629b-104">Posicionar um controle na superfície de design do Designer de Formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="4629b-104">Position a control on the design surface of the Windows Forms Designer</span></span>

<span data-ttu-id="4629b-105">No Visual Studio, arraste o controle para o local apropriado com o mouse.</span><span class="sxs-lookup"><span data-stu-id="4629b-105">In Visual Studio, drag the control to the appropriate location with the mouse.</span></span>

> [!NOTE]
> <span data-ttu-id="4629b-106">Selecione o controle e mova-o com as teclas de direção para posicioná-lo com mais precisão.</span><span class="sxs-lookup"><span data-stu-id="4629b-106">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="4629b-107">Além disso, as *guias de alinhamento* ajudam a posicionar os controles com precisão em seu formulário.</span><span class="sxs-lookup"><span data-stu-id="4629b-107">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="4629b-108">Para obter mais informações, confira [Passo a passo: Organizando controles em Windows Forms usando Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="4629b-108">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

## <a name="position-a-control-using-the-properties-window"></a><span data-ttu-id="4629b-109">Posicionar um controle usando o janela Propriedades</span><span class="sxs-lookup"><span data-stu-id="4629b-109">Position a control using the Properties window</span></span>

1. <span data-ttu-id="4629b-110">No Visual Studio, selecione o controle que você deseja posicionar.</span><span class="sxs-lookup"><span data-stu-id="4629b-110">In Visual Studio, select the control you want to position.</span></span>

2. <span data-ttu-id="4629b-111">Na janela **Propriedades** , insira valores para a <xref:System.Windows.Forms.Control.Location%2A> Propriedade, separados por uma vírgula, para posicionar o controle dentro de seu contêiner.</span><span class="sxs-lookup"><span data-stu-id="4629b-111">In the **Properties** window, enter values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>

   <span data-ttu-id="4629b-112">O primeiro número (X) é a distância entre a borda esquerda do contêiner; o segundo número (Y) é a distância entre a borda superior da área do recipiente, medida em pixels.</span><span class="sxs-lookup"><span data-stu-id="4629b-112">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>

   > [!NOTE]
   > <span data-ttu-id="4629b-113">Você pode expandir a <xref:System.Windows.Forms.Control.Location%2A> propriedade para digitar os valores **X** e **Y** individualmente.</span><span class="sxs-lookup"><span data-stu-id="4629b-113">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>

## <a name="position-a-control-programmatically"></a><span data-ttu-id="4629b-114">Posicionar um controle programaticamente</span><span class="sxs-lookup"><span data-stu-id="4629b-114">Position a control programmatically</span></span>

1. <span data-ttu-id="4629b-115">Defina a <xref:System.Windows.Forms.Control.Location%2A> Propriedade do controle como um <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="4629b-115">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. <span data-ttu-id="4629b-116">Altere a coordenada X do local do controle usando o <xref:System.Windows.Forms.Control.Left%2A> subpropriedade.</span><span class="sxs-lookup"><span data-stu-id="4629b-116">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a><span data-ttu-id="4629b-117">Incrementar o local de um controle programaticamente</span><span class="sxs-lookup"><span data-stu-id="4629b-117">Increment a control's location programmatically</span></span>

<span data-ttu-id="4629b-118"><xref:System.Windows.Forms.Control.Left%2A> Defina subpropriedade para incrementar a coordenada X do controle.</span><span class="sxs-lookup"><span data-stu-id="4629b-118">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>

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
> <span data-ttu-id="4629b-119">Use a <xref:System.Windows.Forms.Control.Location%2A> propriedade para definir as posições X e Y de um controle simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="4629b-119">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="4629b-120">Para definir uma posição individualmente, use o <xref:System.Windows.Forms.Control.Left%2A> (**X**) ou <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subpropriedade do controle.</span><span class="sxs-lookup"><span data-stu-id="4629b-120">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="4629b-121">Não tente definir implicitamente as coordenadas X e Y da <xref:System.Drawing.Point> estrutura que representa o local do botão, pois essa estrutura contém uma cópia das coordenadas do botão.</span><span class="sxs-lookup"><span data-stu-id="4629b-121">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="4629b-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4629b-122">See also</span></span>

- [<span data-ttu-id="4629b-123">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4629b-123">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="4629b-124">Passo a passo: Organizando controles em Windows Forms usando Snaplines</span><span class="sxs-lookup"><span data-stu-id="4629b-124">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="4629b-125">Passo a passo: Organizando controles em Windows Forms usando um TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="4629b-125">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="4629b-126">Passo a passo: Organizando controles em Windows Forms usando um FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="4629b-126">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="4629b-127">Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles</span><span class="sxs-lookup"><span data-stu-id="4629b-127">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="4629b-128">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4629b-128">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="4629b-129">Controles dos Windows Forms por função</span><span class="sxs-lookup"><span data-stu-id="4629b-129">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- <span data-ttu-id="4629b-130">[Como: Definir o local da tela de Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4629b-130">[How to: Set the Screen Location of Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span></span>
