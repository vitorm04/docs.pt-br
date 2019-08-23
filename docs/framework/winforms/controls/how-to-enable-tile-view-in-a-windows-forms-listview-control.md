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
ms.openlocfilehash: 44d34ddb00005a0fb86b2d06c4c14e2a5b949819
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966687"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a><span data-ttu-id="7106b-102">Como: Habilitar a exibição de bloco em um controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7106b-102">How to: Enable Tile View in a Windows Forms ListView Control</span></span>
<span data-ttu-id="7106b-103">Com o recurso exibição de bloco do <xref:System.Windows.Forms.ListView> controle, você pode fornecer um equilíbrio visual entre informações gráficas e textuais.</span><span class="sxs-lookup"><span data-stu-id="7106b-103">With the tile view feature of the <xref:System.Windows.Forms.ListView> control, you can provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="7106b-104">As informações textuais exibidas para um item na exibição lado a lado são as mesmas que as informações de coluna definidas para exibição de detalhes.</span><span class="sxs-lookup"><span data-stu-id="7106b-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="7106b-105">O modo de exibição de bloco funciona em combinação com os recursos de agrupamento ou <xref:System.Windows.Forms.ListView> marca de inserção no controle.</span><span class="sxs-lookup"><span data-stu-id="7106b-105">Tile view works in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="7106b-106">O modo de exibição lado a lado usa um ícone de 32 x 32 pixels e várias linhas de texto, conforme mostrado nas imagens a seguir.</span><span class="sxs-lookup"><span data-stu-id="7106b-106">The tile view uses a 32 x 32 pixel icon and several lines of text, as shown in the following images.</span></span>  
  
 <span data-ttu-id="7106b-107">![Exibição de bloco em um controle ListView](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Texto e ícones de exibição de bloco")</span><span class="sxs-lookup"><span data-stu-id="7106b-107">![Tile View in a ListView Control](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Tile view icons and text")</span></span>  
 
 <span data-ttu-id="7106b-108">Para habilitar a exibição de bloco, <xref:System.Windows.Forms.ListView.View%2A> defina a <xref:System.Windows.Forms.View.Tile>Propriedade como.</span><span class="sxs-lookup"><span data-stu-id="7106b-108">To enable tile view, set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Tile>.</span></span> <span data-ttu-id="7106b-109">Você pode ajustar o tamanho dos blocos definindo a <xref:System.Windows.Forms.ListView.TileSize%2A> Propriedade e o número de linhas de texto exibidas no bloco ajustando a <xref:System.Windows.Forms.ListView.Columns%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="7106b-109">You can adjust the size of the tiles by setting the <xref:System.Windows.Forms.ListView.TileSize%2A> property, and the number of text lines displayed in the tile by adjusting the <xref:System.Windows.Forms.ListView.Columns%2A> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7106b-110">A exibição de bloco está disponível somente [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] em quando o aplicativo chama <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> o método.</span><span class="sxs-lookup"><span data-stu-id="7106b-110">The tile view is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7106b-111">Em sistemas operacionais anteriores, qualquer código relacionado à exibição de bloco não tem nenhum efeito e o <xref:System.Windows.Forms.ListView> controle é exibido na exibição de ícones grandes.</span><span class="sxs-lookup"><span data-stu-id="7106b-111">On earlier operating systems, any code related to the tile view has no effect, and the <xref:System.Windows.Forms.ListView> control displays in the large icon view.</span></span> <span data-ttu-id="7106b-112">Para obter mais informações, consulte <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7106b-112">For more information, see <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-set-tile-view-programmatically"></a><span data-ttu-id="7106b-113">Para definir a exibição lado a lado programaticamente</span><span class="sxs-lookup"><span data-stu-id="7106b-113">To set tile view programmatically</span></span>  
  
1. <span data-ttu-id="7106b-114">Use a <xref:System.Windows.Forms.View> enumeração <xref:System.Windows.Forms.ListView> do controle.</span><span class="sxs-lookup"><span data-stu-id="7106b-114">Use the <xref:System.Windows.Forms.View> enumeration of the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a><span data-ttu-id="7106b-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7106b-115">Example</span></span>  
 <span data-ttu-id="7106b-116">O exemplo de código completo a seguir demonstra a exibição lado a lado com blocos modificados para mostrar as três linhas de texto.</span><span class="sxs-lookup"><span data-stu-id="7106b-116">The following complete code example demonstrates Tile view with tiles modified to show three lines of text.</span></span> <span data-ttu-id="7106b-117">O tamanho de bloco foi ajustado para evitar encapsulamento de linha.</span><span class="sxs-lookup"><span data-stu-id="7106b-117">The tile size has been adjusted to prevent line-wrapping.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7106b-118">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="7106b-118">Compiling the Code</span></span>  
 <span data-ttu-id="7106b-119">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="7106b-119">This example requires:</span></span>  
  
- <span data-ttu-id="7106b-120">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="7106b-120">References to the System and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="7106b-121">Um arquivo de ícone denominado book.ico no mesmo diretório do arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="7106b-121">An icon file named book.ico in the same directory as the executable file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7106b-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7106b-122">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="7106b-123">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="7106b-123">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="7106b-124">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="7106b-124">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
