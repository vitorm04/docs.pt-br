---
title: Segurança e condições de corrida
'description:': Describes pitfalls to avoid around security holes exploited by race conditions, including dispose methods, constructors, cached objects, and finalizers.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
ms.openlocfilehash: 09d8d0d6e85af04fe0fb00f53df408126012081e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186789"
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="f4812-102">Segurança e condições de corrida</span><span class="sxs-lookup"><span data-stu-id="f4812-102">Security and Race Conditions</span></span>
<span data-ttu-id="f4812-103">Outra área de preocupação é o potencial de falhas de segurança exploradas pelas condições raciais.</span><span class="sxs-lookup"><span data-stu-id="f4812-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="f4812-104">Há várias maneiras pelas quais isso pode acontecer.</span><span class="sxs-lookup"><span data-stu-id="f4812-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="f4812-105">Os subtópicos que seguem descrevem algumas das principais armadilhas que o desenvolvedor deve evitar.</span><span class="sxs-lookup"><span data-stu-id="f4812-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="f4812-106">Condições de corrida no método de descarte</span><span class="sxs-lookup"><span data-stu-id="f4812-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="f4812-107">Se o método **Descarte** de uma classe (para obter mais informações, consulte [Coleta de Lixo](../../../docs/standard/garbage-collection/index.md)) não estiver sincronizado, é possível que o código de limpeza dentro de **Dispose** possa ser executado mais de uma vez, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f4812-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../../../docs/standard/garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
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
    if (myObj != null)
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 <span data-ttu-id="f4812-108">Como esta **implementação Descartar** não está `Cleanup` sincronizada, é possível ser chamado por `_myObj` primeiro thread e, em seguida, um segundo segmento antes de ser definido como **nulo**.</span><span class="sxs-lookup"><span data-stu-id="f4812-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="f4812-109">Se isso é uma preocupação de `Cleanup` segurança depende do que acontece quando o código é executado.</span><span class="sxs-lookup"><span data-stu-id="f4812-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="f4812-110">Um grande problema com **implementações de descarte** não sincronizadas envolve o uso de alças de recursos, como arquivos.</span><span class="sxs-lookup"><span data-stu-id="f4812-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="f4812-111">O descarte inadequado pode fazer com que o cabo errado seja usado, o que muitas vezes leva a vulnerabilidades de segurança.</span><span class="sxs-lookup"><span data-stu-id="f4812-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="f4812-112">Condições de corrida em Construtores</span><span class="sxs-lookup"><span data-stu-id="f4812-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="f4812-113">Em alguns aplicativos, pode ser possível que outros segmentos acessem os membros da classe antes que seus construtores de classe sejam completamente executados.</span><span class="sxs-lookup"><span data-stu-id="f4812-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="f4812-114">Você deve rever todos os construtores de classe para ter certeza de que não há problemas de segurança se isso acontecer, ou sincronizar threads, se necessário.</span><span class="sxs-lookup"><span data-stu-id="f4812-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="f4812-115">Condições de corrida com objetos armazenados em cache</span><span class="sxs-lookup"><span data-stu-id="f4812-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="f4812-116">Código que armazena informações de segurança ou usa a segurança de acesso ao código A operação [assert](../../../docs/framework/misc/using-the-assert-method.md) também pode ser vulnerável a condições de corrida se outras partes da classe não estiverem adequadamente sincronizadas, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f4812-116">Code that caches security information or uses the code access security [Assert](../../../docs/framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False  
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
    if (SomeDemandPasses())
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false;  
    }  
}  
void DoOtherWork()
{  
    if (fCallersOK)
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
  
 <span data-ttu-id="f4812-117">Se houver outros `DoOtherWork` caminhos para isso que podem ser chamados de outro segmento com o mesmo objeto, um chamador não confiável pode passar por uma demanda.</span><span class="sxs-lookup"><span data-stu-id="f4812-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="f4812-118">Se o seu código armazena informações de segurança, certifique-se de revisá-la para essa vulnerabilidade.</span><span class="sxs-lookup"><span data-stu-id="f4812-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="f4812-119">Condições de corrida em finalizadores</span><span class="sxs-lookup"><span data-stu-id="f4812-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="f4812-120">As condições de corrida também podem ocorrer em um objeto que faz referência a um recurso estático ou não gerenciado que ele então libera em seu finalizador.</span><span class="sxs-lookup"><span data-stu-id="f4812-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="f4812-121">Se vários objetos compartilharem um recurso manipulado no finalizador de uma classe, os objetos devem sincronizar todo o acesso a esse recurso.</span><span class="sxs-lookup"><span data-stu-id="f4812-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4812-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="f4812-122">See also</span></span>

- [<span data-ttu-id="f4812-123">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="f4812-123">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
