---
title: 'Como: Associar objetos a controles DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
ms.openlocfilehash: 02c4f94eddfcf782d7d2323787d9b6a9b18db2d5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180252"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a><span data-ttu-id="b8404-102">Como: Associar objetos a controles DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b8404-102">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="b8404-103">O exemplo de código a seguir demonstra como associar uma coleção de objetos para um <xref:System.Windows.Forms.DataGridView> de controle para que cada objeto seja exibido como uma linha separada.</span><span class="sxs-lookup"><span data-stu-id="b8404-103">The following code example demonstrates how to bind a collection of objects to a <xref:System.Windows.Forms.DataGridView> control so that each object displays as a separate row.</span></span> <span data-ttu-id="b8404-104">Este exemplo também ilustra como exibir uma propriedade com um tipo de enumeração em um <xref:System.Windows.Forms.DataGridViewComboBoxColumn> para que a lista suspensa da caixa de combinação contém os valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="b8404-104">This example also illustrates how to display a property with an enumeration type in a <xref:System.Windows.Forms.DataGridViewComboBoxColumn> so that the combo box drop-down list contains the enumeration values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8404-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8404-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b8404-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b8404-106">Compiling the Code</span></span>  
 <span data-ttu-id="b8404-107">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="b8404-107">This example requires:</span></span>  
  
-   <span data-ttu-id="b8404-108">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="b8404-108">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="b8404-109">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b8404-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b8404-110">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="b8404-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8404-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8404-111">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="b8404-112">Exibindo dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b8404-112">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b8404-113">Como: Acessar objetos associados às linhas de DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b8404-113">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
