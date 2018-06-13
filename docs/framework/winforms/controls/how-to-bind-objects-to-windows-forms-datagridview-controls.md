---
title: Como associar objetos a controles DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
ms.openlocfilehash: 9580812be4e15a0b925c5737dc6dfe0e0fdaf407
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530101"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a><span data-ttu-id="66ce6-102">Como associar objetos a controles DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="66ce6-102">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="66ce6-103">O exemplo de código a seguir demonstra como associar uma coleção de objetos para um <xref:System.Windows.Forms.DataGridView> controlar de forma que cada objeto exibido como uma linha separada.</span><span class="sxs-lookup"><span data-stu-id="66ce6-103">The following code example demonstrates how to bind a collection of objects to a <xref:System.Windows.Forms.DataGridView> control so that each object displays as a separate row.</span></span> <span data-ttu-id="66ce6-104">Este exemplo também ilustra como exibir uma propriedade com um tipo de enumeração em um <xref:System.Windows.Forms.DataGridViewComboBoxColumn> para que a lista suspensa da caixa de combinação contém os valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="66ce6-104">This example also illustrates how to display a property with an enumeration type in a <xref:System.Windows.Forms.DataGridViewComboBoxColumn> so that the combo box drop-down list contains the enumeration values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66ce6-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="66ce6-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="66ce6-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="66ce6-106">Compiling the Code</span></span>  
 <span data-ttu-id="66ce6-107">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="66ce6-107">This example requires:</span></span>  
  
-   <span data-ttu-id="66ce6-108">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="66ce6-108">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="66ce6-109">Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="66ce6-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="66ce6-110">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="66ce6-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="66ce6-111">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="66ce6-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66ce6-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66ce6-112">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="66ce6-113">Exibindo dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="66ce6-113">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="66ce6-114">Como acessar objetos associados às linhas de DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="66ce6-114">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](../../../../docs/framework/winforms/controls/how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
