---
title: "Acesso à propriedade padrão é ambíguo entre os membros de interface herdada&lt;defaultpropertyname&gt;&quot;da interface&quot;&lt;interfacename1&gt;&quot;e&quot;&lt;defaultpropertyname&gt;&quot;da interface&quot;&lt;interfacename2&gt;&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30686
- bc30686
dev_langs:
- VB
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
caps.latest.revision: 13
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
ms.openlocfilehash: 42e334b2d7ac26785498bb2171912e86d0976623
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename1gt39-and-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename2gt39"></a><span data-ttu-id="2edac-102">Acesso à propriedade padrão é ambíguo entre os membros de interface herdada&lt;defaultpropertyname&gt;'da interface'&lt;interfacename1&gt;'e'&lt;defaultpropertyname&gt;'da interface'&lt;interfacename2&gt;'</span><span class="sxs-lookup"><span data-stu-id="2edac-102">Default property access is ambiguous between the inherited interface members &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename1&gt;&#39; and &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename2&gt;&#39;</span></span>
<span data-ttu-id="2edac-103">Uma interface herda de duas interfaces, cada uma declara uma propriedade padrão com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="2edac-103">An interface inherits from two interfaces, each of which declares a default property with the same name.</span></span> <span data-ttu-id="2edac-104">O compilador não resolve um acesso a sua propriedade padrão sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="2edac-104">The compiler cannot resolve an access to this default property without qualification.</span></span> <span data-ttu-id="2edac-105">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="2edac-105">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="2edac-106">Quando você especificar `testObj(1)`, o compilador tenta resolvê-lo para a propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="2edac-106">When you specify `testObj(1)`, the compiler tries to resolve it to the default property.</span></span> <span data-ttu-id="2edac-107">No entanto, há duas propriedades padrão possível por causa de interfaces herdadas, para que o compilador sinaliza esse erro.</span><span class="sxs-lookup"><span data-stu-id="2edac-107">However, there are two possible default properties because of the inherited interfaces, so the compiler signals this error.</span></span>  
  
 <span data-ttu-id="2edac-108">**ID do erro:** BC30686</span><span class="sxs-lookup"><span data-stu-id="2edac-108">**Error ID:** BC30686</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2edac-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="2edac-109">To correct this error</span></span>  
  
-   <span data-ttu-id="2edac-110">Evite herdar quaisquer membros com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="2edac-110">Avoid inheriting any members with the same name.</span></span> <span data-ttu-id="2edac-111">No exemplo anterior, se `testObj` não precisa de nenhum dos membros de, digamos, `Iface2`, declare-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2edac-111">In the preceding example, if `testObj` does not need any of the members of, say, `Iface2`, then declare it as follows:</span></span>  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     <span data-ttu-id="2edac-112">-ou-</span><span class="sxs-lookup"><span data-stu-id="2edac-112">-or-</span></span>  
  
-   <span data-ttu-id="2edac-113">Implemente a interface herda de uma classe.</span><span class="sxs-lookup"><span data-stu-id="2edac-113">Implement the inheriting interface in a class.</span></span> <span data-ttu-id="2edac-114">Em seguida, você pode implementar cada uma das propriedades herdadas com nomes diferentes.</span><span class="sxs-lookup"><span data-stu-id="2edac-114">Then you can implement each of the inherited properties with different names.</span></span> <span data-ttu-id="2edac-115">No entanto, apenas um deles pode ser a propriedade padrão da classe de implementação.</span><span class="sxs-lookup"><span data-stu-id="2edac-115">However, only one of them can be the default property of the implementing class.</span></span> <span data-ttu-id="2edac-116">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="2edac-116">The following example illustrates this.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2edac-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2edac-117">See Also</span></span>  
 [<span data-ttu-id="2edac-118">Interfaces</span><span class="sxs-lookup"><span data-stu-id="2edac-118">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
