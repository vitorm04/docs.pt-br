---
title: 'Como: Limpar associações'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
ms.openlocfilehash: 8140928d44555e399ddf4ebd73407a251ad3cffe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101413"
---
# <a name="how-to-clear-bindings"></a><span data-ttu-id="5f390-102">Como: Limpar associações</span><span class="sxs-lookup"><span data-stu-id="5f390-102">How to: Clear Bindings</span></span>
<span data-ttu-id="5f390-103">Este exemplo mostra como limpar as associações de um objeto.</span><span class="sxs-lookup"><span data-stu-id="5f390-103">This example shows how to clear bindings from an object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f390-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5f390-104">Example</span></span>  
 <span data-ttu-id="5f390-105">Para limpar uma associação de uma propriedade individual em um objeto, chame <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5f390-105">To clear a binding from an individual property on an object, call <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> as shown in the following example.</span></span> <span data-ttu-id="5f390-106">O exemplo a seguir remove a associação a <xref:System.Windows.Controls.TextBlock.TextProperty> dos *mytext*, um <xref:System.Windows.Controls.TextBlock> objeto.</span><span class="sxs-lookup"><span data-stu-id="5f390-106">The following example removes the binding from the <xref:System.Windows.Controls.TextBlock.TextProperty> of *mytext*, a <xref:System.Windows.Controls.TextBlock> object.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 <span data-ttu-id="5f390-107">Limpar a associação remove a associação para que o valor da propriedade de dependência é alterado para tudo o que teria sido sem a associação.</span><span class="sxs-lookup"><span data-stu-id="5f390-107">Clearing the binding removes the binding so that the value of the dependency property is changed to whatever it would have been without the binding.</span></span> <span data-ttu-id="5f390-108">Esse valor pode ser um valor padrão, um valor herdado ou um valor de uma associação de modelo de dados.</span><span class="sxs-lookup"><span data-stu-id="5f390-108">This value could be a default value, an inherited value, or a value from a data template binding.</span></span>  
  
 <span data-ttu-id="5f390-109">Para limpar as associações de todas as propriedades possíveis em um objeto, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span><span class="sxs-lookup"><span data-stu-id="5f390-109">To clear bindings from all possible properties on an object, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f390-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f390-110">See also</span></span>

- <xref:System.Windows.Data.BindingOperations>
- [<span data-ttu-id="5f390-111">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="5f390-111">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="5f390-112">Tópicos explicativos </span><span class="sxs-lookup"><span data-stu-id="5f390-112">How-to Topics</span></span>](data-binding-how-to-topics.md)
