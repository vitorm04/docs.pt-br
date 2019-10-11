---
title: Não é possível fazer referência a um membro da instância de uma classe de dentro de um método compartilhado ou inicializador de membro compartilhado sem uma instância explícita da classe
ms.date: 07/20/2015
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
ms.openlocfilehash: 9b388685299469d5865d57b698e3a66de912fa84
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250202"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a><span data-ttu-id="dd923-102">Não é possível fazer referência a um membro da instância de uma classe de dentro de um método compartilhado ou inicializador de membro compartilhado sem uma instância explícita da classe</span><span class="sxs-lookup"><span data-stu-id="dd923-102">Cannot refer to an instance member of a class from within a shared method or shared member initializer without an explicit instance of the class</span></span>

<span data-ttu-id="dd923-103">Você tentou fazer referência a um membro não compartilhado de uma classe de dentro de um procedimento compartilhado.</span><span class="sxs-lookup"><span data-stu-id="dd923-103">You have tried to refer to a non-shared member of a class from within a shared procedure.</span></span> <span data-ttu-id="dd923-104">O exemplo a seguir demonstra tal situação:</span><span class="sxs-lookup"><span data-stu-id="dd923-104">The following example demonstrates such a situation:</span></span>
  
```vb  
Class Sample
    Public x as Integer  
    Public Shared Sub SetX()
        x = 10  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="dd923-105">No exemplo anterior, a instrução de atribuição `x = 10` gera essa mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="dd923-105">In the preceding example, the assignment statement `x = 10` generates this error message.</span></span> <span data-ttu-id="dd923-106">Isso ocorre porque um procedimento compartilhado está tentando acessar uma variável de instância.</span><span class="sxs-lookup"><span data-stu-id="dd923-106">This is because a shared procedure is attempting to access an instance variable.</span></span>  
  
 <span data-ttu-id="dd923-107">A variável `x` é um membro de instância porque não está declarada como [compartilhada](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="dd923-107">The variable `x` is an instance member because it is not declared as [Shared](../modifiers/shared.md).</span></span> <span data-ttu-id="dd923-108">Cada instância da classe `Sample` contém sua própria variável individual `x`.</span><span class="sxs-lookup"><span data-stu-id="dd923-108">Each instance of class `Sample` contains its own individual variable `x`.</span></span> <span data-ttu-id="dd923-109">Quando uma instância define ou altera o valor de `x`, ela não afeta o valor de `x` em nenhuma outra instância.</span><span class="sxs-lookup"><span data-stu-id="dd923-109">When one instance sets or changes the value of `x`, it does not affect the value of `x` in any other instance.</span></span>
  
 <span data-ttu-id="dd923-110">No entanto, o procedimento `SetX` é `Shared` entre todas as instâncias da classe `Sample`.</span><span class="sxs-lookup"><span data-stu-id="dd923-110">However, the procedure `SetX` is `Shared` among all instances of class `Sample`.</span></span> <span data-ttu-id="dd923-111">Isso significa que ele não está associado a uma instância da classe, mas opera independentemente de instâncias individuais.</span><span class="sxs-lookup"><span data-stu-id="dd923-111">This means it is not associated with any one instance of the class, but rather operates independently of individual instances.</span></span> <span data-ttu-id="dd923-112">Como não tem conexão com uma instância específica, `setX` não pode acessar uma variável de instância.</span><span class="sxs-lookup"><span data-stu-id="dd923-112">Because it has no connection with a particular instance, `setX` cannot access an instance variable.</span></span> <span data-ttu-id="dd923-113">Ele deve operar somente em variáveis `Shared`.</span><span class="sxs-lookup"><span data-stu-id="dd923-113">It must operate only on `Shared` variables.</span></span> <span data-ttu-id="dd923-114">Quando `SetX` define ou altera o valor de uma variável compartilhada, esse novo valor está disponível para todas as instâncias da classe.</span><span class="sxs-lookup"><span data-stu-id="dd923-114">When `SetX` sets or changes the value of a shared variable, that new value is available to all instances of the class.</span></span>
  
 <span data-ttu-id="dd923-115">**ID do erro:** BC30369</span><span class="sxs-lookup"><span data-stu-id="dd923-115">**Error ID:** BC30369</span></span>
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dd923-116">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="dd923-116">To correct this error</span></span>
  
1. <span data-ttu-id="dd923-117">Decida se deseja que o membro seja compartilhado entre todas as instâncias da classe ou mantido separadamente para cada instância.</span><span class="sxs-lookup"><span data-stu-id="dd923-117">Decide whether you want the member to be shared among all instances of the class, or kept individual for each instance.</span></span>

2. <span data-ttu-id="dd923-118">Se você quiser que uma única cópia do membro seja compartilhada entre todas as instâncias, adicione a palavra-chave `Shared` à declaração de membro.</span><span class="sxs-lookup"><span data-stu-id="dd923-118">If you want a single copy of the member to be shared among all instances, add the `Shared` keyword to the member declaration.</span></span> <span data-ttu-id="dd923-119">Mantenha a palavra-chave `Shared` na declaração de procedimento.</span><span class="sxs-lookup"><span data-stu-id="dd923-119">Retain the `Shared` keyword in the procedure declaration.</span></span>

3. <span data-ttu-id="dd923-120">Se você quiser que cada instância tenha sua própria cópia individual do membro, não especifique `Shared` para a declaração de membro.</span><span class="sxs-lookup"><span data-stu-id="dd923-120">If you want each instance to have its own individual copy of the member, do not specify `Shared` for the member declaration.</span></span> <span data-ttu-id="dd923-121">Remova a palavra-chave `Shared` da declaração de procedimento.</span><span class="sxs-lookup"><span data-stu-id="dd923-121">Remove the `Shared` keyword from the procedure declaration.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="dd923-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd923-122">See also</span></span>

- [<span data-ttu-id="dd923-123">Compartilhado</span><span class="sxs-lookup"><span data-stu-id="dd923-123">Shared</span></span>](../modifiers/shared.md)
