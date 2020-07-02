---
title: MDA virtualCERCall
description: Examine o MDA (Assistente de depuração gerenciada) virtualCERCall, que é invocado se uma CER contém uma chamada para um método virtual que não pode ser preparado automaticamente.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- virtualCERCall MDA
- virtual CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
ms.openlocfilehash: fab0686b1c7d2fbb1485f6e4b82d008495a553cd
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803554"
---
# <a name="virtualcercall-mda"></a><span data-ttu-id="1d9b6-103">MDA virtualCERCall</span><span class="sxs-lookup"><span data-stu-id="1d9b6-103">virtualCERCall MDA</span></span>
<span data-ttu-id="1d9b6-104">O MDA (assistente para depuração gerenciada) `virtualCERCall` é ativado como um aviso, indicando que um site de chamada em um gráfico de chamadas da CER (região de execução restrita) se refere a um destino virtual, ou seja, uma chamada virtual a um método virtual não final ou uma chamada usando uma interface.</span><span class="sxs-lookup"><span data-stu-id="1d9b6-104">The `virtualCERCall` managed debugging assistant (MDA) is activated as a warning indicating that a call site within a constrained execution region (CER) call graph refers to a virtual target, that is, a virtual call to a non-final virtual method or a call using an interface.</span></span> <span data-ttu-id="1d9b6-105">O CLR (Common Language Runtime) não pode prever o método de destino dessas chamadas pela análise de metadados e de linguagem intermediária apenas.</span><span class="sxs-lookup"><span data-stu-id="1d9b6-105">The common language runtime (CLR) cannot predict the destination method of these calls from the intermediate language and metadata analysis alone.</span></span> <span data-ttu-id="1d9b6-106">Como resultado, a árvore de chamadas não pode ser preparada como parte do gráfico da CER e as anulações de thread nessa subárvore não podem ser bloqueadas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="1d9b6-106">As a result, the call tree cannot be prepared as part of the CER graph and thread aborts in that subtree cannot be automatically blocked.</span></span> <span data-ttu-id="1d9b6-107">Esse MDA avisa sobre casos em que uma CER talvez precise ser estendida usando chamadas explícitas ao método <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> depois que as informações adicionais necessárias para calcular o destino de chamada são conhecidas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="1d9b6-107">This MDA warns of cases where a CER might need to be extended by using explicit calls to the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method once the additional information required to compute the call target is known at run time.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1d9b6-108">Sintomas</span><span class="sxs-lookup"><span data-stu-id="1d9b6-108">Symptoms</span></span>  
 <span data-ttu-id="1d9b6-109">As CERs não são executadas quando um thread é anulado ou um domínio do aplicativo é descarregado.</span><span class="sxs-lookup"><span data-stu-id="1d9b6-109">CERs that do not run when a thread is aborted or an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1d9b6-110">Causa</span><span class="sxs-lookup"><span data-stu-id="1d9b6-110">Cause</span></span>  
 <span data-ttu-id="1d9b6-111">Uma CER contém uma chamada a um método virtual que não pode ser preparado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="1d9b6-111">A CER contains a call to a virtual method that cannot be prepared automatically.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1d9b6-112">Resolução</span><span class="sxs-lookup"><span data-stu-id="1d9b6-112">Resolution</span></span>  
 <span data-ttu-id="1d9b6-113">Chame <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> para o método virtual.</span><span class="sxs-lookup"><span data-stu-id="1d9b6-113">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> for the virtual method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1d9b6-114">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="1d9b6-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="1d9b6-115">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="1d9b6-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1d9b6-116">Saída</span><span class="sxs-lookup"><span data-stu-id="1d9b6-116">Output</span></span>  
  
```output
Method 'MethodWithCer', while executing within a constrained execution region, makes a call  
at IL offset 0x0024 to 'VirtualMethod', which is virtual and cannot be prepared automatically  
at compile time. The caller must ensure this method is prepared explicitly at  
runtime before entering the constrained execution region.  
method name="VirtualMethod"  
declaringType name="VirtualCERCall+MyClass"  
  declaringModule name="mda"  
    callsite name="MethodWithCer" offset="0x0024"  
```  
  
## <a name="configuration"></a><span data-ttu-id="1d9b6-117">Configuração</span><span class="sxs-lookup"><span data-stu-id="1d9b6-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="1d9b6-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1d9b6-118">Example</span></span>  
  
```csharp
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
  
## <a name="see-also"></a><span data-ttu-id="1d9b6-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="1d9b6-119">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="1d9b6-120">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="1d9b6-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="1d9b6-121">Realizando marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="1d9b6-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
