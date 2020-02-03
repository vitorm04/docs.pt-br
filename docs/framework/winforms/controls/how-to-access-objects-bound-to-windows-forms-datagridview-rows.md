---
title: acessar objetos vinculados a linhas DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
ms.openlocfilehash: 0b9a4becb78ae817141728467c1e9ea5b693476d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743170"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a><span data-ttu-id="834c9-102">Como acessar objetos associados a linhas DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="834c9-102">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>
<span data-ttu-id="834c9-103">Às vezes, é útil exibir uma tabela de informações armazenadas em uma coleção de objetos de negócios.</span><span class="sxs-lookup"><span data-stu-id="834c9-103">Sometimes it is useful to display a table of information stored in a collection of business objects.</span></span> <span data-ttu-id="834c9-104">Quando você associa um controle de <xref:System.Windows.Forms.DataGridView> a essa coleção, cada propriedade pública é exibida em sua própria coluna, a menos que a propriedade tenha sido marcada como não navegável com um <xref:System.ComponentModel.BrowsableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="834c9-104">When you bind a <xref:System.Windows.Forms.DataGridView> control to such a collection, each public property is displayed in its own column unless the property has been marked non-browsable with a <xref:System.ComponentModel.BrowsableAttribute>.</span></span> <span data-ttu-id="834c9-105">Por exemplo, uma coleção de objetos `Customer` teria colunas como **Nome** e **Endereço**.</span><span class="sxs-lookup"><span data-stu-id="834c9-105">For example, a collection of `Customer` objects would have columns such as **Name** and **Address**.</span></span>  
  
 <span data-ttu-id="834c9-106">Se esses objetos contiverem informações adicionais e o código que você deseja acessar, será possível alcançá-lo por meio de objetos de linha.</span><span class="sxs-lookup"><span data-stu-id="834c9-106">If these objects contain additional information and code that you want to access, you can reach it through row objects.</span></span> <span data-ttu-id="834c9-107">No exemplo de código a seguir, os usuários podem selecionar várias linhas e clicar em um botão para enviar uma fatura para cada um dos clientes correspondentes.</span><span class="sxs-lookup"><span data-stu-id="834c9-107">In the following code example, users can select multiple rows and click a button to send an invoice to each of the corresponding customers.</span></span>  
  
### <a name="to-access-row-bound-objects"></a><span data-ttu-id="834c9-108">Para acessar objetos associados a linhas</span><span class="sxs-lookup"><span data-stu-id="834c9-108">To access row-bound objects</span></span>  
  
- <span data-ttu-id="834c9-109">Use a propriedade <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="834c9-109">Use the <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="834c9-110">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="834c9-110">Example</span></span>  
 <span data-ttu-id="834c9-111">O exemplo de código completo inclui uma implementação simples de `Customer` e associa o <xref:System.Windows.Forms.DataGridView> a um <xref:System.Collections.ArrayList> contendo alguns objetos `Customer`.</span><span class="sxs-lookup"><span data-stu-id="834c9-111">The complete code example includes a simple `Customer` implementation and binds the <xref:System.Windows.Forms.DataGridView> to an <xref:System.Collections.ArrayList> containing a few `Customer` objects.</span></span> <span data-ttu-id="834c9-112">O manipulador de eventos <xref:System.Windows.Forms.Control.Click> da <xref:System.Windows.Forms.Button?displayProperty=nameWithType> deve acessar os objetos `Customer` por meio das linhas, porque a coleção Customer não está acessível fora do manipulador de eventos <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="834c9-112">The <xref:System.Windows.Forms.Control.Click> event handler of the <xref:System.Windows.Forms.Button?displayProperty=nameWithType> must access the `Customer` objects through the rows, because the customer collection is not accessible outside the <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> event handler.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="834c9-113">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="834c9-113">Compiling the Code</span></span>  
 <span data-ttu-id="834c9-114">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="834c9-114">This example requires:</span></span>  
  
- <span data-ttu-id="834c9-115">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="834c9-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="834c9-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="834c9-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>
- [<span data-ttu-id="834c9-117">Exibindo dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="834c9-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="834c9-118">Como associar objetos a controles DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="834c9-118">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)
