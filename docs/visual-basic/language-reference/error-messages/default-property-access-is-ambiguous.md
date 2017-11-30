---
title: "Acesso à propriedade padrão é ambíguo entre os membros de interface herdada &#39; &lt;defaultpropertyname&gt;&#39; de interface &#39;&lt; interfacename1&gt;&#39; e &#39;&lt; defaultpropertyname&gt;&#39; de interface &#39;&lt; interfacename2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords: BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 23d613668ee2d92484117759dd614ed2cad4bcb2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename1gt39-and-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename2gt39"></a><span data-ttu-id="60c4d-102">Acesso à propriedade padrão é ambíguo entre os membros de interface herdada &#39; &lt;defaultpropertyname&gt;&#39; de interface &#39;&lt; interfacename1&gt;&#39; e &#39;&lt; defaultpropertyname&gt;&#39; de interface &#39;&lt; interfacename2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="60c4d-102">Default property access is ambiguous between the inherited interface members &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename1&gt;&#39; and &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename2&gt;&#39;</span></span>
<span data-ttu-id="60c4d-103">Uma interface herda de duas interfaces, cada uma delas declara uma propriedade padrão com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="60c4d-103">An interface inherits from two interfaces, each of which declares a default property with the same name.</span></span> <span data-ttu-id="60c4d-104">O compilador não é possível resolver um acesso de propriedade padrão sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="60c4d-104">The compiler cannot resolve an access to this default property without qualification.</span></span> <span data-ttu-id="60c4d-105">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="60c4d-105">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="60c4d-106">Quando você especificar `testObj(1)`, o compilador tenta resolvê-lo para a propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="60c4d-106">When you specify `testObj(1)`, the compiler tries to resolve it to the default property.</span></span> <span data-ttu-id="60c4d-107">No entanto, há duas propriedades padrão possíveis devido a interfaces herdadas, para que o compilador sinaliza este erro.</span><span class="sxs-lookup"><span data-stu-id="60c4d-107">However, there are two possible default properties because of the inherited interfaces, so the compiler signals this error.</span></span>  
  
 <span data-ttu-id="60c4d-108">**ID do erro:** BC30686</span><span class="sxs-lookup"><span data-stu-id="60c4d-108">**Error ID:** BC30686</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="60c4d-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="60c4d-109">To correct this error</span></span>  
  
-   <span data-ttu-id="60c4d-110">Evite herdar quaisquer membros com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="60c4d-110">Avoid inheriting any members with the same name.</span></span> <span data-ttu-id="60c4d-111">No exemplo anterior, se `testObj` não precisa de nenhum dos membros de, digamos, `Iface2`, declare-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="60c4d-111">In the preceding example, if `testObj` does not need any of the members of, say, `Iface2`, then declare it as follows:</span></span>  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     <span data-ttu-id="60c4d-112">-ou-</span><span class="sxs-lookup"><span data-stu-id="60c4d-112">-or-</span></span>  
  
-   <span data-ttu-id="60c4d-113">Implemente a interface que herda de uma classe.</span><span class="sxs-lookup"><span data-stu-id="60c4d-113">Implement the inheriting interface in a class.</span></span> <span data-ttu-id="60c4d-114">Em seguida, você pode implementar cada uma das propriedades herdadas com nomes diferentes.</span><span class="sxs-lookup"><span data-stu-id="60c4d-114">Then you can implement each of the inherited properties with different names.</span></span> <span data-ttu-id="60c4d-115">No entanto, apenas um deles pode ser a propriedade padrão da classe de implementação.</span><span class="sxs-lookup"><span data-stu-id="60c4d-115">However, only one of them can be the default property of the implementing class.</span></span> <span data-ttu-id="60c4d-116">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="60c4d-116">The following example illustrates this.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="60c4d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60c4d-117">See Also</span></span>  
 [<span data-ttu-id="60c4d-118">Interfaces</span><span class="sxs-lookup"><span data-stu-id="60c4d-118">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
