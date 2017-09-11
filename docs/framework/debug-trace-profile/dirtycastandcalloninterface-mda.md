---
title: MDA dirtyCastAndCallOnInterface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- managed debugging assistants (MDAs), early bound calls AutoDispatch
- dispatch-only mode
- dirtyCastAndCallOnInterface
- early-bound managed classes
- early bound calls on AutoDispatch
- MDAs (managed debugging assistants), early bound calls AutoDispatch
- EarlyBoundCallOnAutorDispatchClassInteface MDA
ms.assetid: aa388ed3-7e3d-48ea-a0b5-c47ae19cec38
caps.latest.revision: 17
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 838348b3af485025ee196931237527333be73235
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="dirtycastandcalloninterface-mda"></a><span data-ttu-id="26d0e-102">MDA dirtyCastAndCallOnInterface</span><span class="sxs-lookup"><span data-stu-id="26d0e-102">dirtyCastAndCallOnInterface MDA</span></span>
<span data-ttu-id="26d0e-103">O MDA (assistente para depuração gerenciada) `dirtyCastAndCallOnInterface` é ativado quando há uma tentativa de realizar uma chamada de associação inicial por meio de uma vtable em uma interface de classe que foi marcada como somente associação tardia.</span><span class="sxs-lookup"><span data-stu-id="26d0e-103">The `dirtyCastAndCallOnInterface` managed debugging assistant (MDA) is activated when an early-bound call through a vtable is attempted on a class interface that has been marked late-bound only.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="26d0e-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="26d0e-104">Symptoms</span></span>  
 <span data-ttu-id="26d0e-105">Um aplicativo gera uma violação de acesso ou tem um comportamento inesperado quando você faz uma chamada de associação inicial por meio do COM ao CLR.</span><span class="sxs-lookup"><span data-stu-id="26d0e-105">An application throws an access violation or has unexpected behavior when placing an early-bound call via COM into the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="26d0e-106">Causa</span><span class="sxs-lookup"><span data-stu-id="26d0e-106">Cause</span></span>  
 <span data-ttu-id="26d0e-107">O código está tentando fazer uma chamada de associação inicial por meio de uma vtable em uma interface de classe que é somente associação tardia.</span><span class="sxs-lookup"><span data-stu-id="26d0e-107">Code is attempting an early-bound call through a vtable via a class interface that is late-bound only.</span></span> <span data-ttu-id="26d0e-108">Observe que, por padrão, as interfaces de classe são identificadas como sendo somente de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="26d0e-108">Note that by default class interfaces are identified as being late-bound only.</span></span> <span data-ttu-id="26d0e-109">Elas também podem ser identificadas como sendo de associação tardia com o atributo <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> com um valor <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span><span class="sxs-lookup"><span data-stu-id="26d0e-109">They can also be identified as late-bound with the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute with an <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch> value (`[ClassInterface(ClassInterfaceType.AutoDispatch)]`).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="26d0e-110">Resolução</span><span class="sxs-lookup"><span data-stu-id="26d0e-110">Resolution</span></span>  
 <span data-ttu-id="26d0e-111">A resolução recomendada é definir uma interface explícita para uso pelo COM e fazer com que os clientes COM façam a chamada por meio dessa interface, em vez de por meio da interface de classe gerada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="26d0e-111">The recommended resolution is to define an explicit interface for use by COM and have the COM clients call through this interface instead of through the automatically generated class interface.</span></span> <span data-ttu-id="26d0e-112">Como alternativa, a chamada do COM pode ser transformada em uma chamada de associação tardia por meio de `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="26d0e-112">Alternatively, the call from COM can be transformed into a late-bound call via `IDispatch`.</span></span>  
  
 <span data-ttu-id="26d0e-113">Por fim, é possível identificar a classe como <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) para permitir que as chamadas de associação inicial sejam feitas por meio do COM; no entanto, o uso de <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> não é recomendado devido às limitações de controle de versão descritas no <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span><span class="sxs-lookup"><span data-stu-id="26d0e-113">Finally, it is possible to identify the class as <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> (`[ClassInterface(ClassInterfaceType.AutoDual)]`) to allow early bound calls to be placed from COM; however, using <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual> is strongly discouraged because of the versioning limitations described in <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="26d0e-114">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="26d0e-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="26d0e-115">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="26d0e-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="26d0e-116">Ele apenas relata dados sobre chamadas de associação inicial em interfaces de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="26d0e-116">It only reports data about early-bound calls on late-bound interfaces.</span></span>  
  
## <a name="output"></a><span data-ttu-id="26d0e-117">Saída</span><span class="sxs-lookup"><span data-stu-id="26d0e-117">Output</span></span>  
 <span data-ttu-id="26d0e-118">O nome do método ou o nome do campo que está sendo acessado com associação inicial.</span><span class="sxs-lookup"><span data-stu-id="26d0e-118">The name of the method or name of the field being accessed early-bound.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="26d0e-119">Configuração</span><span class="sxs-lookup"><span data-stu-id="26d0e-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dirtyCastAndCallOnInterface />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="26d0e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26d0e-120">See Also</span></span>  
 <span data-ttu-id="26d0e-121"><xref:System.Runtime.InteropServices.ClassInterfaceAttribute></span><span class="sxs-lookup"><span data-stu-id="26d0e-121"><xref:System.Runtime.InteropServices.ClassInterfaceAttribute></span></span>   
 [<span data-ttu-id="26d0e-122">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="26d0e-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

