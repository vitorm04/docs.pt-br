---
title: 'Como: Habilitar a exibição de bloco em um controle ListView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tile view feature
- tiling
- Windows Forms, controls
- ListView control [Windows Forms], tile view
ms.assetid: c20e67a3-2d94-413d-9fcf-ecbd0fe251da
ms.openlocfilehash: 14eb21fa0285275e510b865c5cee7d1fc82fd0fd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326990"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a><span data-ttu-id="e01c4-102">Como: Habilitar a exibição de bloco em um controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e01c4-102">How to: Enable Tile View in a Windows Forms ListView Control</span></span>
<span data-ttu-id="e01c4-103">Com o recurso de exibição de bloco a <xref:System.Windows.Forms.ListView> controle, você pode fornecer um equilíbrio visual entre informações gráficas e textuais.</span><span class="sxs-lookup"><span data-stu-id="e01c4-103">With the tile view feature of the <xref:System.Windows.Forms.ListView> control, you can provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="e01c4-104">As informações textuais exibidas para um item na exibição lado a lado são as mesmas que as informações de coluna definidas para exibição de detalhes.</span><span class="sxs-lookup"><span data-stu-id="e01c4-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="e01c4-105">Exibição lado a lado funciona em combinação com recursos de marca de agrupamento ou inserção no <xref:System.Windows.Forms.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="e01c4-105">Tile view works in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="e01c4-106">O modo de exibição lado a lado usa um ícone de 32 x 32 pixels e várias linhas de texto, conforme mostrado nas imagens a seguir.</span><span class="sxs-lookup"><span data-stu-id="e01c4-106">The tile view uses a 32 x 32 pixel icon and several lines of text, as shown in the following images.</span></span>  
  
 <span data-ttu-id="e01c4-107">![Exibição em um controle ListView lado a lado](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "lado a lado exibir ícones e texto")</span><span class="sxs-lookup"><span data-stu-id="e01c4-107">![Tile View in a ListView Control](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Tile view icons and text")</span></span>  
 
 <span data-ttu-id="e01c4-108">Para habilitar exibição lado a lado, defina as <xref:System.Windows.Forms.ListView.View%2A> propriedade para <xref:System.Windows.Forms.View.Tile>.</span><span class="sxs-lookup"><span data-stu-id="e01c4-108">To enable tile view, set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Tile>.</span></span> <span data-ttu-id="e01c4-109">Você pode ajustar o tamanho dos blocos, definindo o <xref:System.Windows.Forms.ListView.TileSize%2A> propriedade e o número de linhas de texto exibidas no bloco ajustando a <xref:System.Windows.Forms.ListView.Columns%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="e01c4-109">You can adjust the size of the tiles by setting the <xref:System.Windows.Forms.ListView.TileSize%2A> property, and the number of text lines displayed in the tile by adjusting the <xref:System.Windows.Forms.ListView.Columns%2A> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e01c4-110">A exibição lado a lado está disponível apenas no [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] quando seu aplicativo chama o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="e01c4-110">The tile view is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e01c4-111">Em sistemas operacionais anteriores, qualquer código relacionado ao modo de exibição lado a lado não terá efeito e o <xref:System.Windows.Forms.ListView> controle exibe no modo de exibição de ícones grandes.</span><span class="sxs-lookup"><span data-stu-id="e01c4-111">On earlier operating systems, any code related to the tile view has no effect, and the <xref:System.Windows.Forms.ListView> control displays in the large icon view.</span></span> <span data-ttu-id="e01c4-112">Para obter mais informações, consulte <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e01c4-112">For more information, see <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-set-tile-view-programmatically"></a><span data-ttu-id="e01c4-113">Para definir a exibição lado a lado programaticamente</span><span class="sxs-lookup"><span data-stu-id="e01c4-113">To set tile view programmatically</span></span>  
  
1. <span data-ttu-id="e01c4-114">Use o <xref:System.Windows.Forms.View> enumeração do <xref:System.Windows.Forms.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="e01c4-114">Use the <xref:System.Windows.Forms.View> enumeration of the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a><span data-ttu-id="e01c4-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e01c4-115">Example</span></span>  
 <span data-ttu-id="e01c4-116">O exemplo de código completo a seguir demonstra a exibição lado a lado com blocos modificados para mostrar as três linhas de texto.</span><span class="sxs-lookup"><span data-stu-id="e01c4-116">The following complete code example demonstrates Tile view with tiles modified to show three lines of text.</span></span> <span data-ttu-id="e01c4-117">O tamanho de bloco foi ajustado para evitar encapsulamento de linha.</span><span class="sxs-lookup"><span data-stu-id="e01c4-117">The tile size has been adjusted to prevent line-wrapping.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e01c4-118">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e01c4-118">Compiling the Code</span></span>  
 <span data-ttu-id="e01c4-119">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="e01c4-119">This example requires:</span></span>  
  
-   <span data-ttu-id="e01c4-120">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="e01c4-120">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="e01c4-121">Um arquivo de ícone denominado book.ico no mesmo diretório do arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="e01c4-121">An icon file named book.ico in the same directory as the executable file.</span></span>  
  
 <span data-ttu-id="e01c4-122">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e01c4-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e01c4-123">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="e01c4-123">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e01c4-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e01c4-124">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="e01c4-125">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="e01c4-125">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="e01c4-126">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="e01c4-126">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
