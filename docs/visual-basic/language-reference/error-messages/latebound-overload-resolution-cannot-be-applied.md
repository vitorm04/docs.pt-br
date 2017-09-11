---
title: "Resolução de sobrecarga com associação tardia não pode ser aplicada a &quot;&lt;procedurename&gt;&quot; porque a instância de acesso é um tipo de interface | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30933
- bc30933
dev_langs:
- VB
helpviewer_keywords:
- overload resolution, with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
caps.latest.revision: 11
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
ms.openlocfilehash: f3a72b07b1e0f71613bfd1f703e3a2d6f4cc347e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="latebound-overload-resolution-cannot-be-applied-to-39ltprocedurenamegt39-because-the-accessing-instance-is-an-interface-type"></a><span data-ttu-id="568c6-102">Resolução de sobrecarga com associação tardia não pode ser aplicada a '&lt;procedurename&gt;' porque a instância de acesso é um tipo de interface</span><span class="sxs-lookup"><span data-stu-id="568c6-102">Latebound overload resolution cannot be applied to &#39;&lt;procedurename&gt;&#39; because the accessing instance is an interface type</span></span>
<span data-ttu-id="568c6-103">O compilador está tentando resolver uma referência a uma propriedade ou procedimento sobrecarregado, mas a referência falha porque um argumento é do tipo `Object` e o objeto da referência possui o tipo de dados de uma interface.</span><span class="sxs-lookup"><span data-stu-id="568c6-103">The compiler is attempting to resolve a reference to an overloaded property or procedure, but the reference fails because an argument is of type `Object` and the referring object has the data type of an interface.</span></span> <span data-ttu-id="568c6-104">O `Object` argumento força o compilador a resolver a referência de ligação tardia.</span><span class="sxs-lookup"><span data-stu-id="568c6-104">The `Object` argument forces the compiler to resolve the reference as late-bound.</span></span>  
  
 <span data-ttu-id="568c6-105">Nessas circunstâncias, o compilador resolve o sobrecarregamento através da classe de implementação, em vez de por meio da interface subjacente.</span><span class="sxs-lookup"><span data-stu-id="568c6-105">In these circumstances, the compiler resolves the overload through the implementing class instead of through the underlying interface.</span></span> <span data-ttu-id="568c6-106">Se a classe renomeia uma das versões sobrecarregadas, o compilador não considera que aquela versão seja um sobrecarregamento porque seu nome é diferente.</span><span class="sxs-lookup"><span data-stu-id="568c6-106">If the class renames one of the overloaded versions, the compiler does not consider that version to be an overload because its name is different.</span></span> <span data-ttu-id="568c6-107">Isso por sua vez faz o compilador ignorar a versão renomeada quando ela pode ter sido a escolha correta para resolver a referência.</span><span class="sxs-lookup"><span data-stu-id="568c6-107">This in turn causes the compiler to ignore the renamed version when it might have been the correct choice to resolve the reference.</span></span>  
  
 <span data-ttu-id="568c6-108">**ID do erro:** BC30933</span><span class="sxs-lookup"><span data-stu-id="568c6-108">**Error ID:** BC30933</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="568c6-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="568c6-109">To correct this error</span></span>  
  
-   <span data-ttu-id="568c6-110">Use `CType` para lançar um argumento de `Object` para o tipo especificado pela assinatura do sobrecarregamento que você deseja chamar.</span><span class="sxs-lookup"><span data-stu-id="568c6-110">Use `CType` to cast the argument from `Object` to the type specified by the signature of the overload you want to call.</span></span>  
  
     <span data-ttu-id="568c6-111">Observe que isso não ajuda a converter o objeto que faz referência a interface subjacente.</span><span class="sxs-lookup"><span data-stu-id="568c6-111">Note that it does not help to cast the referring object to the underlying interface.</span></span> <span data-ttu-id="568c6-112">Você deve converter o argumento para evitar esse erro.</span><span class="sxs-lookup"><span data-stu-id="568c6-112">You must cast the argument to avoid this error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="568c6-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="568c6-113">Example</span></span>  
 <span data-ttu-id="568c6-114">O exemplo a seguir mostra uma chamada para um sobrecarregado `Sub` procedimento que causa esse erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="568c6-114">The following example shows a call to an overloaded `Sub` procedure that causes this error at compile time.</span></span>  
  
```  
Module m1  
    Interface i1  
        Sub s1(ByVal p1 As Integer)  
        Sub s1(ByVal p1 As Double)  
    End Interface  
    Class c1  
        Implements i1  
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1  
        End Sub  
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1  
        End Sub  
    End Class  
    Sub Main()  
        Dim refer As i1 = New c1  
        Dim o1 As Object = 3.1415  
        ' The following reference is INVALID and causes a compiler error.  
        refer.s1(o1)   
    End Sub  
End Module  
```  
  
 <span data-ttu-id="568c6-115">No exemplo anterior, se o compilador permitisse a chamada a `s1` como escrito, a resolução teria se realizado através da classe `c1` em vez da interface `i1`.</span><span class="sxs-lookup"><span data-stu-id="568c6-115">In the preceding example, if the compiler allowed the call to `s1` as written, the resolution would take place through the class `c1` instead of the interface `i1`.</span></span> <span data-ttu-id="568c6-116">Isso significa que o compilador não consideraria `s2` porque seu nome é diferente em `c1`, embora seja a escolha correta como definido pelo `i1`.</span><span class="sxs-lookup"><span data-stu-id="568c6-116">This would mean that the compiler would not consider `s2` because its name is different in `c1`, even though it is the correct choice as defined by `i1`.</span></span>  
  
 <span data-ttu-id="568c6-117">Você pode corrigir o erro alterando a chamada para qualquer uma das seguintes linhas de código:</span><span class="sxs-lookup"><span data-stu-id="568c6-117">You can correct the error by changing the call to either of the following lines of code:</span></span>  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 <span data-ttu-id="568c6-118">Cada uma das linhas de código explicitamente converte o `Object` variável `o1` para um dos tipos de parâmetro definido para as sobrecargas.</span><span class="sxs-lookup"><span data-stu-id="568c6-118">Each of the preceding lines of code explicitly casts the `Object` variable `o1` to one of the parameter types defined for the overloads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="568c6-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="568c6-119">See Also</span></span>  
 <span data-ttu-id="568c6-120">[Sobrecarga de procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="568c6-120">[Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md) </span></span>  
<span data-ttu-id="568c6-121"> [Resolução de sobrecarga](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="568c6-121"> [Overload Resolution](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md) </span></span>  
<span data-ttu-id="568c6-122"> [Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)</span><span class="sxs-lookup"><span data-stu-id="568c6-122"> [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md)</span></span>
