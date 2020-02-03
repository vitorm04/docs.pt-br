---
title: associar objetos a controles DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
ms.openlocfilehash: d5aa5cb64c7fb2b82d69d6c87134ee901b84f5c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746705"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a><span data-ttu-id="c6d5c-102">Como associar objetos a controles DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6d5c-102">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="c6d5c-103">O exemplo de código a seguir demonstra como associar uma coleção de objetos a um controle de <xref:System.Windows.Forms.DataGridView> para que cada objeto seja exibido como uma linha separada.</span><span class="sxs-lookup"><span data-stu-id="c6d5c-103">The following code example demonstrates how to bind a collection of objects to a <xref:System.Windows.Forms.DataGridView> control so that each object displays as a separate row.</span></span> <span data-ttu-id="c6d5c-104">Este exemplo também ilustra como exibir uma propriedade com um tipo de enumeração em um <xref:System.Windows.Forms.DataGridViewComboBoxColumn> para que a lista suspensa caixa de combinação contenha os valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="c6d5c-104">This example also illustrates how to display a property with an enumeration type in a <xref:System.Windows.Forms.DataGridViewComboBoxColumn> so that the combo box drop-down list contains the enumeration values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6d5c-105">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c6d5c-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c6d5c-106">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="c6d5c-106">Compiling the Code</span></span>  
 <span data-ttu-id="c6d5c-107">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="c6d5c-107">This example requires:</span></span>  
  
- <span data-ttu-id="c6d5c-108">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="c6d5c-108">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6d5c-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6d5c-109">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="c6d5c-110">Exibindo dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6d5c-110">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="c6d5c-111">Como acessar objetos associados a linhas DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6d5c-111">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
