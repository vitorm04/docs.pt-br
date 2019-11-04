---
title: Como criar uma associação simples
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: faef59ed426059eb2d488d0584d3325c8d46d415
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453503"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="64250-102">Como criar uma associação simples</span><span class="sxs-lookup"><span data-stu-id="64250-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="64250-103">Este exemplo mostra como criar um <xref:System.Windows.Data.Binding>simples.</span><span class="sxs-lookup"><span data-stu-id="64250-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64250-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64250-104">Example</span></span>  
 <span data-ttu-id="64250-105">Neste exemplo, você tem um objeto `Person` com uma propriedade de cadeia de caracteres chamada `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="64250-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="64250-106">O objeto `Person` é definido no namespace chamado `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="64250-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="64250-107">A linha realçada que contém o elemento `<src>` no exemplo a seguir instancia o objeto `Person` com um valor de propriedade `PersonName` de `Joe`.</span><span class="sxs-lookup"><span data-stu-id="64250-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="64250-108">Isso é feito na seção `Resources` e recebe um `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="64250-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="64250-109">A linha realçada que contém o elemento `<TextBlock>` associa o controle <xref:System.Windows.Controls.TextBlock> à propriedade `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="64250-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="64250-110">Como resultado, o <xref:System.Windows.Controls.TextBlock> aparece com o valor "Joe".</span><span class="sxs-lookup"><span data-stu-id="64250-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64250-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64250-111">See also</span></span>

- [<span data-ttu-id="64250-112">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="64250-112">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="64250-113">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="64250-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
