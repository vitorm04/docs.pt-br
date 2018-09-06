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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3e613ad4823254a6bed43cb95294e6b8d3674b6d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881743"
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="55fdc-102">Segurança e condições de corrida</span><span class="sxs-lookup"><span data-stu-id="55fdc-102">Security and Race Conditions</span></span>
<span data-ttu-id="55fdc-103">Outra área de interesse é o potencial para brechas de segurança exploradas por condições de corrida.</span><span class="sxs-lookup"><span data-stu-id="55fdc-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="55fdc-104">Há várias maneiras em que isso pode acontecer.</span><span class="sxs-lookup"><span data-stu-id="55fdc-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="55fdc-105">Os subtópicos seguir descrevem algumas das principais armadilhas que o desenvolvedor deve evitar.</span><span class="sxs-lookup"><span data-stu-id="55fdc-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="55fdc-106">Condições de corrida no método Dispose</span><span class="sxs-lookup"><span data-stu-id="55fdc-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="55fdc-107">Se uma classe **Dispose** método (para obter mais informações, consulte [coleta de lixo](../../../docs/standard/garbage-collection/index.md)) não é sincronizado, é possível esse código de limpeza dentro **Dispose** pode ser executado mais de uma vez, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="55fdc-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../../../docs/standard/garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="55fdc-108">Porque isso **Dispose** implementação não está sincronizada, é possível `Cleanup` a ser chamado pelo primeiro um thread e, em seguida, um segundo thread antes `_myObj` está definido como **nulo**.</span><span class="sxs-lookup"><span data-stu-id="55fdc-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="55fdc-109">Se esta é uma preocupação de segurança depende do que acontece quando o `Cleanup` código é executado.</span><span class="sxs-lookup"><span data-stu-id="55fdc-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="55fdc-110">Um grande problema com não sincronizadas **Dispose** implementações envolve o uso de identificadores de recurso, como arquivos.</span><span class="sxs-lookup"><span data-stu-id="55fdc-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="55fdc-111">Descarte inadequado pode fazer com que o identificador errado a ser usado, o que muitas vezes leva a vulnerabilidades de segurança.</span><span class="sxs-lookup"><span data-stu-id="55fdc-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="55fdc-112">Condições de corrida em construtores</span><span class="sxs-lookup"><span data-stu-id="55fdc-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="55fdc-113">Em alguns aplicativos, pode ser possível que outros threads acessar membros de classe antes de executaram completamente seus construtores de classe.</span><span class="sxs-lookup"><span data-stu-id="55fdc-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="55fdc-114">Você deve examinar todos os construtores de classe para certificar-se de que não há nenhum problema de segurança se isso deve acontecer ou sincronizar threads, se necessário.</span><span class="sxs-lookup"><span data-stu-id="55fdc-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="55fdc-115">Condições de corrida com objetos armazenados em cache</span><span class="sxs-lookup"><span data-stu-id="55fdc-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="55fdc-116">Código que armazena em cache informações de segurança ou usa a segurança de acesso do código [Assert](../../../docs/framework/misc/using-the-assert-method.md) operação também pode ser vulnerável a condições de corrida se outras partes da classe não estão sincronizados corretamente, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="55fdc-116">Code that caches security information or uses the code access security [Assert](../../../docs/framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="55fdc-117">Se houver outros caminhos para `DoOtherWork` que podem ser chamados de outro thread com o mesmo objeto, um chamador não confiável pode ser adiada uma demanda passada.</span><span class="sxs-lookup"><span data-stu-id="55fdc-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="55fdc-118">Se seu código armazena em cache informações de segurança, certifique-se de que você examine essa vulnerabilidade.</span><span class="sxs-lookup"><span data-stu-id="55fdc-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="55fdc-119">Condições de corrida em finalizadores</span><span class="sxs-lookup"><span data-stu-id="55fdc-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="55fdc-120">Condições de corrida também podem ocorrer em um objeto que faz referência a um recurso estático ou não gerenciado que ele libera, em seguida, no seu finalizador.</span><span class="sxs-lookup"><span data-stu-id="55fdc-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="55fdc-121">Se vários objetos compartilham um recurso que é manipulado no finalizador de uma classe, os objetos devem sincronizar todo o acesso a esse recurso.</span><span class="sxs-lookup"><span data-stu-id="55fdc-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55fdc-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55fdc-122">See also</span></span>

- [<span data-ttu-id="55fdc-123">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="55fdc-123">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
