---
title: MDA invalidApartmentStateChange
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid apartment state
- managed debugging assistants (MDAs), invalid apartment state
- InvalidApartmentStateChange MDA
- invalid apartment state changes
- threading [.NET Framework], apartment states
- apartment states
- threading [.NET Framework], managed debugging assistants
- COM apartment states
ms.assetid: e56fb9df-5286-4be7-b313-540c4d876cd7
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 654e950aab0e8ae2929a62e035ffc1252c5717d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="invalidapartmentstatechange-mda"></a><span data-ttu-id="117d8-102">MDA invalidApartmentStateChange</span><span class="sxs-lookup"><span data-stu-id="117d8-102">invalidApartmentStateChange MDA</span></span>
<span data-ttu-id="117d8-103">O MDS (Assistente de Depuração Gerenciado) de `invalidApartmentStateChange` é ativado por qualquer um de dois problemas:</span><span class="sxs-lookup"><span data-stu-id="117d8-103">The `invalidApartmentStateChange` managed debugging assistant (MDS) is activated by either of two problems:</span></span>  
  
-   <span data-ttu-id="117d8-104">É feita uma tentativa de alterar o estado de apartment COM de um thread que já foi inicializado pelo COM para um estado de apartment diferente.</span><span class="sxs-lookup"><span data-stu-id="117d8-104">An attempt is made to change the COM apartment state of a thread that has already been initialized by COM to a different apartment state.</span></span>  
  
-   <span data-ttu-id="117d8-105">O estado de apartment COM de um thread é alterado inesperadamente.</span><span class="sxs-lookup"><span data-stu-id="117d8-105">The COM apartment state of a thread changes unexpectedly.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="117d8-106">Sintomas</span><span class="sxs-lookup"><span data-stu-id="117d8-106">Symptoms</span></span>  
  
-   <span data-ttu-id="117d8-107">Estado de apartment COM de um thread não é o que foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="117d8-107">A thread's COM apartment state is not what was requested.</span></span> <span data-ttu-id="117d8-108">Isso pode fazer com que proxies sejam usados para componentes COM que têm um modelo de threading diferente do atual.</span><span class="sxs-lookup"><span data-stu-id="117d8-108">This may cause proxies to be used for COM components that have a threading model different from the current one.</span></span> <span data-ttu-id="117d8-109">Isso, por sua vez, pode fazer com que uma <xref:System.InvalidCastException> seja gerada ao chamar o objeto COM por meio de interfaces não definidas para marshaling entre apartments.</span><span class="sxs-lookup"><span data-stu-id="117d8-109">This in turn may cause an <xref:System.InvalidCastException> to be thrown when calling the COM object through interfaces that are not set up for cross-apartment marshaling.</span></span>  
  
-   <span data-ttu-id="117d8-110">O estado de apartment COM do thread é diferente do esperado.</span><span class="sxs-lookup"><span data-stu-id="117d8-110">The COM apartment state of the thread is different than expected.</span></span> <span data-ttu-id="117d8-111">Isso pode causar uma <xref:System.Runtime.InteropServices.COMException> com um HRESULT RPC_E_WRONG_THREAD, bem como uma <xref:System.InvalidCastException> ao fazer chamadas em um [RCW](../../../docs/framework/interop/runtime-callable-wrapper.md) (Runtime Callable Wrapper).</span><span class="sxs-lookup"><span data-stu-id="117d8-111">This can cause a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD as well as a <xref:System.InvalidCastException> when making calls on a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="117d8-112">Isso também pode fazer com que alguns componentes COM de thread único sejam acessados por vários threads ao mesmo tempo, o que pode levar a danos ou perda de dados.</span><span class="sxs-lookup"><span data-stu-id="117d8-112">This can also cause some single-threaded COM components to be accessed by multiple threads at the same time, which can lead to corruption or data loss.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="117d8-113">Causa</span><span class="sxs-lookup"><span data-stu-id="117d8-113">Cause</span></span>  
  
-   <span data-ttu-id="117d8-114">O thread foi inicializado anteriormente para um estado de apartment COM diferente.</span><span class="sxs-lookup"><span data-stu-id="117d8-114">The thread was previously initialized to a different COM apartment state.</span></span> <span data-ttu-id="117d8-115">Observe que o estado de apartment de um thread pode ser definido explicitamente ou implicitamente.</span><span class="sxs-lookup"><span data-stu-id="117d8-115">Note that the apartment state of a thread can be set either explicitly or implicitly.</span></span> <span data-ttu-id="117d8-116">As operações explícitas incluem a propriedade <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> e os métodos <xref:System.Threading.Thread.SetApartmentState%2A> e <xref:System.Threading.Thread.TrySetApartmentState%2A>.</span><span class="sxs-lookup"><span data-stu-id="117d8-116">The explicit operations include the <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> property and the <xref:System.Threading.Thread.SetApartmentState%2A> and <xref:System.Threading.Thread.TrySetApartmentState%2A> methods.</span></span> <span data-ttu-id="117d8-117">Um thread criado usando o método <xref:System.Threading.Thread.Start%2A> está implicitamente definido como <xref:System.Threading.ApartmentState.MTA>, a menos que <xref:System.Threading.Thread.SetApartmentState%2A> seja chamado antes do thread ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="117d8-117">A thread created using the <xref:System.Threading.Thread.Start%2A> method is implicitly set to <xref:System.Threading.ApartmentState.MTA> unless <xref:System.Threading.Thread.SetApartmentState%2A> is called before the thread is started.</span></span> <span data-ttu-id="117d8-118">O thread principal do aplicativo também é implicitamente inicializado como <xref:System.Threading.ApartmentState.MTA>, a menos que o atributo <xref:System.STAThreadAttribute> seja especificado no método principal.</span><span class="sxs-lookup"><span data-stu-id="117d8-118">The main thread of the application is also implicitly initialized to <xref:System.Threading.ApartmentState.MTA> unless the <xref:System.STAThreadAttribute> attribute is specified on the main method.</span></span>  
  
-   <span data-ttu-id="117d8-119">O método `CoUninitialize` (ou o método `CoInitializeEx`) com um modelo de simultaneidade diferente é chamado no thread.</span><span class="sxs-lookup"><span data-stu-id="117d8-119">The `CoUninitialize` method (or the `CoInitializeEx` method) with a different concurrency model is called on the thread.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="117d8-120">Resolução</span><span class="sxs-lookup"><span data-stu-id="117d8-120">Resolution</span></span>  
 <span data-ttu-id="117d8-121">Defina o estado de apartment do thread antes que ele comece a executar ou então aplique o atributo <xref:System.STAThreadAttribute> ou o atributo <xref:System.MTAThreadAttribute> ao método principal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="117d8-121">Set the apartment state of the thread before it begins executing, or apply either the <xref:System.STAThreadAttribute> attribute or the <xref:System.MTAThreadAttribute> attribute to the main method of the application.</span></span>  
  
 <span data-ttu-id="117d8-122">Para a segunda causa, idealmente, o código que chama o método `CoUninitialize` deve ser modificado para atrasar a chamada até que o thread esteja prestes a ser encerrado e que não exista nenhum RCW nem componentes COM subjacentes que ainda estejam em uso pelo thread.</span><span class="sxs-lookup"><span data-stu-id="117d8-122">For the second cause, ideally, the code that calls the `CoUninitialize` method should be modified to delay the call until the thread is about to terminate and there are no RCWs and their underlying COM components still in use by the thread.</span></span> <span data-ttu-id="117d8-123">No entanto, se não é possível modificar o código que chama o método `CoUninitialize`, então nenhum RCWs devem ser usado de threads cuja inicialização é cancelada dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="117d8-123">However, if it is not possible to modify the code that calls the `CoUninitialize` method, then no RCWs should be used from threads that are uninitialized in this way.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="117d8-124">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="117d8-124">Effect on the Runtime</span></span>  
 <span data-ttu-id="117d8-125">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="117d8-125">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="117d8-126">Saída</span><span class="sxs-lookup"><span data-stu-id="117d8-126">Output</span></span>  
 <span data-ttu-id="117d8-127">O estado de apartment COM do thread atual e o estado em que o código estava tentando aplicar.</span><span class="sxs-lookup"><span data-stu-id="117d8-127">The COM apartment state of the current thread, and the state that the code was attempting to apply.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="117d8-128">Configuração</span><span class="sxs-lookup"><span data-stu-id="117d8-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="117d8-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="117d8-129">Example</span></span>  
 <span data-ttu-id="117d8-130">O exemplo de código a seguir demonstra uma situação que pode ativar esse MDA.</span><span class="sxs-lookup"><span data-stu-id="117d8-130">The following code example demonstrates a situation that can activate this MDA.</span></span>  
  
```  
using System.Threading;  
namespace ApartmentStateMDA  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Thread.CurrentThread.SetApartmentState(ApartmentState.STA);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="117d8-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="117d8-131">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="117d8-132">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="117d8-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="117d8-133">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="117d8-133">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
