---
title: MDA virtualCERCall
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
- MDAs (managed debugging assistants), CER calls
- virtualCERCall MDA
- virtual CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
caps.latest.revision: 13
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 334900cbcc04cb1883b93a6bac17309add9ec159
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="virtualcercall-mda"></a><span data-ttu-id="2cd77-102">MDA virtualCERCall</span><span class="sxs-lookup"><span data-stu-id="2cd77-102">virtualCERCall MDA</span></span>
<span data-ttu-id="2cd77-103">O MDA (assistente para depuração gerenciada) `virtualCERCall` é ativado como um aviso, indicando que um site de chamada em um gráfico de chamadas da CER (região de execução restrita) se refere a um destino virtual, ou seja, uma chamada virtual a um método virtual não final ou uma chamada usando uma interface.</span><span class="sxs-lookup"><span data-stu-id="2cd77-103">The `virtualCERCall` managed debugging assistant (MDA) is activated as a warning indicating that a call site within a constrained execution region (CER) call graph refers to a virtual target, that is, a virtual call to a non-final virtual method or a call using an interface.</span></span> <span data-ttu-id="2cd77-104">O CLR (Common Language Runtime) não pode prever o método de destino dessas chamadas pela análise de metadados e de linguagem intermediária apenas.</span><span class="sxs-lookup"><span data-stu-id="2cd77-104">The common language runtime (CLR) cannot predict the destination method of these calls from the intermediate language and metadata analysis alone.</span></span> <span data-ttu-id="2cd77-105">Como resultado, a árvore de chamadas não pode ser preparada como parte do gráfico da CER e as anulações de thread nessa subárvore não podem ser bloqueadas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="2cd77-105">As a result, the call tree cannot be prepared as part of the CER graph and thread aborts in that subtree cannot be automatically blocked.</span></span> <span data-ttu-id="2cd77-106">Esse MDA avisa sobre casos em que uma CER talvez precise ser estendida usando chamadas explícitas ao método <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> depois que as informações adicionais necessárias para calcular o destino de chamada são conhecidas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2cd77-106">This MDA warns of cases where a CER might need to be extended by using explicit calls to the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method once the additional information required to compute the call target is known at run time.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="2cd77-107">Sintomas</span><span class="sxs-lookup"><span data-stu-id="2cd77-107">Symptoms</span></span>  
 <span data-ttu-id="2cd77-108">As CERs não são executadas quando um thread é anulado ou um domínio do aplicativo é descarregado.</span><span class="sxs-lookup"><span data-stu-id="2cd77-108">CERs that do not run when a thread is aborted or an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="2cd77-109">Causa</span><span class="sxs-lookup"><span data-stu-id="2cd77-109">Cause</span></span>  
 <span data-ttu-id="2cd77-110">Uma CER contém uma chamada a um método virtual que não pode ser preparado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="2cd77-110">A CER contains a call to a virtual method that cannot be prepared automatically.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="2cd77-111">Resolução</span><span class="sxs-lookup"><span data-stu-id="2cd77-111">Resolution</span></span>  
 <span data-ttu-id="2cd77-112">Chame <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> para o método virtual.</span><span class="sxs-lookup"><span data-stu-id="2cd77-112">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> for the virtual method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="2cd77-113">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="2cd77-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="2cd77-114">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="2cd77-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="2cd77-115">Saída</span><span class="sxs-lookup"><span data-stu-id="2cd77-115">Output</span></span>  
  
```  
Method 'MethodWithCer', while executing within a constrained execution region, makes a call  
at IL offset 0x0024 to 'VirtualMethod', which is virtual and cannot be prepared automatically  
at compile time. The caller must ensure this method is prepared explicitly at  
runtime before entering the constrained execution region.  
method name="VirtualMethod"  
declaringType name="VirtualCERCall+MyClass"  
  declaringModule name="mda"  
    callsite name="MethodWithCer" offset="0x0024"  
```  
  
## <a name="configuration"></a><span data-ttu-id="2cd77-116">Configuração</span><span class="sxs-lookup"><span data-stu-id="2cd77-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    < VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="2cd77-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2cd77-117">Example</span></span>  
  
```  
class MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    virtual void VirtualMethod()  
    {  
        ...  
    }  
}  
  
class MyDerivedClass : MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    override void VirtualMethod()  
    {  
        ...  
    }  
}  
  
void MethodWithCer(MyClass object)  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    try  
    {  
        ...  
    }  
    finally  
    {  
        // Start of the CER.  
  
        // Cannot tell at analysis time whether object is a MyClass  
        // or a MyDerivedClass, so we do not know which version of   
        // VirtualMethod we are going to call.  
        object.VirtualMethod();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2cd77-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2cd77-118">See Also</span></span>  
 <span data-ttu-id="2cd77-119"><xref:System.Runtime.InteropServices.MarshalAsAttribute></span><span class="sxs-lookup"><span data-stu-id="2cd77-119"><xref:System.Runtime.InteropServices.MarshalAsAttribute></span></span>   
 <span data-ttu-id="2cd77-120">[Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md) </span><span class="sxs-lookup"><span data-stu-id="2cd77-120">[Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md) </span></span>  
 [<span data-ttu-id="2cd77-121">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="2cd77-121">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)

