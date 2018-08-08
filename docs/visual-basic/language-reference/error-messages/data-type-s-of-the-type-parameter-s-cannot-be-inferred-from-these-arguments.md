---
title: Não é possível inferir o(s) tipo(s) de dados do(s) parâmetro(s) de tipo a partir destes argumentos
ms.date: 07/20/2015
f1_keywords:
- bc36644
- bc36647
- vbc36647
- vbc36644
helpviewer_keywords:
- BC36644
- BC36647
ms.assetid: 0e0050f2-2039-4311-b260-f0ebfde84189
ms.openlocfilehash: 6f84df5c9388220e5ca817d95362753df0920534
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586806"
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a><span data-ttu-id="add3b-102">Não é possível inferir o(s) tipo(s) de dados do(s) parâmetro(s) de tipo a partir destes argumentos</span><span class="sxs-lookup"><span data-stu-id="add3b-102">Data type(s) of the type parameter(s) cannot be inferred from these arguments</span></span>
<span data-ttu-id="add3b-103">Tipos de dados dos parâmetros de tipo não podem ser inferidos a partir destes argumentos.</span><span class="sxs-lookup"><span data-stu-id="add3b-103">Data type(s) of the type parameter(s) cannot be inferred from these arguments.</span></span> <span data-ttu-id="add3b-104">Especificando os dados tipos explicitamente talvez corrija esse erro.</span><span class="sxs-lookup"><span data-stu-id="add3b-104">Specifying the data type(s) explicitly might correct this error.</span></span>  
  
 <span data-ttu-id="add3b-105">Esse erro ocorre quando ocorre falha na resolução de sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="add3b-105">This error occurs when overload resolution has failed.</span></span> <span data-ttu-id="add3b-106">Isso ocorre como uma mensagem subordinada que indica por que um candidato a sobrecarga específica foi eliminado.</span><span class="sxs-lookup"><span data-stu-id="add3b-106">It occurs as a subordinate message that states why a particular overload candidate has been eliminated.</span></span> <span data-ttu-id="add3b-107">A mensagem de erro explica que o compilador não pode usar a inferência de tipo para localizar tipos de dados para os parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="add3b-107">The error message explains that the compiler cannot use type inference to find data types for the type parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="add3b-108">Quando especificar argumentos não é uma opção (por exemplo, para operadores de consulta em expressões de consulta), a mensagem de erro aparece sem a segunda frase.</span><span class="sxs-lookup"><span data-stu-id="add3b-108">When specifying arguments is not an option (for example, for query operators in query expressions), the error message appears without the second sentence.</span></span>  
  
 <span data-ttu-id="add3b-109">O código a seguir demonstra o erro.</span><span class="sxs-lookup"><span data-stu-id="add3b-109">The following code demonstrates the error.</span></span>  
  
```vb  
Module Module1  
  
    Sub Main()  
  
        '' Not Valid.  
        'OverloadedGenericMethod("Hello", "World")  
  
    End Sub  
  
    Sub OverloadedGenericMethod(Of T)(ByVal x As String,   
                                      ByVal y As InterfaceExample(Of T))  
    End Sub  
  
    Sub OverloadedGenericMethod(Of T, R)(ByVal x As T,   
                                         ByVal y As InterfaceExample(Of R))  
    End Sub  
  
End Module  
  
Interface InterfaceExample(Of T)  
End Interface  
```  
  
 <span data-ttu-id="add3b-110">**ID do erro:** BC36647 e BC36644</span><span class="sxs-lookup"><span data-stu-id="add3b-110">**Error ID:** BC36647 and BC36644</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="add3b-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="add3b-111">To correct this error</span></span>  
  
-   <span data-ttu-id="add3b-112">Você poderá especificar um tipo de dados para o parâmetro de tipo ou os parâmetros em vez de depender de inferência de tipo.</span><span class="sxs-lookup"><span data-stu-id="add3b-112">You may be able to specify a data type for the type parameter or parameters instead of relying on type inference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="add3b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="add3b-113">See Also</span></span>  
 [<span data-ttu-id="add3b-114">Conversão de Delegado Reduzida</span><span class="sxs-lookup"><span data-stu-id="add3b-114">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [<span data-ttu-id="add3b-115">Procedimentos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="add3b-115">Generic Procedures in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [<span data-ttu-id="add3b-116">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="add3b-116">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
