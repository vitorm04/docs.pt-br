---
title: "A expressão tem o tipo &quot;&lt;typename&gt;&quot; que é um tipo restrito e não pode ser usado para acessar membros herdados de &quot;Object&quot; ou &quot;ValueType&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc31393
- vbc31393
dev_langs:
- VB
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b89f7e83bf596c52296a090563d0dd0403ace548
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a><span data-ttu-id="bfc19-102">A expressão tem o tipo '&lt;typename&gt;' que é um tipo restrito e não pode ser usado para acessar membros herdados de 'Object' ou 'ValueType'</span><span class="sxs-lookup"><span data-stu-id="bfc19-102">Expression has the type &#39;&lt;typename&gt;&#39; which is a restricted type and cannot be used to access members inherited from &#39;Object&#39; or &#39;ValueType&#39;</span></span>
<span data-ttu-id="bfc19-103">Uma expressão avaliada como um tipo que não pode ser convertido pelo common language runtime (CLR), mas acessa um membro que requer conversão.</span><span class="sxs-lookup"><span data-stu-id="bfc19-103">An expression evaluates to a type that cannot be boxed by the common language runtime (CLR) but accesses a member that requires boxing.</span></span>  
  
 <span data-ttu-id="bfc19-104">*Conversão boxing* refere-se ao processamento necessário para converter um tipo para `Object` ou, ocasionalmente, para <xref:System.ValueType>.</xref:System.ValueType></span><span class="sxs-lookup"><span data-stu-id="bfc19-104">*Boxing* refers to the processing necessary to convert a type to `Object` or, on occasion, to <xref:System.ValueType>.</span></span> <span data-ttu-id="bfc19-105">O common language runtime não é possível caixa certos tipos de estrutura, por exemplo <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>e <xref:System.TypedReference>.</xref:System.TypedReference> </xref:System.RuntimeArgumentHandle> </xref:System.ArgIterator></span><span class="sxs-lookup"><span data-stu-id="bfc19-105">The common language runtime cannot box certain structure types, for example <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, and <xref:System.TypedReference>.</span></span>  
  
 <span data-ttu-id="bfc19-106">Essa expressão tenta usar o tipo restrito para chamar um método herdado de <xref:System.Object>ou <xref:System.ValueType>, como <xref:System.Object.GetHashCode%2A>ou <xref:System.Object.ToString%2A>.</xref:System.Object.ToString%2A> </xref:System.Object.GetHashCode%2A> </xref:System.ValueType> </xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="bfc19-106">This expression attempts to use the restricted type to call a method inherited from <xref:System.Object> or <xref:System.ValueType>, such as <xref:System.Object.GetHashCode%2A> or <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="bfc19-107">Para acessar esse método, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tentou uma conversão boxing implícita que causa esse erro.</span><span class="sxs-lookup"><span data-stu-id="bfc19-107">To access this method, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] has attempted an implicit boxing conversion that causes this error.</span></span>  
  
 <span data-ttu-id="bfc19-108">**ID do erro:** BC31393</span><span class="sxs-lookup"><span data-stu-id="bfc19-108">**Error ID:** BC31393</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bfc19-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="bfc19-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="bfc19-110">Localize a expressão que é avaliada como o tipo citado.</span><span class="sxs-lookup"><span data-stu-id="bfc19-110">Locate the expression that evaluates to the cited type.</span></span>  
  
2.  <span data-ttu-id="bfc19-111">Localize a parte da sua declaração que tenta chamar o método herdado por <xref:System.Object>ou <xref:System.ValueType>.</xref:System.ValueType> </xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="bfc19-111">Locate the part of your statement that attempts to call the method inherited from <xref:System.Object> or <xref:System.ValueType>.</span></span>  
  
3.  <span data-ttu-id="bfc19-112">Reescreva a instrução para evitar a chamada do método.</span><span class="sxs-lookup"><span data-stu-id="bfc19-112">Rewrite the statement to avoid the method call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfc19-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bfc19-113">See Also</span></span>  
 [<span data-ttu-id="bfc19-114">Conversões Implícitas e Explícitas</span><span class="sxs-lookup"><span data-stu-id="bfc19-114">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
