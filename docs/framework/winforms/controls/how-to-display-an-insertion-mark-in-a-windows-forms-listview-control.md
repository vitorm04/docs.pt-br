---
title: Exibir uma marca de inserção no controle ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ListView control [Windows Forms], drag operations
- graphics [Windows Forms], insertion marks
- drop and drag [Windows Forms], insertion marks
- insertion marks
ms.assetid: 88d0a15b-25fd-4dc3-a685-297351311940
ms.openlocfilehash: eeae51223a21baaf4d2412de2ce11d0c6cbcae27
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742215"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a><span data-ttu-id="2e245-102">Como exibir uma marca de inserção em um controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2e245-102">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>
<span data-ttu-id="2e245-103">A marca de inserção no controle de <xref:System.Windows.Forms.ListView> mostra aos usuários o ponto em que os itens arrastados serão inseridos.</span><span class="sxs-lookup"><span data-stu-id="2e245-103">The insertion mark in the <xref:System.Windows.Forms.ListView> control shows users the point where dragged items will be inserted.</span></span> <span data-ttu-id="2e245-104">Quando um usuário arrasta um item para um ponto entre dois outros itens, a marca de inserção mostra o novo local esperado do item.</span><span class="sxs-lookup"><span data-stu-id="2e245-104">When a user drags an item to a point between two other items, the insertion mark shows the item's expected new location.</span></span>  
  
 <span data-ttu-id="2e245-105">A imagem a seguir mostra uma marca de inserção:</span><span class="sxs-lookup"><span data-stu-id="2e245-105">The following image shows an insertion mark:</span></span>  
  
 <span data-ttu-id="2e245-106">![Captura de tela que mostra uma marca de inserção de ListView.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span><span class="sxs-lookup"><span data-stu-id="2e245-106">![Screenshot that shows a ListView insertion mark.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")</span></span>  
  
 <span data-ttu-id="2e245-107">O exemplo de código a seguir demonstra como usar esse recurso.</span><span class="sxs-lookup"><span data-stu-id="2e245-107">The following code example demonstrates how to use this feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e245-108">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="2e245-108">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2e245-109">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="2e245-109">Compiling the Code</span></span>  
 <span data-ttu-id="2e245-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="2e245-110">This example requires:</span></span>  
  
- <span data-ttu-id="2e245-111">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="2e245-111">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e245-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e245-112">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [<span data-ttu-id="2e245-113">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="2e245-113">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="2e245-114">Visão geral do controle ListView</span><span class="sxs-lookup"><span data-stu-id="2e245-114">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="2e245-115">Instruções Passo a Passo: Executando uma Operação do Tipo "Arrastar e Soltar" nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2e245-115">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
