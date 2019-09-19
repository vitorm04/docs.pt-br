---
title: MDA gcManagedToUnmanaged
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GcManagedToUnmanaged MDA
- GC managed to unmanaged
- transitioning threads managed to unmanaged code
- threading [.NET Framework], garbage collection
- managed to unmanaged garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
ms.assetid: 7417f837-805e-4fed-a430-ca919c8421dc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: afc0fd47e51723a7b3ba1b07dffc49260f88917d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052777"
---
# <a name="gcmanagedtounmanaged-mda"></a><span data-ttu-id="6c452-102">MDA gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="6c452-102">gcManagedToUnmanaged MDA</span></span>
<span data-ttu-id="6c452-103">O MDA (assistente para depuração gerenciada) `gcManagedToUnmanaged` causa uma coleta de lixo sempre que um thread faz a transição de código gerenciado para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="6c452-103">The `gcManagedToUnmanaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="6c452-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="6c452-104">Symptoms</span></span>  
 <span data-ttu-id="6c452-105">Um componente de usuário não gerenciado gera uma violação de acesso ao tentar usar um objeto gerenciado que tinha sido exposto a COM.</span><span class="sxs-lookup"><span data-stu-id="6c452-105">An unmanaged user component throws an access violation when trying to use a managed object that had been exposed to COM.</span></span> <span data-ttu-id="6c452-106">O objeto COM parece ter sido liberado.</span><span class="sxs-lookup"><span data-stu-id="6c452-106">The COM object appears to have been released.</span></span> <span data-ttu-id="6c452-107">A violação de acesso é não determinística.</span><span class="sxs-lookup"><span data-stu-id="6c452-107">The access violation is nondeterministic.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="6c452-108">Causa</span><span class="sxs-lookup"><span data-stu-id="6c452-108">Cause</span></span>  
 <span data-ttu-id="6c452-109">Se um componente não gerenciado não estiver fazendo uma contagem de referência de um objeto COM gerenciado corretamente, o tempo de execução poderá coletar um objeto gerenciado exposto ao COM quando o componente não gerenciado ainda contiver uma referência ao objeto.</span><span class="sxs-lookup"><span data-stu-id="6c452-109">If an unmanaged component is not reference counting a managed COM object correctly, then the runtime could collect a managed object exposed to COM when the unmanaged component still holds a reference to the object.</span></span> <span data-ttu-id="6c452-110">O tempo de execução chama <xref:System.Runtime.InteropServices.Marshal.Release%2A> durante as coletas de lixo e, portanto, se o componente de usuário usar o objeto antes que a coleta de lixo ocorra, ele ainda não terá sido coletado.</span><span class="sxs-lookup"><span data-stu-id="6c452-110">The runtime calls <xref:System.Runtime.InteropServices.Marshal.Release%2A> during garbage collections, so if the user component uses the object before the garbage collection occurs, then it will not yet have been collected.</span></span> <span data-ttu-id="6c452-111">Essa é a origem do não determinismo.</span><span class="sxs-lookup"><span data-stu-id="6c452-111">This is the source of the nondeterminism.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="6c452-112">Resolução</span><span class="sxs-lookup"><span data-stu-id="6c452-112">Resolution</span></span>  
 <span data-ttu-id="6c452-113">A habilitação deste assistente reduz o tempo entre o período em que o objeto é qualificado para a coleta e <xref:System.Runtime.InteropServices.Marshal.Release%2A> é chamado, ajudando a rastrear qual componente não gerenciado tenta acessar o objeto coletado primeiro.</span><span class="sxs-lookup"><span data-stu-id="6c452-113">Enabling this assistant reduces the time between when the object is eligible for collection and <xref:System.Runtime.InteropServices.Marshal.Release%2A> is called, helping to track down which unmanaged component first tries to access the collected object.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="6c452-114">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="6c452-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="6c452-115">Causa uma coleta de lixo sempre que um thread faz a transição de código gerenciado para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="6c452-115">Causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="6c452-116">Saída</span><span class="sxs-lookup"><span data-stu-id="6c452-116">Output</span></span>  
 <span data-ttu-id="6c452-117">Esse MDA não produz nenhuma saída.</span><span class="sxs-lookup"><span data-stu-id="6c452-117">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="6c452-118">Configuração</span><span class="sxs-lookup"><span data-stu-id="6c452-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c452-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c452-119">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="6c452-120">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="6c452-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="6c452-121">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="6c452-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
- [<span data-ttu-id="6c452-122">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="6c452-122">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)
