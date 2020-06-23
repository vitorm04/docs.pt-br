---
title: posicionar controles
description: Saiba como usar o Designer de Formulários do Windows no Visual Studio ou a propriedade Location para posicionar seus controles.
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
ms.openlocfilehash: 0aa3faade71e0f7e0a9d5e676327a80747524b8c
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904293"
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="7129d-103">Como: posicionar controles em Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7129d-103">How to: Position controls on Windows Forms</span></span>

<span data-ttu-id="7129d-104">Para posicionar controles, use o Designer de Formulários do Windows no Visual Studio ou especifique a <xref:System.Windows.Forms.Control.Location%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="7129d-104">To position controls, use the Windows Forms Designer in Visual Studio or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="7129d-105">Posicionar um controle na superfície de design do Designer de Formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="7129d-105">Position a control on the design surface of the Windows Forms Designer</span></span>

<span data-ttu-id="7129d-106">No Visual Studio, arraste o controle para o local apropriado com o mouse.</span><span class="sxs-lookup"><span data-stu-id="7129d-106">In Visual Studio, drag the control to the appropriate location with the mouse.</span></span>

> [!NOTE]
> <span data-ttu-id="7129d-107">Selecione o controle e mova-o com as teclas de direção para posicioná-lo com mais precisão.</span><span class="sxs-lookup"><span data-stu-id="7129d-107">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="7129d-108">Além disso, as *guias de alinhamento* ajudam a posicionar os controles com precisão em seu formulário.</span><span class="sxs-lookup"><span data-stu-id="7129d-108">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="7129d-109">Para obter mais informações, consulte [Instruções passo a passo: organizando controles nos Windows Forms usando guias de alinhamento](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="7129d-109">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

## <a name="position-a-control-using-the-properties-window"></a><span data-ttu-id="7129d-110">Posicionar um controle usando o janela Propriedades</span><span class="sxs-lookup"><span data-stu-id="7129d-110">Position a control using the Properties window</span></span>

1. <span data-ttu-id="7129d-111">No Visual Studio, selecione o controle que você deseja posicionar.</span><span class="sxs-lookup"><span data-stu-id="7129d-111">In Visual Studio, select the control you want to position.</span></span>

2. <span data-ttu-id="7129d-112">Na janela **Propriedades** , insira valores para a <xref:System.Windows.Forms.Control.Location%2A> propriedade, separados por uma vírgula, para posicionar o controle dentro de seu contêiner.</span><span class="sxs-lookup"><span data-stu-id="7129d-112">In the **Properties** window, enter values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>

   <span data-ttu-id="7129d-113">O primeiro número (X) é a distância entre a borda esquerda do contêiner; o segundo número (Y) é a distância entre a borda superior da área do recipiente, medida em pixels.</span><span class="sxs-lookup"><span data-stu-id="7129d-113">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>

   > [!NOTE]
   > <span data-ttu-id="7129d-114">Você pode expandir a <xref:System.Windows.Forms.Control.Location%2A> propriedade para digitar os valores **X** e **Y** individualmente.</span><span class="sxs-lookup"><span data-stu-id="7129d-114">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>

## <a name="position-a-control-programmatically"></a><span data-ttu-id="7129d-115">Posicionar um controle programaticamente</span><span class="sxs-lookup"><span data-stu-id="7129d-115">Position a control programmatically</span></span>

1. <span data-ttu-id="7129d-116">Defina a <xref:System.Windows.Forms.Control.Location%2A> Propriedade do controle como um <xref:System.Drawing.Point> .</span><span class="sxs-lookup"><span data-stu-id="7129d-116">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. <span data-ttu-id="7129d-117">Altere a coordenada X do local do controle usando o <xref:System.Windows.Forms.Control.Left%2A> subpropriedade.</span><span class="sxs-lookup"><span data-stu-id="7129d-117">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a><span data-ttu-id="7129d-118">Incrementar o local de um controle programaticamente</span><span class="sxs-lookup"><span data-stu-id="7129d-118">Increment a control's location programmatically</span></span>

<span data-ttu-id="7129d-119">Defina <xref:System.Windows.Forms.Control.Left%2A> subpropriedade para incrementar a coordenada X do controle.</span><span class="sxs-lookup"><span data-stu-id="7129d-119">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>

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
> <span data-ttu-id="7129d-120">Use a <xref:System.Windows.Forms.Control.Location%2A> propriedade para definir as posições X e Y de um controle simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="7129d-120">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="7129d-121">Para definir uma posição individualmente, use o <xref:System.Windows.Forms.Control.Left%2A> (**X**) ou <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subpropriedade do controle.</span><span class="sxs-lookup"><span data-stu-id="7129d-121">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="7129d-122">Não tente definir implicitamente as coordenadas X e Y da <xref:System.Drawing.Point> estrutura que representa o local do botão, pois essa estrutura contém uma cópia das coordenadas do botão.</span><span class="sxs-lookup"><span data-stu-id="7129d-122">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="7129d-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="7129d-123">See also</span></span>

- [<span data-ttu-id="7129d-124">Controles de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7129d-124">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="7129d-125">Instruções passo a passo: organizando controles no Windows Forms usando guias de alinhamento</span><span class="sxs-lookup"><span data-stu-id="7129d-125">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="7129d-126">Explicação passo a passo: organizando controles no Windows Forms utilizando um TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7129d-126">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="7129d-127">Passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7129d-127">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="7129d-128">Identificando controles dos Windows Forms individuais e fornecendo atalhos para eles</span><span class="sxs-lookup"><span data-stu-id="7129d-128">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="7129d-129">Controles a serem usados em Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7129d-129">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="7129d-130">Controles dos Windows Forms por função</span><span class="sxs-lookup"><span data-stu-id="7129d-130">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- <span data-ttu-id="7129d-131">[Como configurar o local da tela dos Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7129d-131">[How to: Set the Screen Location of Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span></span>
