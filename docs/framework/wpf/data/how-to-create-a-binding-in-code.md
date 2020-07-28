---
title: Como criar uma associação em código
description: Saiba como criar uma associação no código em um aplicativo Windows Presentation Foundation chamando o método SetBinding diretamente.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: aa2a29f4c1262d8ac54641b856c297b284b23a38
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165804"
---
# <a name="how-to-create-a-binding-in-code"></a><span data-ttu-id="2e7ad-103">Como criar uma associação em código</span><span class="sxs-lookup"><span data-stu-id="2e7ad-103">How to: Create a Binding in Code</span></span>
<span data-ttu-id="2e7ad-104">Este exemplo mostra como criar e definir um <xref:System.Windows.Data.Binding> no código.</span><span class="sxs-lookup"><span data-stu-id="2e7ad-104">This example shows how to create and set a <xref:System.Windows.Data.Binding> in code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e7ad-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2e7ad-105">Example</span></span>  
 <span data-ttu-id="2e7ad-106">A <xref:System.Windows.FrameworkElement> classe e a <xref:System.Windows.FrameworkContentElement> classe expõem um `SetBinding` método.</span><span class="sxs-lookup"><span data-stu-id="2e7ad-106">The <xref:System.Windows.FrameworkElement> class and the <xref:System.Windows.FrameworkContentElement> class both expose a `SetBinding` method.</span></span> <span data-ttu-id="2e7ad-107">Se você estiver ligando um elemento que herde qualquer uma dessas classes, você pode chamar o <xref:System.Windows.FrameworkElement.SetBinding%2A> método diretamente.</span><span class="sxs-lookup"><span data-stu-id="2e7ad-107">If you are binding an element that inherits either of these classes, you can call the <xref:System.Windows.FrameworkElement.SetBinding%2A> method directly.</span></span>  
  
 <span data-ttu-id="2e7ad-108">O exemplo a seguir cria uma classe chamada `MyData`, que contém uma propriedade chamada `MyDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="2e7ad-108">The following example creates a class named, `MyData`, which contains a property named `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 <span data-ttu-id="2e7ad-109">O exemplo a seguir mostra como criar um objeto de associação para definir a origem da associação.</span><span class="sxs-lookup"><span data-stu-id="2e7ad-109">The following example shows how to create a binding object to set the source of the binding.</span></span>  <span data-ttu-id="2e7ad-110">O exemplo usa <xref:System.Windows.FrameworkElement.SetBinding%2A> para associar a <xref:System.Windows.Controls.TextBlock.Text%2A> propriedade de `myText` , que é um <xref:System.Windows.Controls.TextBlock> controle, ao `MyDataProperty` .</span><span class="sxs-lookup"><span data-stu-id="2e7ad-110">The example uses <xref:System.Windows.FrameworkElement.SetBinding%2A> to bind the <xref:System.Windows.Controls.TextBlock.Text%2A> property of `myText`, which is a <xref:System.Windows.Controls.TextBlock> control, to `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 <span data-ttu-id="2e7ad-111">Para ver o exemplo de código completo, confira [Exemplo de associação somente de código](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="2e7ad-111">For the complete code sample, see [Code-only Binding Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span></span>  
  
 <span data-ttu-id="2e7ad-112">Em vez de chamar <xref:System.Windows.FrameworkElement.SetBinding%2A> , você pode usar o <xref:System.Windows.Data.BindingOperations.SetBinding%2A> método estático da <xref:System.Windows.Data.BindingOperations> classe.</span><span class="sxs-lookup"><span data-stu-id="2e7ad-112">Instead of calling <xref:System.Windows.FrameworkElement.SetBinding%2A>, you can use the <xref:System.Windows.Data.BindingOperations.SetBinding%2A> static method of the <xref:System.Windows.Data.BindingOperations> class.</span></span> <span data-ttu-id="2e7ad-113">O exemplo a seguir chama <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> em vez de <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> associar `myText` a `myDataProperty` .</span><span class="sxs-lookup"><span data-stu-id="2e7ad-113">The following example, calls <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> instead of <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> to bind `myText` to `myDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a><span data-ttu-id="2e7ad-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="2e7ad-114">See also</span></span>

- [<span data-ttu-id="2e7ad-115">Visão geral da ligação de dados</span><span class="sxs-lookup"><span data-stu-id="2e7ad-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="2e7ad-116">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="2e7ad-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
