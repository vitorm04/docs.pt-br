---
title: 'Como: Acessar objetos associados às linhas de DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
ms.openlocfilehash: 50882ab9a1a498bf8f76381e3f4aac53876abbb8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217400"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a><span data-ttu-id="15d0d-102">Como: Acessar objetos associados às linhas de DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="15d0d-102">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>
<span data-ttu-id="15d0d-103">Às vezes, é útil exibir uma tabela de informações armazenadas em uma coleção de objetos de negócios.</span><span class="sxs-lookup"><span data-stu-id="15d0d-103">Sometimes it is useful to display a table of information stored in a collection of business objects.</span></span> <span data-ttu-id="15d0d-104">Quando você associa um <xref:System.Windows.Forms.DataGridView> controle a uma coleção assim, cada propriedade pública é exibido em sua própria coluna, a menos que a propriedade foi marcado como não pesquisável com um <xref:System.ComponentModel.BrowsableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="15d0d-104">When you bind a <xref:System.Windows.Forms.DataGridView> control to such a collection, each public property is displayed in its own column unless the property has been marked non-browsable with a <xref:System.ComponentModel.BrowsableAttribute>.</span></span> <span data-ttu-id="15d0d-105">Por exemplo, uma coleção de objetos `Customer` teria colunas como **Nome** e **Endereço**.</span><span class="sxs-lookup"><span data-stu-id="15d0d-105">For example, a collection of `Customer` objects would have columns such as **Name** and **Address**.</span></span>  
  
 <span data-ttu-id="15d0d-106">Se esses objetos contiverem informações adicionais e o código que você deseja acessar, será possível alcançá-lo por meio de objetos de linha.</span><span class="sxs-lookup"><span data-stu-id="15d0d-106">If these objects contain additional information and code that you want to access, you can reach it through row objects.</span></span> <span data-ttu-id="15d0d-107">No exemplo de código a seguir, os usuários podem selecionar várias linhas e clicar em um botão para enviar uma fatura para cada um dos clientes correspondentes.</span><span class="sxs-lookup"><span data-stu-id="15d0d-107">In the following code example, users can select multiple rows and click a button to send an invoice to each of the corresponding customers.</span></span>  
  
### <a name="to-access-row-bound-objects"></a><span data-ttu-id="15d0d-108">Para acessar objetos associados a linhas</span><span class="sxs-lookup"><span data-stu-id="15d0d-108">To access row-bound objects</span></span>  
  
-   <span data-ttu-id="15d0d-109">Use a propriedade <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="15d0d-109">Use the <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="15d0d-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="15d0d-110">Example</span></span>  
 <span data-ttu-id="15d0d-111">O exemplo de código completo inclui um simples `Customer` implementação e associa o <xref:System.Windows.Forms.DataGridView> para um <xref:System.Collections.ArrayList> que contém alguns `Customer` objetos.</span><span class="sxs-lookup"><span data-stu-id="15d0d-111">The complete code example includes a simple `Customer` implementation and binds the <xref:System.Windows.Forms.DataGridView> to an <xref:System.Collections.ArrayList> containing a few `Customer` objects.</span></span> <span data-ttu-id="15d0d-112">O <xref:System.Windows.Forms.Control.Click> manipulador de eventos do <xref:System.Windows.Forms.Button?displayProperty=nameWithType> deve acessar o `Customer` objetos por meio de linhas, porque a coleção do cliente não é acessível de fora a <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="15d0d-112">The <xref:System.Windows.Forms.Control.Click> event handler of the <xref:System.Windows.Forms.Button?displayProperty=nameWithType> must access the `Customer` objects through the rows, because the customer collection is not accessible outside the <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> event handler.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="15d0d-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="15d0d-113">Compiling the Code</span></span>  
 <span data-ttu-id="15d0d-114">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="15d0d-114">This example requires:</span></span>  
  
-   <span data-ttu-id="15d0d-115">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="15d0d-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="15d0d-116">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="15d0d-116">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="15d0d-117">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="15d0d-117">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15d0d-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15d0d-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>
- [<span data-ttu-id="15d0d-119">Exibindo dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="15d0d-119">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="15d0d-120">Como: Associar objetos a controles DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="15d0d-120">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)
