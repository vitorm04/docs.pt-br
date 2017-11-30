---
title: "Não é possível fazer referência a um membro da instância de uma classe de dentro de um método compartilhado ou inicializador de membro compartilhado sem uma instância explícita da classe"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6a15d36c0b3a4d6b1657d583de0dc61621da960d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a><span data-ttu-id="feda1-102">Não é possível fazer referência a um membro da instância de uma classe de dentro de um método compartilhado ou inicializador de membro compartilhado sem uma instância explícita da classe</span><span class="sxs-lookup"><span data-stu-id="feda1-102">Cannot refer to an instance member of a class from within a shared method or shared member initializer without an explicit instance of the class</span></span>
<span data-ttu-id="feda1-103">Você tentou fazer referência a um membro não compartilhado de uma classe de dentro de um procedimento compartilhado.</span><span class="sxs-lookup"><span data-stu-id="feda1-103">You have tried to refer to a non-shared member of a class from within a shared procedure.</span></span> <span data-ttu-id="feda1-104">O exemplo a seguir demonstra essa situação.</span><span class="sxs-lookup"><span data-stu-id="feda1-104">The following example demonstrates such a situation.</span></span>  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="feda1-105">No exemplo anterior, a instrução de atribuição `x = 10` gera essa mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="feda1-105">In the preceding example, the assignment statement `x = 10` generates this error message.</span></span> <span data-ttu-id="feda1-106">Isso ocorre porque um procedimento compartilhado está tentando acessar uma variável de instância.</span><span class="sxs-lookup"><span data-stu-id="feda1-106">This is because a shared procedure is attempting to access an instance variable.</span></span>  
  
 <span data-ttu-id="feda1-107">A variável `x` é um membro de instância porque ele não está declarado como [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="feda1-107">The variable `x` is an instance member because it is not declared as [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="feda1-108">Cada instância da classe `sample` contém sua própria variável individual `x`.</span><span class="sxs-lookup"><span data-stu-id="feda1-108">Each instance of class `sample` contains its own individual variable `x`.</span></span> <span data-ttu-id="feda1-109">Quando uma instância define ou altera o valor de `x`, ele não afeta o valor de `x` em qualquer outra instância.</span><span class="sxs-lookup"><span data-stu-id="feda1-109">When one instance sets or changes the value of `x`, it does not affect the value of `x` in any other instance.</span></span>  
  
 <span data-ttu-id="feda1-110">No entanto, o procedimento `setX` é `Shared` entre todas as instâncias da classe `sample`.</span><span class="sxs-lookup"><span data-stu-id="feda1-110">However, the procedure `setX` is `Shared` among all instances of class `sample`.</span></span> <span data-ttu-id="feda1-111">Isso significa que ele não está associado a qualquer instância da classe, mas em vez disso, opera independentemente das instâncias individuais.</span><span class="sxs-lookup"><span data-stu-id="feda1-111">This means it is not associated with any one instance of the class, but rather operates independently of individual instances.</span></span> <span data-ttu-id="feda1-112">Porque ele tem nenhuma conexão com uma determinada instância, `setX` não é possível acessar uma variável de instância.</span><span class="sxs-lookup"><span data-stu-id="feda1-112">Because it has no connection with a particular instance, `setX` cannot access an instance variable.</span></span> <span data-ttu-id="feda1-113">Ele deve operar somente em `Shared` variáveis.</span><span class="sxs-lookup"><span data-stu-id="feda1-113">It must operate only on `Shared` variables.</span></span> <span data-ttu-id="feda1-114">Quando `setX` define ou altera o valor de uma variável compartilhada, que o novo valor está disponível para todas as instâncias da classe.</span><span class="sxs-lookup"><span data-stu-id="feda1-114">When `setX` sets or changes the value of a shared variable, that new value is available to all instances of the class.</span></span>  
  
 <span data-ttu-id="feda1-115">**ID do erro:** BC30369</span><span class="sxs-lookup"><span data-stu-id="feda1-115">**Error ID:** BC30369</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="feda1-116">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="feda1-116">To correct this error</span></span>  
  
1.  <span data-ttu-id="feda1-117">Decida se deseja que o membro a ser compartilhado entre todas as instâncias da classe, ou mantido individual para cada instância.</span><span class="sxs-lookup"><span data-stu-id="feda1-117">Decide whether you want the member to be shared among all instances of the class, or kept individual for each instance.</span></span>  
  
2.  <span data-ttu-id="feda1-118">Se desejar que uma única cópia do membro a ser compartilhado entre todas as instâncias, adicione a `Shared` palavra-chave para a declaração de membro.</span><span class="sxs-lookup"><span data-stu-id="feda1-118">If you want a single copy of the member to be shared among all instances, add the `Shared` keyword to the member declaration.</span></span> <span data-ttu-id="feda1-119">Manter o `Shared` palavra-chave na declaração do procedimento.</span><span class="sxs-lookup"><span data-stu-id="feda1-119">Retain the `Shared` keyword in the procedure declaration.</span></span>  
  
3.  <span data-ttu-id="feda1-120">Se você quiser que cada instância tenha sua própria cópia individual do membro, não especifique `Shared` na declaração de membro.</span><span class="sxs-lookup"><span data-stu-id="feda1-120">If you want each instance to have its own individual copy of the member, do not specify `Shared` for the member declaration.</span></span> <span data-ttu-id="feda1-121">Remover o `Shared` palavra-chave da declaração de procedimento.</span><span class="sxs-lookup"><span data-stu-id="feda1-121">Remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feda1-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="feda1-122">See Also</span></span>  
 [<span data-ttu-id="feda1-123">Compartilhado</span><span class="sxs-lookup"><span data-stu-id="feda1-123">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
