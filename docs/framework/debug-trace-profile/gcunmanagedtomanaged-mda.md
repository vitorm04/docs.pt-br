---
title: MDA gcUnmanagedToManaged
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GC unmanaged to managed
- transitioning threads unmanaged to managed code
- GcUnmanagedToManaged MDA
- threading [.NET Framework], garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
- unmanaged to managed garbage collection
ms.assetid: 103eb3a3-1cf0-4406-8a9a-a7798fdc22d1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c99ae7d222db2e44de471eb9a41fed614362e300
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614374"
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="3284b-102">MDA gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="3284b-102">gcUnmanagedToManaged MDA</span></span>
<span data-ttu-id="3284b-103">O MDA (assistente para depuração gerenciada) `gcUnmanagedToManaged` causa uma coleta de lixo sempre que um thread faz a transição de código não gerenciado para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="3284b-103">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="3284b-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="3284b-104">Symptoms</span></span>  
 <span data-ttu-id="3284b-105">Um aplicativo que executa componentes de usuário não gerenciados usando o COM e a invocação de plataforma está causando uma violação de acesso não determinístico no CLR.</span><span class="sxs-lookup"><span data-stu-id="3284b-105">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="3284b-106">Causa</span><span class="sxs-lookup"><span data-stu-id="3284b-106">Cause</span></span>  
 <span data-ttu-id="3284b-107">Se um aplicativo estiver executando componentes de usuário não gerenciados, esses componentes poderão ter corrompido o heap coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="3284b-107">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="3284b-108">Isso causa uma violação de acesso no CLR quando o coletor de lixo tenta percorrer o gráfico do objeto.</span><span class="sxs-lookup"><span data-stu-id="3284b-108">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="3284b-109">Resolução</span><span class="sxs-lookup"><span data-stu-id="3284b-109">Resolution</span></span>  
 <span data-ttu-id="3284b-110">A habilitação desse assistente reduz o tempo entre o período em que o componente não gerenciado corrompe o heap coletado como lixo e o período em que ocorre a violação de acesso, forçando uma coleta de lixo antes de cada transição gerenciada.</span><span class="sxs-lookup"><span data-stu-id="3284b-110">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="3284b-111">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="3284b-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="3284b-112">Causa uma coleta de lixo sempre que um thread faz a transição de código não gerenciado para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="3284b-112">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="3284b-113">Saída</span><span class="sxs-lookup"><span data-stu-id="3284b-113">Output</span></span>  
 <span data-ttu-id="3284b-114">Esse MDA não produz nenhuma saída.</span><span class="sxs-lookup"><span data-stu-id="3284b-114">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="3284b-115">Configuração</span><span class="sxs-lookup"><span data-stu-id="3284b-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3284b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3284b-116">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="3284b-117">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="3284b-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="3284b-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="3284b-118">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)
- [<span data-ttu-id="3284b-119">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="3284b-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
