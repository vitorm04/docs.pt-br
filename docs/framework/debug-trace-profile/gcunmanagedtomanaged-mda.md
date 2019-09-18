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
ms.openlocfilehash: 1679f87276262a08f5717ea81d263f4600542971
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052771"
---
# <a name="gcunmanagedtomanaged-mda"></a><span data-ttu-id="e7f74-102">MDA gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="e7f74-102">gcUnmanagedToManaged MDA</span></span>
<span data-ttu-id="e7f74-103">O MDA (assistente para depuração gerenciada) `gcUnmanagedToManaged` causa uma coleta de lixo sempre que um thread faz a transição de código não gerenciado para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e7f74-103">The `gcUnmanagedToManaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e7f74-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="e7f74-104">Symptoms</span></span>  
 <span data-ttu-id="e7f74-105">Um aplicativo que executa componentes de usuário não gerenciados usando o COM e a invocação de plataforma está causando uma violação de acesso não determinístico no CLR.</span><span class="sxs-lookup"><span data-stu-id="e7f74-105">An application running unmanaged user components using COM and platform invoke is causing a nondeterministic access violation in the CLR.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e7f74-106">Causa</span><span class="sxs-lookup"><span data-stu-id="e7f74-106">Cause</span></span>  
 <span data-ttu-id="e7f74-107">Se um aplicativo estiver executando componentes de usuário não gerenciados, esses componentes poderão ter corrompido o heap coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="e7f74-107">If an application is running unmanaged user components, then those components might have corrupted the garbage-collected heap.</span></span> <span data-ttu-id="e7f74-108">Isso causa uma violação de acesso no CLR quando o coletor de lixo tenta percorrer o gráfico do objeto.</span><span class="sxs-lookup"><span data-stu-id="e7f74-108">This causes an access violation in the CLR when the garbage collector tries to walk the object graph.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e7f74-109">Resolução</span><span class="sxs-lookup"><span data-stu-id="e7f74-109">Resolution</span></span>  
 <span data-ttu-id="e7f74-110">A habilitação desse assistente reduz o tempo entre o período em que o componente não gerenciado corrompe o heap coletado como lixo e o período em que ocorre a violação de acesso, forçando uma coleta de lixo antes de cada transição gerenciada.</span><span class="sxs-lookup"><span data-stu-id="e7f74-110">Enabling this assistant reduces the time between when the unmanaged component corrupts the garbage-collected heap and when the access violation happens by forcing a garbage collection to occur before every managed transition.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e7f74-111">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="e7f74-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="e7f74-112">Causa uma coleta de lixo sempre que um thread faz a transição de código não gerenciado para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e7f74-112">Causes a garbage collection whenever a thread transitions from unmanaged to managed code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e7f74-113">Saída</span><span class="sxs-lookup"><span data-stu-id="e7f74-113">Output</span></span>  
 <span data-ttu-id="e7f74-114">Esse MDA não produz nenhuma saída.</span><span class="sxs-lookup"><span data-stu-id="e7f74-114">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e7f74-115">Configuração</span><span class="sxs-lookup"><span data-stu-id="e7f74-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7f74-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7f74-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="e7f74-117">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="e7f74-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="e7f74-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="e7f74-118">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)
- [<span data-ttu-id="e7f74-119">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="e7f74-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
