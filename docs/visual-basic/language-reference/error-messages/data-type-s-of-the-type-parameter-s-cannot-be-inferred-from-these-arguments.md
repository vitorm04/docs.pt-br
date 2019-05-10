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
ms.openlocfilehash: 4167905ca6ddab66b2cbc6c8c40dc7c984e94b8b
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913186"
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a><span data-ttu-id="cdf22-102">Não é possível inferir o(s) tipo(s) de dados do(s) parâmetro(s) de tipo a partir destes argumentos</span><span class="sxs-lookup"><span data-stu-id="cdf22-102">Data type(s) of the type parameter(s) cannot be inferred from these arguments</span></span>
<span data-ttu-id="cdf22-103">Tipos de dados dos parâmetros de tipo não podem ser inferidos destes argumentos.</span><span class="sxs-lookup"><span data-stu-id="cdf22-103">Data type(s) of the type parameter(s) cannot be inferred from these arguments.</span></span> <span data-ttu-id="cdf22-104">Especificar os dados de tipo (s) explicitamente talvez corrija esse erro.</span><span class="sxs-lookup"><span data-stu-id="cdf22-104">Specifying the data type(s) explicitly might correct this error.</span></span>  
  
 <span data-ttu-id="cdf22-105">Esse erro ocorre quando ocorre falha na resolução de sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="cdf22-105">This error occurs when overload resolution has failed.</span></span> <span data-ttu-id="cdf22-106">Ele ocorre como uma mensagem subordinada que indica por que um candidato a sobrecarga específica foi eliminado.</span><span class="sxs-lookup"><span data-stu-id="cdf22-106">It occurs as a subordinate message that states why a particular overload candidate has been eliminated.</span></span> <span data-ttu-id="cdf22-107">A mensagem de erro explica que o compilador não pode usar inferência de tipo para localizar os tipos de dados para os parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="cdf22-107">The error message explains that the compiler cannot use type inference to find data types for the type parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cdf22-108">Ao especificar argumentos não é uma opção (por exemplo, para operadores de consulta em expressões de consulta), a mensagem de erro é exibido sem a segunda frase.</span><span class="sxs-lookup"><span data-stu-id="cdf22-108">When specifying arguments is not an option (for example, for query operators in query expressions), the error message appears without the second sentence.</span></span>  
  
 <span data-ttu-id="cdf22-109">O código a seguir demonstra o erro.</span><span class="sxs-lookup"><span data-stu-id="cdf22-109">The following code demonstrates the error.</span></span>  
  
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
  
 <span data-ttu-id="cdf22-110">**ID do erro:** BC36647 e BC36644</span><span class="sxs-lookup"><span data-stu-id="cdf22-110">**Error ID:** BC36647 and BC36644</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cdf22-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="cdf22-111">To correct this error</span></span>  
  
- <span data-ttu-id="cdf22-112">Você poderá especificar um tipo de dados para o parâmetro de tipo ou os parâmetros em vez de depender de inferência de tipo.</span><span class="sxs-lookup"><span data-stu-id="cdf22-112">You may be able to specify a data type for the type parameter or parameters instead of relying on type inference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdf22-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdf22-113">See also</span></span>

- [<span data-ttu-id="cdf22-114">Conversão de Delegado Reduzida</span><span class="sxs-lookup"><span data-stu-id="cdf22-114">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="cdf22-115">Procedimentos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cdf22-115">Generic Procedures in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="cdf22-116">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cdf22-116">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
