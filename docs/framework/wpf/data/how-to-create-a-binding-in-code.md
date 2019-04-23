---
title: 'Como: Criar uma associação no código'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: 57ec845c5c9a5bddb801428b9ecde035a97cf447
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089257"
---
# <a name="how-to-create-a-binding-in-code"></a><span data-ttu-id="a9aa0-102">Como: Criar uma associação no código</span><span class="sxs-lookup"><span data-stu-id="a9aa0-102">How to: Create a Binding in Code</span></span>
<span data-ttu-id="a9aa0-103">Este exemplo mostra como criar e definir um <xref:System.Windows.Data.Binding> no código.</span><span class="sxs-lookup"><span data-stu-id="a9aa0-103">This example shows how to create and set a <xref:System.Windows.Data.Binding> in code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9aa0-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a9aa0-104">Example</span></span>  
 <span data-ttu-id="a9aa0-105">O <xref:System.Windows.FrameworkElement> classe e o <xref:System.Windows.FrameworkContentElement> expõem um `SetBinding` método.</span><span class="sxs-lookup"><span data-stu-id="a9aa0-105">The <xref:System.Windows.FrameworkElement> class and the <xref:System.Windows.FrameworkContentElement> class both expose a `SetBinding` method.</span></span> <span data-ttu-id="a9aa0-106">Se você estiver associando um elemento que herda de qualquer uma dessas classes, você pode chamar o <xref:System.Windows.FrameworkElement.SetBinding%2A> método diretamente.</span><span class="sxs-lookup"><span data-stu-id="a9aa0-106">If you are binding an element that inherits either of these classes, you can call the <xref:System.Windows.FrameworkElement.SetBinding%2A> method directly.</span></span>  
  
 <span data-ttu-id="a9aa0-107">O exemplo a seguir cria uma classe chamada `MyData`, que contém uma propriedade chamada `MyDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="a9aa0-107">The following example creates a class named, `MyData`, which contains a property named `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 <span data-ttu-id="a9aa0-108">O exemplo a seguir mostra como criar um objeto de associação para definir a origem da associação.</span><span class="sxs-lookup"><span data-stu-id="a9aa0-108">The following example shows how to create a binding object to set the source of the binding.</span></span>  <span data-ttu-id="a9aa0-109">O exemplo usa <xref:System.Windows.FrameworkElement.SetBinding%2A> para associar o <xref:System.Windows.Controls.TextBlock.Text%2A> propriedade de `myText`, que é uma <xref:System.Windows.Controls.TextBlock> controlam a, `MyDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="a9aa0-109">The example uses <xref:System.Windows.FrameworkElement.SetBinding%2A> to bind the <xref:System.Windows.Controls.TextBlock.Text%2A> property of `myText`, which is a <xref:System.Windows.Controls.TextBlock> control, to `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 <span data-ttu-id="a9aa0-110">Para ver o exemplo de código completo, confira [Exemplo de associação somente de código](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="a9aa0-110">For the complete code sample, see [Code-only Binding Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span></span>  
  
 <span data-ttu-id="a9aa0-111">Em vez de chamar <xref:System.Windows.FrameworkElement.SetBinding%2A>, você pode usar o <xref:System.Windows.Data.BindingOperations.SetBinding%2A> método estático do <xref:System.Windows.Data.BindingOperations> classe.</span><span class="sxs-lookup"><span data-stu-id="a9aa0-111">Instead of calling <xref:System.Windows.FrameworkElement.SetBinding%2A>, you can use the <xref:System.Windows.Data.BindingOperations.SetBinding%2A> static method of the <xref:System.Windows.Data.BindingOperations> class.</span></span> <span data-ttu-id="a9aa0-112">O exemplo a seguir, chamadas <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> em vez de <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> para associar `myText` para `myDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="a9aa0-112">The following example, calls <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> instead of <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> to bind `myText` to `myDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a><span data-ttu-id="a9aa0-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9aa0-113">See also</span></span>

- [<span data-ttu-id="a9aa0-114">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="a9aa0-114">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="a9aa0-115">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="a9aa0-115">How-to Topics</span></span>](data-binding-how-to-topics.md)
