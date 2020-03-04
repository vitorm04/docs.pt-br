---
title: Segurança e condições de corrida
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
ms.openlocfilehash: bc0d9f481fd212ede55bffde6cc20c3e080629e4
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159410"
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="17eca-102">Segurança e condições de corrida</span><span class="sxs-lookup"><span data-stu-id="17eca-102">Security and Race Conditions</span></span>
<span data-ttu-id="17eca-103">Outra área de preocupação é o potencial de brechas de segurança exploradas por condições de corrida.</span><span class="sxs-lookup"><span data-stu-id="17eca-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="17eca-104">Há várias maneiras pelas quais isso pode acontecer.</span><span class="sxs-lookup"><span data-stu-id="17eca-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="17eca-105">Os subtópicos a seguir descrevem algumas das principais armadilhas que o desenvolvedor deve evitar.</span><span class="sxs-lookup"><span data-stu-id="17eca-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="17eca-106">Condições de corrida no método Dispose</span><span class="sxs-lookup"><span data-stu-id="17eca-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="17eca-107">Se o método **Dispose** de uma classe (para obter mais informações, consulte [coleta de lixo](../../../docs/standard/garbage-collection/index.md)) não estiver sincronizado, é possível que o código de limpeza dentro de **Dispose** possa ser executado mais de uma vez, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="17eca-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../../../docs/standard/garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="17eca-108">Como essa implementação **Dispose** não é sincronizada, é possível que `Cleanup` seja chamado pelo primeiro thread e, depois, por um segundo thread antes que `_myObj` seja definido como **NULL**.</span><span class="sxs-lookup"><span data-stu-id="17eca-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="17eca-109">Se essa é uma preocupação de segurança depende do que acontece quando o código de `Cleanup` é executado.</span><span class="sxs-lookup"><span data-stu-id="17eca-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="17eca-110">Um grande problema com implementações de **Dispose** não sincronizadas envolve o uso de identificadores de recursos, como arquivos.</span><span class="sxs-lookup"><span data-stu-id="17eca-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="17eca-111">A alienação imprópria pode fazer com que o identificador errado seja usado, o que geralmente leva a vulnerabilidades de segurança.</span><span class="sxs-lookup"><span data-stu-id="17eca-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="17eca-112">Condições de corrida em construtores</span><span class="sxs-lookup"><span data-stu-id="17eca-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="17eca-113">Em alguns aplicativos, pode ser possível que outros threads acessem os membros da classe antes que seus construtores de classe tenham sido executados completamente.</span><span class="sxs-lookup"><span data-stu-id="17eca-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="17eca-114">Você deve examinar todos os construtores de classe para garantir que não haja problemas de segurança se isso ocorrer ou sincronizar threads, se necessário.</span><span class="sxs-lookup"><span data-stu-id="17eca-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="17eca-115">Condições de corrida com objetos armazenados em cache</span><span class="sxs-lookup"><span data-stu-id="17eca-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="17eca-116">O código que armazena em cache informações de segurança ou usa a operação de [declaração](../../../docs/framework/misc/using-the-assert-method.md) de segurança de acesso ao código também pode ser vulnerável a condições de corrida se outras partes da classe não estiverem sincronizadas adequadamente, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="17eca-116">Code that caches security information or uses the code access security [Assert](../../../docs/framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="17eca-117">Se houver outros caminhos para `DoOtherWork` que podem ser chamados de outro thread com o mesmo objeto, um chamador não confiável poderá passar por uma demanda.</span><span class="sxs-lookup"><span data-stu-id="17eca-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="17eca-118">Se o código armazenar em cache as informações de segurança, certifique-se de analisá-las para essa vulnerabilidade.</span><span class="sxs-lookup"><span data-stu-id="17eca-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="17eca-119">Condições de corrida em finalizadores</span><span class="sxs-lookup"><span data-stu-id="17eca-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="17eca-120">As condições de corrida também podem ocorrer em um objeto que faz referência a um recurso estático ou não gerenciado que ele libera em seu finalizador.</span><span class="sxs-lookup"><span data-stu-id="17eca-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="17eca-121">Se vários objetos compartilharem um recurso que é manipulado no finalizador de uma classe, os objetos deverão sincronizar todo o acesso a esse recurso.</span><span class="sxs-lookup"><span data-stu-id="17eca-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17eca-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="17eca-122">See also</span></span>

- [<span data-ttu-id="17eca-123">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="17eca-123">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
