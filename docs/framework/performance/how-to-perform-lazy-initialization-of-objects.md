---
title: "Como executar a inicialização lenta de objetos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: lazy initialization in .NET, how to perform
ms.assetid: 8cd68620-dcc3-4f20-8835-c728a6820e71
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b616aa284b6f7fff01b3b1fbfb15f2ceb54c9663
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-perform-lazy-initialization-of-objects"></a><span data-ttu-id="5b304-102">Como executar a inicialização lenta de objetos</span><span class="sxs-lookup"><span data-stu-id="5b304-102">How to: Perform Lazy Initialization of Objects</span></span>
<span data-ttu-id="5b304-103">A classe <xref:System.Lazy%601?displayProperty=nameWithType> simplifica o trabalho de inicialização lenta e instanciação de objetos.</span><span class="sxs-lookup"><span data-stu-id="5b304-103">The <xref:System.Lazy%601?displayProperty=nameWithType> class simplifies the work of performing lazy initialization and instantiation of objects.</span></span> <span data-ttu-id="5b304-104">Inicializando objetos de maneira lenta, você poderá evitar a necessidade de criá-los se eles nunca forem necessários ou você poderá adiar sua inicialização até que eles sejam acessados pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="5b304-104">By initializing objects in a lazy manner, you can avoid having to create them at all if they are never needed, or you can postpone their initialization until they are first accessed.</span></span> <span data-ttu-id="5b304-105">Para obter mais informações, veja [Inicialização lenta](../../../docs/framework/performance/lazy-initialization.md).</span><span class="sxs-lookup"><span data-stu-id="5b304-105">For more information, see [Lazy Initialization](../../../docs/framework/performance/lazy-initialization.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b304-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5b304-106">Example</span></span>  
 <span data-ttu-id="5b304-107">O exemplo a seguir mostra como inicializar um valor com <xref:System.Lazy%601>.</span><span class="sxs-lookup"><span data-stu-id="5b304-107">The following example shows how to initialize a value with <xref:System.Lazy%601>.</span></span> <span data-ttu-id="5b304-108">Suponha que a variável lenta talvez não seja necessária, dependendo de algum outro código que define a variável `someCondition` como true ou false.</span><span class="sxs-lookup"><span data-stu-id="5b304-108">Assume that the lazy variable might not be needed, depending on some other code that sets the `someCondition` variable to true or false.</span></span>  
  
```vb  
Dim someCondition As Boolean = False  
  
Sub Main()  
    'Initializing a value with a big computation, computed in parallel  
    Dim _data As Lazy(Of Integer) = New Lazy(Of Integer)(Function()  
                                                             Dim result =  
                                                                 ParallelEnumerable.Range(0, 1000).  
                                                                 Aggregate(Function(x, y)  
                                                                               Return x + y  
                                                                           End Function)  
                                                             Return result  
                                                         End Function)  
  
    '  do work that may or may not set someCondition to True  
    ' ...  
    '  Initialize the data only if needed  
    If someCondition = True Then  
  
        If (_data.Value > 100) Then  
  
            Console.WriteLine("Good data")  
        End If  
    End If  
End Sub  
```  
  
```csharp  
  static bool someCondition = false;    
  //Initializing a value with a big computation, computed in parallel  
  Lazy<int> _data = new Lazy<int>(delegate  
  {  
      return ParallelEnumerable.Range(0, 1000).  
          Select(i => Compute(i)).Aggregate((x,y) => x + y);  
  }, LazyExecutionMode.EnsureSingleThreadSafeExecution);  
  
  // Do some work that may or may not set someCondition to true.  
  //  ...  
  // Initialize the data only if necessary  
  if (someCondition)  
{  
    if (_data.Value > 100)  
      {  
          Console.WriteLine("Good data");  
      }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="5b304-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5b304-109">Example</span></span>  
 <span data-ttu-id="5b304-110">O exemplo a seguir mostra como usar a classe <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> para inicializar um tipo que é visível somente para a instância atual do objeto no thread atual.</span><span class="sxs-lookup"><span data-stu-id="5b304-110">The following example shows how to use the <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> class to initialize a type that is visible only to the current object instance on the current thread.</span></span>  
  
 [!code-csharp[CDS#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds2.cs#13)]
 [!code-vb[CDS#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/lazyhowto.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="5b304-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b304-111">See Also</span></span>  
 <xref:System.Threading.LazyInitializer?displayProperty=nameWithType>  
 [<span data-ttu-id="5b304-112">Inicialização lenta</span><span class="sxs-lookup"><span data-stu-id="5b304-112">Lazy Initialization</span></span>](../../../docs/framework/performance/lazy-initialization.md)
