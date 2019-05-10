---
title: "'<typename>' é um tipo delegado"
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 45dc0403468fa40888a6c5e6bdfe6ca782e98325
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664181"
---
# <a name="typename-is-a-delegate-type"></a><span data-ttu-id="49346-102">'\<typename >' é um tipo delegado</span><span class="sxs-lookup"><span data-stu-id="49346-102">'\<typename>' is a delegate type</span></span>
<span data-ttu-id="49346-103">'\<typename >' é um tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="49346-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="49346-104">A construção Delegate permite apenas uma única expressão AddressOf como uma lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="49346-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="49346-105">Geralmente, uma expressão de AddressOf pode ser usada em vez de uma construção de delegado.</span><span class="sxs-lookup"><span data-stu-id="49346-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="49346-106">Um `New` cláusula criando uma instância de uma classe de representante fornece uma lista de argumentos inválida para o construtor do delegado.</span><span class="sxs-lookup"><span data-stu-id="49346-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="49346-107">Você pode fornecer um único `AddressOf` expressão durante a criação de uma nova instância de delegado.</span><span class="sxs-lookup"><span data-stu-id="49346-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="49346-108">Esse erro pode resultar se você não passar argumentos para o construtor delegado, se você passar mais de um argumento ou se você passar um argumento único que não é válido `AddressOf` expressão.</span><span class="sxs-lookup"><span data-stu-id="49346-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="49346-109">**ID do erro:** BC32008</span><span class="sxs-lookup"><span data-stu-id="49346-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="49346-110">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="49346-110">To correct this error</span></span>  
  
- <span data-ttu-id="49346-111">Usar uma única `AddressOf` expressão na lista de argumentos para a classe de delegado no `New` cláusula.</span><span class="sxs-lookup"><span data-stu-id="49346-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49346-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49346-112">See also</span></span>

- [<span data-ttu-id="49346-113">Operador New</span><span class="sxs-lookup"><span data-stu-id="49346-113">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="49346-114">Operador AddressOf</span><span class="sxs-lookup"><span data-stu-id="49346-114">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="49346-115">Delegados</span><span class="sxs-lookup"><span data-stu-id="49346-115">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="49346-116">Como: Invocar um método delegado</span><span class="sxs-lookup"><span data-stu-id="49346-116">How to: Invoke a Delegate Method</span></span>](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
