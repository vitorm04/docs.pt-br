---
title: 'Como: Posição de controles nos Windows Forms'
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
ms.openlocfilehash: 2baf311f04209e988f2f5dd562e247ee13ed59ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607154"
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="26ff2-102">Como: Posição de controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26ff2-102">How to: Position Controls on Windows Forms</span></span>
<span data-ttu-id="26ff2-103">Para posicionar controles, use o Designer de formulários do Windows ou especifique o <xref:System.Windows.Forms.Control.Location%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="26ff2-103">To position controls, use the Windows Forms Designer, or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26ff2-104">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="26ff2-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="26ff2-105">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="26ff2-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="26ff2-106">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="26ff2-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="26ff2-107">Posicionar um controle na superfície de design do Designer de Formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="26ff2-107">To position a control on the design surface of the Windows Forms Designer</span></span>  
  
-   <span data-ttu-id="26ff2-108">Arraste o controle para o local apropriado com o mouse.</span><span class="sxs-lookup"><span data-stu-id="26ff2-108">Drag the control to the appropriate location with the mouse.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="26ff2-109">Selecione o controle e mova-o com as teclas de direção para posicioná-lo com mais precisão.</span><span class="sxs-lookup"><span data-stu-id="26ff2-109">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="26ff2-110">Além disso, as *guias de alinhamento* ajudam a posicionar os controles com precisão em seu formulário.</span><span class="sxs-lookup"><span data-stu-id="26ff2-110">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="26ff2-111">Para obter mais informações, confira [Passo a passo: Organizando controles nos Windows Forms usando guias de alinhamento](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="26ff2-111">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>  
  
### <a name="to-position-a-control-using-the-properties-window"></a><span data-ttu-id="26ff2-112">Posicionar um controle usando a janela Propriedades</span><span class="sxs-lookup"><span data-stu-id="26ff2-112">To position a control using the Properties window</span></span>  
  
1.  <span data-ttu-id="26ff2-113">Clique no controle que você deseja posicionar.</span><span class="sxs-lookup"><span data-stu-id="26ff2-113">Click the control you want to position.</span></span>  
  
2.  <span data-ttu-id="26ff2-114">No **propriedades** janela, os valores de tipo para o <xref:System.Windows.Forms.Control.Location%2A> propriedade, separada por uma vírgula, para posicionar o controle dentro de seu contêiner.</span><span class="sxs-lookup"><span data-stu-id="26ff2-114">In the **Properties** window, type values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>  
  
     <span data-ttu-id="26ff2-115">O primeiro número (X) é a distância entre a borda esquerda do contêiner; o segundo número (Y) é a distância entre a borda superior da área do recipiente, medida em pixels.</span><span class="sxs-lookup"><span data-stu-id="26ff2-115">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="26ff2-116">Você pode expandir a <xref:System.Windows.Forms.Control.Location%2A> propriedade para o tipo de **X** e **Y** valores individualmente.</span><span class="sxs-lookup"><span data-stu-id="26ff2-116">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>  
  
### <a name="to-position-a-control-programmatically"></a><span data-ttu-id="26ff2-117">Posicionar um controle com programação</span><span class="sxs-lookup"><span data-stu-id="26ff2-117">To position a control programmatically</span></span>  
  
1.  <span data-ttu-id="26ff2-118">Defina as <xref:System.Windows.Forms.Control.Location%2A> propriedade do controle para um <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="26ff2-118">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>  
  
    ```vb  
    Button1.Location = New Point(100, 100)  
    ```  
  
    ```csharp  
    button1.Location = new Point(100, 100);  
    ```  
  
    ```cpp  
    button1->Location = Point(100, 100);  
    ```  
  
2.  <span data-ttu-id="26ff2-119">Altere a coordenada X do local do controle usando o <xref:System.Windows.Forms.Control.Left%2A> subpropriedade.</span><span class="sxs-lookup"><span data-stu-id="26ff2-119">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>  
  
    ```vb  
    Button1.Left = 300  
    ```  
  
    ```csharp  
    button1.Left = 300;  
    ```  
  
    ```cpp  
    button1->Left = 300;  
    ```  
  
### <a name="to-increment-a-controls-location-programmatically"></a><span data-ttu-id="26ff2-120">Incrementar o local de um controle com programação</span><span class="sxs-lookup"><span data-stu-id="26ff2-120">To increment a control's location programmatically</span></span>  
  
1.  <span data-ttu-id="26ff2-121">Defina o <xref:System.Windows.Forms.Control.Left%2A> subpropriedade para incrementar a coordenada X do controle.</span><span class="sxs-lookup"><span data-stu-id="26ff2-121">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>  
  
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
    >  <span data-ttu-id="26ff2-122">Use o <xref:System.Windows.Forms.Control.Location%2A> posiciona de propriedade para definir um controle X e Y simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="26ff2-122">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="26ff2-123">Para definir uma posição individualmente, use o controle <xref:System.Windows.Forms.Control.Left%2A> (**X**) ou <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subpropriedade.</span><span class="sxs-lookup"><span data-stu-id="26ff2-123">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="26ff2-124">Não tente definir implicitamente as coordenadas X e Y do <xref:System.Drawing.Point> estrutura que representa o local do botão, pois essa estrutura contém uma cópia das coordenadas do botão.</span><span class="sxs-lookup"><span data-stu-id="26ff2-124">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26ff2-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26ff2-125">See also</span></span>
- [<span data-ttu-id="26ff2-126">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26ff2-126">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)
- [<span data-ttu-id="26ff2-127">Passo a passo: Organizando controles nos formulários do Windows usando guias de alinhamento</span><span class="sxs-lookup"><span data-stu-id="26ff2-127">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="26ff2-128">Passo a passo: Organizando controles nos Windows Forms utilizando um TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="26ff2-128">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="26ff2-129">Passo a passo: Organizando controles nos Windows Forms utilizando um FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="26ff2-129">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="26ff2-130">Organizando Controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26ff2-130">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="26ff2-131">Rotulando controles individuais dos Windows Forms e fornecendo atalhos para eles</span><span class="sxs-lookup"><span data-stu-id="26ff2-131">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="26ff2-132">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26ff2-132">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="26ff2-133">Controles dos Windows Forms por função</span><span class="sxs-lookup"><span data-stu-id="26ff2-133">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
- [<span data-ttu-id="26ff2-134">Como: Defina o local da tela dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26ff2-134">How to: Set the Screen Location of Windows Forms</span></span>](https://msdn.microsoft.com/library/cb023ab7-dea7-4284-9aa6-8c03c59b60c6)
