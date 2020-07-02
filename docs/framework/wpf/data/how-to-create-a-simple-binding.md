---
title: Como criar uma associação simples
description: Crie uma associação simples para seus aplicativos por meio deste exemplo de instruções no Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 63dc44b442bb4658382bf12faf57b51c8e0698bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618695"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="5522f-103">Como criar uma associação simples</span><span class="sxs-lookup"><span data-stu-id="5522f-103">How to: Create a Simple Binding</span></span>
<span data-ttu-id="5522f-104">Este exemplo mostra como criar um simples <xref:System.Windows.Data.Binding> .</span><span class="sxs-lookup"><span data-stu-id="5522f-104">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5522f-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5522f-105">Example</span></span>  
 <span data-ttu-id="5522f-106">Neste exemplo, você tem um `Person` objeto com uma propriedade de cadeia de caracteres chamada `PersonName` .</span><span class="sxs-lookup"><span data-stu-id="5522f-106">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="5522f-107">O objeto `Person` é definido no namespace chamado `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="5522f-107">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="5522f-108">A linha realçada que contém o `<src>` elemento no exemplo a seguir instancia o `Person` objeto com um `PersonName` valor de propriedade de `Joe` .</span><span class="sxs-lookup"><span data-stu-id="5522f-108">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="5522f-109">Isso é feito na `Resources` seção e atribuído a `x:Key` .</span><span class="sxs-lookup"><span data-stu-id="5522f-109">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="5522f-110">A linha realçada que contém o `<TextBlock>` elemento, em seguida, associa o <xref:System.Windows.Controls.TextBlock> controle à `PersonName` propriedade.</span><span class="sxs-lookup"><span data-stu-id="5522f-110">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="5522f-111">Como resultado, o <xref:System.Windows.Controls.TextBlock> aparece com o valor "Joe".</span><span class="sxs-lookup"><span data-stu-id="5522f-111">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5522f-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5522f-112">See also</span></span>

- [<span data-ttu-id="5522f-113">Visão geral da ligação de dados</span><span class="sxs-lookup"><span data-stu-id="5522f-113">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="5522f-114">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="5522f-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
