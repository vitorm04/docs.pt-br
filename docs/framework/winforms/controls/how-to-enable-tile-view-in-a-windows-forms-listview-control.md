---
title: Como habilitar exibição lado a lado em um controle ListView dos Windows Forms
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
ms.openlocfilehash: 489b9a9d0341391c756175acb19d962d642eb7b2
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960454"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a><span data-ttu-id="13dab-102">Como habilitar exibição lado a lado em um controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="13dab-102">How to: Enable Tile View in a Windows Forms ListView Control</span></span>
<span data-ttu-id="13dab-103">Com o recurso exibição de bloco do controle de <xref:System.Windows.Forms.ListView>, você pode fornecer um equilíbrio visual entre informações gráficas e textuais.</span><span class="sxs-lookup"><span data-stu-id="13dab-103">With the tile view feature of the <xref:System.Windows.Forms.ListView> control, you can provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="13dab-104">As informações textuais exibidas para um item na exibição lado a lado são as mesmas que as informações de coluna definidas para exibição de detalhes.</span><span class="sxs-lookup"><span data-stu-id="13dab-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="13dab-105">O modo de exibição de bloco funciona em combinação com os recursos de agrupamento ou marca de inserção no controle de <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="13dab-105">Tile view works in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="13dab-106">O modo de exibição lado a lado usa um ícone de 32 x 32 pixels e várias linhas de texto, conforme mostrado nas imagens a seguir.</span><span class="sxs-lookup"><span data-stu-id="13dab-106">The tile view uses a 32 x 32 pixel icon and several lines of text, as shown in the following images.</span></span>  
  
 <span data-ttu-id="13dab-107">![Exibição lado a lado em um controle ListView](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Ícones e texto da exibição lado a lado")</span><span class="sxs-lookup"><span data-stu-id="13dab-107">![Tile View in a ListView Control](./media/how-to-enable-tile-view-in-a-windows-forms-listview-control/tile-view-in-listview-control.gif "Tile view icons and text")</span></span>  
 
 <span data-ttu-id="13dab-108">Para habilitar a exibição de bloco, defina a propriedade <xref:System.Windows.Forms.ListView.View%2A> como <xref:System.Windows.Forms.View.Tile>.</span><span class="sxs-lookup"><span data-stu-id="13dab-108">To enable tile view, set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Tile>.</span></span> <span data-ttu-id="13dab-109">Você pode ajustar o tamanho dos blocos definindo a propriedade <xref:System.Windows.Forms.ListView.TileSize%2A> e o número de linhas de texto exibidas no bloco ajustando a coleção de <xref:System.Windows.Forms.ListView.Columns%2A>.</span><span class="sxs-lookup"><span data-stu-id="13dab-109">You can adjust the size of the tiles by setting the <xref:System.Windows.Forms.ListView.TileSize%2A> property, and the number of text lines displayed in the tile by adjusting the <xref:System.Windows.Forms.ListView.Columns%2A> collection.</span></span>  
  
### <a name="to-set-tile-view-programmatically"></a><span data-ttu-id="13dab-110">Para definir a exibição lado a lado programaticamente</span><span class="sxs-lookup"><span data-stu-id="13dab-110">To set tile view programmatically</span></span>  
  
1. <span data-ttu-id="13dab-111">Use a enumeração <xref:System.Windows.Forms.View> do controle de <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="13dab-111">Use the <xref:System.Windows.Forms.View> enumeration of the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a><span data-ttu-id="13dab-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13dab-112">Example</span></span>  
 <span data-ttu-id="13dab-113">O exemplo de código completo a seguir demonstra a exibição lado a lado com blocos modificados para mostrar as três linhas de texto.</span><span class="sxs-lookup"><span data-stu-id="13dab-113">The following complete code example demonstrates Tile view with tiles modified to show three lines of text.</span></span> <span data-ttu-id="13dab-114">O tamanho de bloco foi ajustado para evitar encapsulamento de linha.</span><span class="sxs-lookup"><span data-stu-id="13dab-114">The tile size has been adjusted to prevent line-wrapping.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="13dab-115">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="13dab-115">Compiling the Code</span></span>  
 <span data-ttu-id="13dab-116">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="13dab-116">This example requires:</span></span>  
  
- <span data-ttu-id="13dab-117">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="13dab-117">References to the System and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="13dab-118">Um arquivo de ícone denominado book.ico no mesmo diretório do arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="13dab-118">An icon file named book.ico in the same directory as the executable file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13dab-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13dab-119">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="13dab-120">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="13dab-120">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="13dab-121">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="13dab-121">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
