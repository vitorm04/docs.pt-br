---
title: A expressão tem o tipo '<typename>', que é um tipo restrito e não pode ser usado para acessar membros herdados de 'Object' ou 'ValueType'
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 6d2edadc323994f7f25394321fb1aff18f7154c5
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824267"
---
# <a name="expression-has-the-type-typename-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-object-or-valuetype"></a><span data-ttu-id="48966-102">Expressão tem o tipo '\<typename >' que é um tipo restrito e não pode ser usado para acessar membros herdados de 'Object' ou 'ValueType'</span><span class="sxs-lookup"><span data-stu-id="48966-102">Expression has the type '\<typename>' which is a restricted type and cannot be used to access members inherited from 'Object' or 'ValueType'</span></span>
<span data-ttu-id="48966-103">Uma expressão é avaliada como um tipo que não pode ser convertido pelo common language runtime (CLR), mas acessa um membro que requer conversão boxing.</span><span class="sxs-lookup"><span data-stu-id="48966-103">An expression evaluates to a type that cannot be boxed by the common language runtime (CLR) but accesses a member that requires boxing.</span></span>  
  
 <span data-ttu-id="48966-104">*Conversão boxing* refere-se ao processamento necessário para converter um tipo para `Object` ou, às vezes, para <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="48966-104">*Boxing* refers to the processing necessary to convert a type to `Object` or, on occasion, to <xref:System.ValueType>.</span></span> <span data-ttu-id="48966-105">O common language runtime não pode encaixotar certos tipos de estrutura, por exemplo <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, e <xref:System.TypedReference>.</span><span class="sxs-lookup"><span data-stu-id="48966-105">The common language runtime cannot box certain structure types, for example <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, and <xref:System.TypedReference>.</span></span>  
  
 <span data-ttu-id="48966-106">Essa expressão tenta usar o tipo restrito para chamar um método herdado de <xref:System.Object> ou <xref:System.ValueType>, como <xref:System.Object.GetHashCode%2A> ou <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="48966-106">This expression attempts to use the restricted type to call a method inherited from <xref:System.Object> or <xref:System.ValueType>, such as <xref:System.Object.GetHashCode%2A> or <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="48966-107">Para acessar esse método, Visual Basic foi tentada uma conversão boxing implícita que causa esse erro.</span><span class="sxs-lookup"><span data-stu-id="48966-107">To access this method, Visual Basic has attempted an implicit boxing conversion that causes this error.</span></span>  
  
 <span data-ttu-id="48966-108">**ID do erro:** BC31393</span><span class="sxs-lookup"><span data-stu-id="48966-108">**Error ID:** BC31393</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="48966-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="48966-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="48966-110">Localize a expressão que é avaliada como o tipo citado.</span><span class="sxs-lookup"><span data-stu-id="48966-110">Locate the expression that evaluates to the cited type.</span></span>  
  
2.  <span data-ttu-id="48966-111">Localize a parte da sua declaração que tenta chamar o método herdado de <xref:System.Object> ou <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="48966-111">Locate the part of your statement that attempts to call the method inherited from <xref:System.Object> or <xref:System.ValueType>.</span></span>  
  
3.  <span data-ttu-id="48966-112">Reescreva a instrução para evitar a chamada de método.</span><span class="sxs-lookup"><span data-stu-id="48966-112">Rewrite the statement to avoid the method call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48966-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48966-113">See also</span></span>

- [<span data-ttu-id="48966-114">Conversões Implícitas e Explícitas</span><span class="sxs-lookup"><span data-stu-id="48966-114">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
