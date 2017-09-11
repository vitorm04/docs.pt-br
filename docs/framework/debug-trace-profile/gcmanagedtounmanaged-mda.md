---
title: MDA gcManagedToUnmanaged
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
caps.latest.revision: 13
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 03dbbee0c45e5c256c40157c8cebebc2507f7e01
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="gcmanagedtounmanaged-mda"></a><span data-ttu-id="113e8-102">MDA gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="113e8-102">gcManagedToUnmanaged MDA</span></span>
<span data-ttu-id="113e8-103">O MDA (assistente para depuração gerenciada) `gcManagedToUnmanaged` causa uma coleta de lixo sempre que um thread faz a transição de código gerenciado para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="113e8-103">The `gcManagedToUnmanaged` managed debugging assistant (MDA) causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="113e8-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="113e8-104">Symptoms</span></span>  
 <span data-ttu-id="113e8-105">Um componente de usuário não gerenciado gera uma violação de acesso ao tentar usar um objeto gerenciado que tinha sido exposto a COM.</span><span class="sxs-lookup"><span data-stu-id="113e8-105">An unmanaged user component throws an access violation when trying to use a managed object that had been exposed to COM.</span></span> <span data-ttu-id="113e8-106">O objeto COM parece ter sido liberado.</span><span class="sxs-lookup"><span data-stu-id="113e8-106">The COM object appears to have been released.</span></span> <span data-ttu-id="113e8-107">A violação de acesso é não determinística.</span><span class="sxs-lookup"><span data-stu-id="113e8-107">The access violation is nondeterministic.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="113e8-108">Causa</span><span class="sxs-lookup"><span data-stu-id="113e8-108">Cause</span></span>  
 <span data-ttu-id="113e8-109">Se um componente não gerenciado não estiver fazendo uma contagem de referência de um objeto COM gerenciado corretamente, o tempo de execução poderá coletar um objeto gerenciado exposto ao COM quando o componente não gerenciado ainda contiver uma referência ao objeto.</span><span class="sxs-lookup"><span data-stu-id="113e8-109">If an unmanaged component is not reference counting a managed COM object correctly, then the runtime could collect a managed object exposed to COM when the unmanaged component still holds a reference to the object.</span></span> <span data-ttu-id="113e8-110">O tempo de execução chama <xref:System.Runtime.InteropServices.Marshal.Release%2A> durante as coletas de lixo e, portanto, se o componente de usuário usar o objeto antes que a coleta de lixo ocorra, ele ainda não terá sido coletado.</span><span class="sxs-lookup"><span data-stu-id="113e8-110">The runtime calls <xref:System.Runtime.InteropServices.Marshal.Release%2A> during garbage collections, so if the user component uses the object before the garbage collection occurs, then it will not yet have been collected.</span></span> <span data-ttu-id="113e8-111">Essa é a origem do não determinismo.</span><span class="sxs-lookup"><span data-stu-id="113e8-111">This is the source of the nondeterminism.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="113e8-112">Resolução</span><span class="sxs-lookup"><span data-stu-id="113e8-112">Resolution</span></span>  
 <span data-ttu-id="113e8-113">A habilitação deste assistente reduz o tempo entre o período em que o objeto é qualificado para a coleta e <xref:System.Runtime.InteropServices.Marshal.Release%2A> é chamado, ajudando a rastrear qual componente não gerenciado tenta acessar o objeto coletado primeiro.</span><span class="sxs-lookup"><span data-stu-id="113e8-113">Enabling this assistant reduces the time between when the object is eligible for collection and <xref:System.Runtime.InteropServices.Marshal.Release%2A> is called, helping to track down which unmanaged component first tries to access the collected object.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="113e8-114">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="113e8-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="113e8-115">Causa uma coleta de lixo sempre que um thread faz a transição de código gerenciado para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="113e8-115">Causes a garbage collection whenever a thread transitions from managed to unmanaged code.</span></span>  
  
## <a name="output"></a><span data-ttu-id="113e8-116">Saída</span><span class="sxs-lookup"><span data-stu-id="113e8-116">Output</span></span>  
 <span data-ttu-id="113e8-117">Esse MDA não produz nenhuma saída.</span><span class="sxs-lookup"><span data-stu-id="113e8-117">This MDA produces no output.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="113e8-118">Configuração</span><span class="sxs-lookup"><span data-stu-id="113e8-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="113e8-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="113e8-119">See Also</span></span>  
 <span data-ttu-id="113e8-120"><xref:System.Runtime.InteropServices.MarshalAsAttribute></span><span class="sxs-lookup"><span data-stu-id="113e8-120"><xref:System.Runtime.InteropServices.MarshalAsAttribute></span></span>   
 <span data-ttu-id="113e8-121">[Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md) </span><span class="sxs-lookup"><span data-stu-id="113e8-121">[Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md) </span></span>  
 <span data-ttu-id="113e8-122">[Marshaling de interoperabilidade](../../../docs/framework/interop/interop-marshaling.md) </span><span class="sxs-lookup"><span data-stu-id="113e8-122">[Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md) </span></span>  
 [<span data-ttu-id="113e8-123">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="113e8-123">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)

