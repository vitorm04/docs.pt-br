---
title: "Segurança e condições de corrida"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c092113f670c5799d98dcb13c9c713bbd1a47fb6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="80a49-102">Segurança e condições de corrida</span><span class="sxs-lookup"><span data-stu-id="80a49-102">Security and Race Conditions</span></span>
<span data-ttu-id="80a49-103">Outra área de interesse é a possibilidade de falhas de segurança explorado por condições de corrida.</span><span class="sxs-lookup"><span data-stu-id="80a49-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="80a49-104">Há várias maneiras em que isso pode acontecer.</span><span class="sxs-lookup"><span data-stu-id="80a49-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="80a49-105">Os seguintes subtópicos descrevem algumas das principais armadilhas que o desenvolvedor deve evitar.</span><span class="sxs-lookup"><span data-stu-id="80a49-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="80a49-106">Condições de corrida no método Dispose</span><span class="sxs-lookup"><span data-stu-id="80a49-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="80a49-107">Se uma classe **Dispose** método (para obter mais informações, consulte [coleta de lixo](../../../docs/standard/garbage-collection/index.md)) não é sincronizada, é possível que o código de limpeza dentro de **Dispose** pode ser executado mais de vez, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="80a49-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../../../docs/standard/garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
```vb  
Sub Dispose()  
    If Not (myObj Is Nothing) Then  
       Cleanup(myObj)  
       myObj = Nothing  
    End If  
End Sub  
```  
  
```csharp  
void Dispose()   
{  
    if( myObj != null )   
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 <span data-ttu-id="80a49-108">Porque isso **Dispose** implementação não está sincronizada, é possível `Cleanup` a ser chamado pelo primeiro um thread e, em seguida, um thread de segundo antes `_myObj` é definido como **nulo**.</span><span class="sxs-lookup"><span data-stu-id="80a49-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="80a49-109">Se isso for uma preocupação de segurança depende do que acontece quando o `Cleanup` código é executado.</span><span class="sxs-lookup"><span data-stu-id="80a49-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="80a49-110">Um grande problema com sincronizado **Dispose** implementações envolve o uso de identificadores de recursos, como arquivos.</span><span class="sxs-lookup"><span data-stu-id="80a49-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="80a49-111">Descarte inadequado pode fazer com que o identificador incorreto para ser usada, que geralmente leva a vulnerabilidades de segurança.</span><span class="sxs-lookup"><span data-stu-id="80a49-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="80a49-112">Condições de corrida em construtores</span><span class="sxs-lookup"><span data-stu-id="80a49-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="80a49-113">Em alguns aplicativos, pode ser possível para outros threads para acessar membros de classe antes de executaram completamente seus construtores de classe.</span><span class="sxs-lookup"><span data-stu-id="80a49-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="80a49-114">Você deve revisar todos os construtores de classe para certificar-se de que não há nenhum problema de segurança se isso deve acontecer ou sincronizar threads, se necessário.</span><span class="sxs-lookup"><span data-stu-id="80a49-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="80a49-115">Condições de corrida com objetos armazenados em cache</span><span class="sxs-lookup"><span data-stu-id="80a49-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="80a49-116">Código que armazena informações de segurança ou usa a segurança de acesso do código [Assert](../../../docs/framework/misc/using-the-assert-method.md) operação também pode ser vulnerável a condições de corrida se outras partes da classe não estão sincronizados corretamente, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="80a49-116">Code that caches security information or uses the code access security [Assert](../../../docs/framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False()  
    End If  
End Sub  
  
Sub DoOtherWork()  
    If fCallersOK Then  
        DoSomethingTrusted()  
    Else  
        DemandSomething()  
        DoSomethingTrusted()  
    End If  
End Sub  
```  
  
```csharp  
void SomeSecureFunction()   
{  
    if(SomeDemandPasses())   
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false();  
    }  
}  
void DoOtherWork()   
{  
    if( fCallersOK )   
    {  
        DoSomethingTrusted();  
    }  
    else   
    {  
        DemandSomething();  
        DoSomethingTrusted();  
    }  
}  
```  
  
 <span data-ttu-id="80a49-117">Se não houver outros caminhos para `DoOtherWork` que pode ser chamado de outro thread com o mesmo objeto, um chamador não confiável pode ser adiada uma demanda passada.</span><span class="sxs-lookup"><span data-stu-id="80a49-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="80a49-118">Se seu código armazena em cache as informações de segurança, certifique-se de que você examine para essa vulnerabilidade.</span><span class="sxs-lookup"><span data-stu-id="80a49-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="80a49-119">Condições de corrida em finalizadores</span><span class="sxs-lookup"><span data-stu-id="80a49-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="80a49-120">Condições de corrida também podem ocorrer em um objeto que faz referência a um recurso estático ou não gerenciado que, em seguida, libera no seu finalizador.</span><span class="sxs-lookup"><span data-stu-id="80a49-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="80a49-121">Se vários objetos compartilharem um recurso que é manipulado no finalizador da classe, os objetos devem sincronizar todo o acesso a esse recurso.</span><span class="sxs-lookup"><span data-stu-id="80a49-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80a49-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80a49-122">See Also</span></span>  
 [<span data-ttu-id="80a49-123">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="80a49-123">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
