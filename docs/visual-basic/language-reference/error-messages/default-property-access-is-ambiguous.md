---
title: O acesso à propriedade padrão é ambíguo entre os membros de interface herdada '<defaultpropertyname>' da interface '<interfacename1>' e '<defaultpropertyname>' da interface '<interfacename2>'
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: 5f058c8e7d480b9145452ae85f186a6ac2ed0d56
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836344"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a><span data-ttu-id="cb598-102">Acesso à propriedade padrão é ambíguo entre os membros da interface herdada\<defaultpropertyname >' da interface '\<interfacename1 >' e '\<defaultpropertyname >' da interface '\< interfacename2 >'</span><span class="sxs-lookup"><span data-stu-id="cb598-102">Default property access is ambiguous between the inherited interface members '\<defaultpropertyname>' of interface '\<interfacename1>' and '\<defaultpropertyname>' of interface '\<interfacename2>'</span></span>
<span data-ttu-id="cb598-103">Uma interface herda de duas interfaces, cada uma das quais declara uma propriedade padrão com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="cb598-103">An interface inherits from two interfaces, each of which declares a default property with the same name.</span></span> <span data-ttu-id="cb598-104">O compilador não pode resolver um acesso a essa propriedade padrão sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="cb598-104">The compiler cannot resolve an access to this default property without qualification.</span></span> <span data-ttu-id="cb598-105">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="cb598-105">The following example illustrates this.</span></span>  
  
```  
Public Interface Iface1  
    Default Property prop(ByVal arg As Integer) As Integer  
End Interface  
Public Interface Iface2  
    Default Property prop(ByVal arg As Integer) As Integer  
End Interface  
Public Interface Iface3  
    Inherits Iface1, Iface2  
End Interface  
Public Class testClass  
    Public Sub accessDefaultProperty()  
        Dim testObj As Iface3  
        Dim testInt As Integer = testObj(1)  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="cb598-106">Quando você especifica `testObj(1)`, o compilador tentar resolvê-lo para a propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="cb598-106">When you specify `testObj(1)`, the compiler tries to resolve it to the default property.</span></span> <span data-ttu-id="cb598-107">No entanto, há duas propriedades padrão possível por causa de interfaces herdadas, portanto, o compilador sinaliza esse erro.</span><span class="sxs-lookup"><span data-stu-id="cb598-107">However, there are two possible default properties because of the inherited interfaces, so the compiler signals this error.</span></span>  
  
 <span data-ttu-id="cb598-108">**ID do erro:** BC30686</span><span class="sxs-lookup"><span data-stu-id="cb598-108">**Error ID:** BC30686</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cb598-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="cb598-109">To correct this error</span></span>  
  
-   <span data-ttu-id="cb598-110">Evite herdar todos os membros com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="cb598-110">Avoid inheriting any members with the same name.</span></span> <span data-ttu-id="cb598-111">No exemplo anterior, se `testObj` não precisa de nenhum dos membros de, digamos, `Iface2`, declare-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cb598-111">In the preceding example, if `testObj` does not need any of the members of, say, `Iface2`, then declare it as follows:</span></span>  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     <span data-ttu-id="cb598-112">- ou -</span><span class="sxs-lookup"><span data-stu-id="cb598-112">-or-</span></span>  
  
-   <span data-ttu-id="cb598-113">Implemente a interface de herança em uma classe.</span><span class="sxs-lookup"><span data-stu-id="cb598-113">Implement the inheriting interface in a class.</span></span> <span data-ttu-id="cb598-114">Em seguida, você pode implementar cada uma das propriedades herdadas com nomes diferentes.</span><span class="sxs-lookup"><span data-stu-id="cb598-114">Then you can implement each of the inherited properties with different names.</span></span> <span data-ttu-id="cb598-115">No entanto, apenas um deles pode ser a propriedade padrão da classe de implementação.</span><span class="sxs-lookup"><span data-stu-id="cb598-115">However, only one of them can be the default property of the implementing class.</span></span> <span data-ttu-id="cb598-116">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="cb598-116">The following example illustrates this.</span></span>  
  
    ```  
    Public Class useIface3  
        Implements Iface3  
        Default Public Property prop1(ByVal arg As Integer) As Integer Implements Iface1.prop  
            ' Insert code to define Get and Set procedures for prop1.  
        End Property  
        Public Property prop2(ByVal arg As Integer) As Integer Implements Iface2.prop  
            ' Insert code to define Get and Set procedures for prop2.  
        End Property  
    End Class  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cb598-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb598-117">See also</span></span>

- [<span data-ttu-id="cb598-118">Interfaces</span><span class="sxs-lookup"><span data-stu-id="cb598-118">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
