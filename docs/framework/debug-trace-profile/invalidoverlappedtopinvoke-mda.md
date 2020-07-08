---
title: MDA invalidOverlappedToPinvoke
description: Examine o MDA (Assistente de depuração gerenciada) do invalidOverlappedToPinvoke no .NET, que pode ser ativado durante uma falha ou uma corrupção de heap inexplicativa.
ms.date: 03/30/2017
helpviewer_keywords:
- overlapped pointers
- managed debugging assistants (MDAs), overlapped pointers
- invalid overlapped pointer to platform invoke
- InvalidOverlappedToPinvoke MDA
- MDAs (managed debugging assistants), overlapped pointers
- pointers, overlapped
ms.assetid: 28876047-58bd-4fed-9452-c7da346d67c0
ms.openlocfilehash: 162efd55bf636cf2e8698706bd011379f2f6f11f
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051695"
---
# <a name="invalidoverlappedtopinvoke-mda"></a><span data-ttu-id="1a213-103">MDA invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="1a213-103">invalidOverlappedToPinvoke MDA</span></span>
<span data-ttu-id="1a213-104">O MDA (Assistente de Depuração Gerenciado) de `invalidOverlappedToPinvoke` é ativado quando um ponteiro sobreposto que não foi criado no heap de coleta de lixo é passado para funções específicas do Win32.</span><span class="sxs-lookup"><span data-stu-id="1a213-104">The `invalidOverlappedToPinvoke` managed debugging assistant (MDA) is activated when an overlapped pointer that was not created on the garbage collection heap is passed to specific Win32 functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a213-105">Por padrão, esse MDA é ativado somente se a chamada de invocação de plataforma é definida no seu código e o depurador relata o status de JustMyCode de cada método.</span><span class="sxs-lookup"><span data-stu-id="1a213-105">By default, this MDA is activated only if the platform invoke call is defined in your code and the debugger reports the JustMyCode status of each method.</span></span> <span data-ttu-id="1a213-106">Um depurador que não entende JustMyCode (tal como MDbg.exe sem nenhuma extensão) não ativará esse MDA.</span><span class="sxs-lookup"><span data-stu-id="1a213-106">A debugger that does not understand JustMyCode (such as MDbg.exe with no extensions) will not activate this MDA.</span></span> <span data-ttu-id="1a213-107">Esse MDA pode ser habilitado para esses depuradores usando um arquivo de configuração e configurando `justMyCode="false"` explicitamente no `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>` do arquivo .mda.config).</span><span class="sxs-lookup"><span data-stu-id="1a213-107">This MDA can be enabled for those debuggers by using a configuration file and explicitly settting `justMyCode="false"` in the .mda.config file `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1a213-108">Sintomas</span><span class="sxs-lookup"><span data-stu-id="1a213-108">Symptoms</span></span>  
 <span data-ttu-id="1a213-109">Falhas ou corrupção de heap inexplicáveis.</span><span class="sxs-lookup"><span data-stu-id="1a213-109">Crashes or unexplainable heap corruptions.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1a213-110">Causa</span><span class="sxs-lookup"><span data-stu-id="1a213-110">Cause</span></span>  
 <span data-ttu-id="1a213-111">Um ponteiro sobreposto que não foi criado no heap de coleta de lixo é passado para as funções de sistema operacional específicas.</span><span class="sxs-lookup"><span data-stu-id="1a213-111">An overlapped pointer that was not created on the garbage collection heap is passed to specific operating system functions.</span></span>  
  
 <span data-ttu-id="1a213-112">A tabela a seguir mostra as funções que esse MDA acompanha.</span><span class="sxs-lookup"><span data-stu-id="1a213-112">The following table shows the functions that this MDA tracks.</span></span>  
  
|<span data-ttu-id="1a213-113">Módulo</span><span class="sxs-lookup"><span data-stu-id="1a213-113">Module</span></span>|<span data-ttu-id="1a213-114">Função</span><span class="sxs-lookup"><span data-stu-id="1a213-114">Function</span></span>|  
|------------|--------------|  
|<span data-ttu-id="1a213-115">HttpApi.dll</span><span class="sxs-lookup"><span data-stu-id="1a213-115">HttpApi.dll</span></span>|`HttpReceiveHttpRequest`|  
|<span data-ttu-id="1a213-116">IpHlpApi.dll</span><span class="sxs-lookup"><span data-stu-id="1a213-116">IpHlpApi.dll</span></span>|`NotifyAddrChange`|  
|<span data-ttu-id="1a213-117">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1a213-117">kernel32.dll</span></span>|`ReadFile`|  
|<span data-ttu-id="1a213-118">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1a213-118">kernel32.dll</span></span>|`ReadFileEx`|  
|<span data-ttu-id="1a213-119">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1a213-119">kernel32.dll</span></span>|`WriteFile`|  
|<span data-ttu-id="1a213-120">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1a213-120">kernel32.dll</span></span>|`WriteFileEx`|  
|<span data-ttu-id="1a213-121">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1a213-121">kernel32.dll</span></span>|`ReadDirectoryChangesW`|  
|<span data-ttu-id="1a213-122">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1a213-122">kernel32.dll</span></span>|`PostQueuedCompletionStatus`|  
|<span data-ttu-id="1a213-123">MSWSock.dll</span><span class="sxs-lookup"><span data-stu-id="1a213-123">MSWSock.dll</span></span>|`ConnectEx`|  
|<span data-ttu-id="1a213-124">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="1a213-124">WS2_32.dll</span></span>|`WSASend`|  
|<span data-ttu-id="1a213-125">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="1a213-125">WS2_32.dll</span></span>|`WSASendTo`|  
|<span data-ttu-id="1a213-126">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="1a213-126">WS2_32.dll</span></span>|`WSARecv`|  
|<span data-ttu-id="1a213-127">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="1a213-127">WS2_32.dll</span></span>|`WSARecvFrom`|  
|<span data-ttu-id="1a213-128">MQRT.dll</span><span class="sxs-lookup"><span data-stu-id="1a213-128">MQRT.dll</span></span>|`MQReceiveMessage`|  
  
 <span data-ttu-id="1a213-129">O potencial de corrupção de heap é alto para essa condição porque o <xref:System.AppDomain> fazendo a chamada pode ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="1a213-129">The potential for heap corruption is high for this condition because the <xref:System.AppDomain> making the call might unload.</span></span> <span data-ttu-id="1a213-130">Se o <xref:System.AppDomain> for descarregado, o código do aplicativo liberará a memória para o ponteiro sobreposto causando corrupção quando a operação for concluída ou então o código causará perda de memória, resultando em problemas mais tarde.</span><span class="sxs-lookup"><span data-stu-id="1a213-130">If the <xref:System.AppDomain> unloads, the application code will either free the memory for the overlapped pointer, causing corruption when the operation finishes, or the code will leak the memory, causing difficulties later.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1a213-131">Resolução</span><span class="sxs-lookup"><span data-stu-id="1a213-131">Resolution</span></span>  
 <span data-ttu-id="1a213-132">Use um objeto <xref:System.Threading.Overlapped>, chamando o método <xref:System.Threading.Overlapped.Pack%2A> para obter uma estrutura <xref:System.Threading.NativeOverlapped> que pode ser passada para a função.</span><span class="sxs-lookup"><span data-stu-id="1a213-132">Use an <xref:System.Threading.Overlapped> object, calling the <xref:System.Threading.Overlapped.Pack%2A> method to get a <xref:System.Threading.NativeOverlapped> structure that can be passed to the function.</span></span> <span data-ttu-id="1a213-133">Se o <xref:System.AppDomain> for descarregado, o CLR aguardará até que a operação assíncrona seja concluída antes de liberar o ponteiro.</span><span class="sxs-lookup"><span data-stu-id="1a213-133">If the <xref:System.AppDomain> unloads, the CLR waits until the asynchronous operation completes before freeing the pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1a213-134">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="1a213-134">Effect on the Runtime</span></span>  
 <span data-ttu-id="1a213-135">Esse MDA não teve efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="1a213-135">This MDA had no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1a213-136">Saída</span><span class="sxs-lookup"><span data-stu-id="1a213-136">Output</span></span>  
 <span data-ttu-id="1a213-137">A seguir temos um exemplo de saída desse MDA.</span><span class="sxs-lookup"><span data-stu-id="1a213-137">The following is an example of output from this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="1a213-138">Configuração</span><span class="sxs-lookup"><span data-stu-id="1a213-138">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a213-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a213-139">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="1a213-140">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="1a213-140">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="1a213-141">Realizando marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="1a213-141">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
