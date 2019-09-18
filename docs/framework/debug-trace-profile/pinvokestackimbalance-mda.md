---
title: MDA pInvokeStackImbalance
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dc4a48c79fc39b12f8231bd913b4ca8970c0f46f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052363"
---
# <a name="pinvokestackimbalance-mda"></a><span data-ttu-id="34670-102">MDA PInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="34670-102">PInvokeStackImbalance MDA</span></span>

<span data-ttu-id="34670-103">O `PInvokeStackImbalance` MDA (Assistente de depuração gerenciada) é ativado quando o CLR detecta que a profundidade da pilha após uma chamada de invocação de plataforma não corresponde à profundidade de pilha esperada, <xref:System.Runtime.InteropServices.DllImportAttribute> Considerando a Convenção de chamada especificada no atributo e o Declaração dos parâmetros na assinatura gerenciada.</span><span class="sxs-lookup"><span data-stu-id="34670-103">The `PInvokeStackImbalance` managed debugging assistant (MDA) is activated when the CLR detects that the stack depth after a platform invoke call does not match the expected stack depth, given the calling convention specified in the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute and the declaration of the parameters in the managed signature.</span></span>

<span data-ttu-id="34670-104">O MDA `PInvokeStackImbalance` é implementado somente para plataformas x86 de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="34670-104">The `PInvokeStackImbalance` MDA is implemented only for 32-bit x86 platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="34670-105">O `PInvokeStackImbalance` MDA é desabilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="34670-105">The `PInvokeStackImbalance` MDA is disabled by default.</span></span> <span data-ttu-id="34670-106">No Visual Studio 2017, o `PInvokeStackImbalance` MDA aparece na lista **de assistentes de depuração gerenciada** na caixa de diálogo **configurações de exceção** (que é exibida quando você seleciona**janelas**  >   >  **de depuração Configurações de exceção**).</span><span class="sxs-lookup"><span data-stu-id="34670-106">In Visual Studio 2017, The `PInvokeStackImbalance` MDA appears in the **Managed Debugging Assistants** list in the **Exception Settings** dialog box (which is displayed when you select **Debug** > **Windows** > **Exception Settings**).</span></span> <span data-ttu-id="34670-107">No entanto, marcar ou desmarcar a caixa de seleção **interromper quando lançados** não habilitará ou desabilitará o MDA; Ele apenas controla se o Visual Studio lança uma exceção quando o MDA é ativado.</span><span class="sxs-lookup"><span data-stu-id="34670-107">However, selecting or clearing the **Break When Thrown** check box does not enable or disable the MDA; it only controls whether Visual Studio throws an exception when the MDA is activated.</span></span>

## <a name="symptoms"></a><span data-ttu-id="34670-108">Sintomas</span><span class="sxs-lookup"><span data-stu-id="34670-108">Symptoms</span></span>

<span data-ttu-id="34670-109">Um aplicativo encontra uma violação de acesso ou uma corrupção de memória ao fazer uma chamada de invocação de plataforma ou em seguida a ela.</span><span class="sxs-lookup"><span data-stu-id="34670-109">An application encounters an access violation or memory corruption when making or following a platform invoke call.</span></span>

## <a name="cause"></a><span data-ttu-id="34670-110">Causa</span><span class="sxs-lookup"><span data-stu-id="34670-110">Cause</span></span>

<span data-ttu-id="34670-111">A assinatura gerenciada da chamada de invocação de plataforma pode não corresponder à assinatura não gerenciada do método que está sendo chamado.</span><span class="sxs-lookup"><span data-stu-id="34670-111">The managed signature of the platform invoke call might not match the unmanaged signature of the method being called.</span></span>  <span data-ttu-id="34670-112">Essa incompatibilidade pode ser causada devido à assinatura gerenciada não declarar o número correto de parâmetros ou não especificar o tamanho apropriado para eles.</span><span class="sxs-lookup"><span data-stu-id="34670-112">This mismatch can be caused by the managed signature not declaring the correct number of parameters or not specifying the appropriate size for the parameters.</span></span>  <span data-ttu-id="34670-113">O MDA também pode ser ativado porque a convenção de chamada, possivelmente especificada pelo atributo <xref:System.Runtime.InteropServices.DllImportAttribute>, não corresponde à convenção de chamada não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="34670-113">The MDA can also activate because the calling convention, possibly specified by the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute, does not match the unmanaged calling convention.</span></span>

## <a name="resolution"></a><span data-ttu-id="34670-114">Resolução</span><span class="sxs-lookup"><span data-stu-id="34670-114">Resolution</span></span>

<span data-ttu-id="34670-115">Examine a assinatura de invocação e convenção de chamada da plataforma gerenciada para confirmar que ela corresponde à assinatura e convenção de chamada do destino nativo.</span><span class="sxs-lookup"><span data-stu-id="34670-115">Review the managed platform invoke signature and calling convention to confirm it matches the signature and calling convention of the native target.</span></span>  <span data-ttu-id="34670-116">Tente especificar explicitamente a convenção de chamada tanto no lado gerenciado quanto no não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="34670-116">Try explicitly specifying the calling convention on both the managed and unmanaged sides.</span></span> <span data-ttu-id="34670-117">Também é possível, embora mais improvável, que a função não gerenciada tenha desequilibrado a pilha por algum outro motivo, assim como um bug no compilador não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="34670-117">It is also possible, although not as likely, that the unmanaged function unbalanced the stack for some other reason, such as a bug in the unmanaged compiler.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="34670-118">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="34670-118">Effect on the Runtime</span></span>

<span data-ttu-id="34670-119">Força todas as chamadas de invocação de plataforma a usar o caminho não otimizado no CLR.</span><span class="sxs-lookup"><span data-stu-id="34670-119">Forces all platform invoke calls to take the nonoptimized path in the CLR.</span></span>

## <a name="output"></a><span data-ttu-id="34670-120">Saída</span><span class="sxs-lookup"><span data-stu-id="34670-120">Output</span></span>

<span data-ttu-id="34670-121">A mensagem MDA fornece o nome da chamada de método de invocação de plataforma que está causando o desequilíbrio na pilha.</span><span class="sxs-lookup"><span data-stu-id="34670-121">The MDA message gives the name of the platform invoke method call that is causing the stack imbalance.</span></span> <span data-ttu-id="34670-122">Uma mensagem de exemplo de uma chamada de invocação de plataforma no método `SampleMethod` é:</span><span class="sxs-lookup"><span data-stu-id="34670-122">A sample message of a platform invoke call on method `SampleMethod` is:</span></span>

<span data-ttu-id="34670-123">**Uma chamada para a função PInvoke ' SampleMethod ' desbalanceou a pilha. Isso é provável porque a assinatura do PInvoke gerenciada não corresponde à assinatura de destino não gerenciada. Verifique se a Convenção de chamada e os parâmetros da assinatura PInvoke correspondem à assinatura não gerenciada de destino.**</span><span class="sxs-lookup"><span data-stu-id="34670-123">**A call to PInvoke function 'SampleMethod' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="configuration"></a><span data-ttu-id="34670-124">Configuração</span><span class="sxs-lookup"><span data-stu-id="34670-124">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="34670-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34670-125">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="34670-126">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="34670-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="34670-127">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="34670-127">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
