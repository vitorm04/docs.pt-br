---
title: '&#39;&lt;TypeName&gt; &#39; é um tipo delegado'
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: c6d4244ce72dedee50b65ba19978149ce86b9e87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595642"
---
# <a name="39lttypenamegt39-is-a-delegate-type"></a><span data-ttu-id="1c35b-102">&#39;&lt;TypeName&gt; &#39; é um tipo delegado</span><span class="sxs-lookup"><span data-stu-id="1c35b-102">&#39;&lt;typename&gt;&#39; is a delegate type</span></span>
<span data-ttu-id="1c35b-103">'\<typename >' é um tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="1c35b-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="1c35b-104">A construção Delegate permite somente uma única expressão AddressOf como uma lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="1c35b-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="1c35b-105">Geralmente, uma expressão AddressOf pode ser usada em vez de uma construção de delegado.</span><span class="sxs-lookup"><span data-stu-id="1c35b-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="1c35b-106">Um `New` cláusula criando uma instância da classe delegada fornece uma lista de argumento inválido para construtor delegado.</span><span class="sxs-lookup"><span data-stu-id="1c35b-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="1c35b-107">Você pode fornecer um único `AddressOf` expressão ao criar uma nova instância de delegado.</span><span class="sxs-lookup"><span data-stu-id="1c35b-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="1c35b-108">Esse erro pode ocorrer se você não passar argumentos para construtor delegate, se você passar a mais de um argumento, ou se você passar um argumento único que não é válido `AddressOf` expressão.</span><span class="sxs-lookup"><span data-stu-id="1c35b-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="1c35b-109">**ID do erro:** BC32008</span><span class="sxs-lookup"><span data-stu-id="1c35b-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1c35b-110">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="1c35b-110">To correct this error</span></span>  
  
-   <span data-ttu-id="1c35b-111">Usar um único `AddressOf` expressão na lista de argumentos para a classe delegate no `New` cláusula.</span><span class="sxs-lookup"><span data-stu-id="1c35b-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c35b-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c35b-112">See Also</span></span>  
 [<span data-ttu-id="1c35b-113">Operador New</span><span class="sxs-lookup"><span data-stu-id="1c35b-113">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)  
 [<span data-ttu-id="1c35b-114">Operador AddressOf</span><span class="sxs-lookup"><span data-stu-id="1c35b-114">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="1c35b-115">Delegados</span><span class="sxs-lookup"><span data-stu-id="1c35b-115">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="1c35b-116">Como invocar um método delegado</span><span class="sxs-lookup"><span data-stu-id="1c35b-116">How to: Invoke a Delegate Method</span></span>](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
