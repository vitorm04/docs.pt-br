---
title: Não é possível aplicar a resolução de sobrecarga com associação tardia a '<procedurename>' porque a instância de acesso é um tipo de interface
ms.date: 07/20/2015
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
ms.openlocfilehash: 7f2ae3bb0e7c09d966c53fb17b1cbe675dfce8b9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814049"
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-procedurename-because-the-accessing-instance-is-an-interface-type"></a><span data-ttu-id="ef9b8-102">Resolução de sobrecarga com associação tardia não pode ser aplicada a '\<procedurename >' porque a instância de acesso é um tipo de interface</span><span class="sxs-lookup"><span data-stu-id="ef9b8-102">Latebound overload resolution cannot be applied to '\<procedurename>' because the accessing instance is an interface type</span></span>
<span data-ttu-id="ef9b8-103">O compilador está tentando resolver uma referência a uma propriedade ou procedimento sobrecarregado, mas a referência falha porque um argumento é do tipo `Object` e o objeto da referência tem o tipo de dados de uma interface.</span><span class="sxs-lookup"><span data-stu-id="ef9b8-103">The compiler is attempting to resolve a reference to an overloaded property or procedure, but the reference fails because an argument is of type `Object` and the referring object has the data type of an interface.</span></span> <span data-ttu-id="ef9b8-104">O `Object` argumento força o compilador a resolver a referência de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="ef9b8-104">The `Object` argument forces the compiler to resolve the reference as late-bound.</span></span>  
  
 <span data-ttu-id="ef9b8-105">Nessas circunstâncias, o compilador resolve a sobrecarga por meio da classe de implementação, em vez de por meio da interface subjacente.</span><span class="sxs-lookup"><span data-stu-id="ef9b8-105">In these circumstances, the compiler resolves the overload through the implementing class instead of through the underlying interface.</span></span> <span data-ttu-id="ef9b8-106">Se a classe renomeia uma das versões sobrecarregadas, o compilador não considera essa versão como uma sobrecarga porque seu nome é diferente.</span><span class="sxs-lookup"><span data-stu-id="ef9b8-106">If the class renames one of the overloaded versions, the compiler does not consider that version to be an overload because its name is different.</span></span> <span data-ttu-id="ef9b8-107">Isso por sua vez faz com que o compilador deverá ignorar a versão renomeada quando ela pode ter sido a escolha correta para resolver a referência.</span><span class="sxs-lookup"><span data-stu-id="ef9b8-107">This in turn causes the compiler to ignore the renamed version when it might have been the correct choice to resolve the reference.</span></span>  
  
 <span data-ttu-id="ef9b8-108">**ID do erro:** BC30933</span><span class="sxs-lookup"><span data-stu-id="ef9b8-108">**Error ID:** BC30933</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ef9b8-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="ef9b8-109">To correct this error</span></span>  
  
-   <span data-ttu-id="ef9b8-110">Use `CType` para lançar um argumento de `Object` para o tipo especificado pela assinatura da sobrecarga que você deseja chamar.</span><span class="sxs-lookup"><span data-stu-id="ef9b8-110">Use `CType` to cast the argument from `Object` to the type specified by the signature of the overload you want to call.</span></span>  
  
     <span data-ttu-id="ef9b8-111">Observe que ele não ajuda a converter o objeto que faz referência a interface subjacente.</span><span class="sxs-lookup"><span data-stu-id="ef9b8-111">Note that it does not help to cast the referring object to the underlying interface.</span></span> <span data-ttu-id="ef9b8-112">Você deve converter o argumento para evitar esse erro.</span><span class="sxs-lookup"><span data-stu-id="ef9b8-112">You must cast the argument to avoid this error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef9b8-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ef9b8-113">Example</span></span>  
 <span data-ttu-id="ef9b8-114">O exemplo a seguir mostra uma chamada para uma sobrecarga `Sub` procedimento que causa esse erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="ef9b8-114">The following example shows a call to an overloaded `Sub` procedure that causes this error at compile time.</span></span>  
  
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
  
 <span data-ttu-id="ef9b8-115">No exemplo anterior, se o compilador permitia a chamada para `s1` conforme foi escrito, a resolução podem ocorrer por meio da classe `c1` em vez da interface `i1`.</span><span class="sxs-lookup"><span data-stu-id="ef9b8-115">In the preceding example, if the compiler allowed the call to `s1` as written, the resolution would take place through the class `c1` instead of the interface `i1`.</span></span> <span data-ttu-id="ef9b8-116">Isso significa que o compilador não consideraria `s2` porque seu nome é diferente `c1`, mesmo que ele seja a escolha correta, conforme definido pelo `i1`.</span><span class="sxs-lookup"><span data-stu-id="ef9b8-116">This would mean that the compiler would not consider `s2` because its name is different in `c1`, even though it is the correct choice as defined by `i1`.</span></span>  
  
 <span data-ttu-id="ef9b8-117">Você pode corrigir o erro alterando a chamada para qualquer uma das seguintes linhas de código:</span><span class="sxs-lookup"><span data-stu-id="ef9b8-117">You can correct the error by changing the call to either of the following lines of code:</span></span>  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 <span data-ttu-id="ef9b8-118">Cada uma das linhas de código converte explicitamente o `Object` variável `o1` para um dos tipos de parâmetro definido para as sobrecargas.</span><span class="sxs-lookup"><span data-stu-id="ef9b8-118">Each of the preceding lines of code explicitly casts the `Object` variable `o1` to one of the parameter types defined for the overloads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef9b8-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef9b8-119">See also</span></span>

- [<span data-ttu-id="ef9b8-120">Sobrecarga de Procedimento</span><span class="sxs-lookup"><span data-stu-id="ef9b8-120">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="ef9b8-121">Resolução de Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="ef9b8-121">Overload Resolution</span></span>](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)
- [<span data-ttu-id="ef9b8-122">Função CType</span><span class="sxs-lookup"><span data-stu-id="ef9b8-122">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
