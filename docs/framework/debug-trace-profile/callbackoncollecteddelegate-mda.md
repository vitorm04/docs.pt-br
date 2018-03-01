---
title: MDA callbackOnCollectedDelegate
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
- cpp
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- managed debugging assistants (MDAs), callback on collected delegates
- MDAs (managed debugging assistants), callback on collected delegates
- callback on delegate after garbage collection
- callbackOnCollectedDelegate MDA
- managed debugging assistants (MDAs), garbage collection
- call back collected delegates
- garbage collection, run-time errors
- delegates [.NET Framework], garbage collection
ms.assetid: 398b0ce0-5cc9-4518-978d-b8263aa21e5b
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5459efbb07aa235bd7c1d34ffd6b56195fe0bf1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="callbackoncollecteddelegate-mda"></a><span data-ttu-id="a3280-102">MDA callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="a3280-102">callbackOnCollectedDelegate MDA</span></span>
<span data-ttu-id="a3280-103">O MDA (assistente para depuração gerenciada) `callbackOnCollectedDelegate` é ativado se um representante tem o marshaling realizado de um código gerenciado para um código não gerenciado como um ponteiro de função e um retorno de chamada é colocado nesse ponteiro de função depois que o representante foi coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="a3280-103">The `callbackOnCollectedDelegate` managed debugging assistant (MDA) is activated if a delegate is marshaled from managed to unmanaged code as a function pointer and a callback is placed on that function pointer after the delegate has been garbage collected.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a3280-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="a3280-104">Symptoms</span></span>  
 <span data-ttu-id="a3280-105">Violações de acesso ocorrem ao tentar chamar o código gerenciado por meio de ponteiros de função que foram obtidos de representantes gerenciados.</span><span class="sxs-lookup"><span data-stu-id="a3280-105">Access violations occur when attempting to call into managed code through function pointers that were obtained from managed delegates.</span></span> <span data-ttu-id="a3280-106">Essas falhas, embora não sejam bugs de CLR (Common Language Runtime), podem parecer ser bugs porque a violação de acesso ocorre no código CLR.</span><span class="sxs-lookup"><span data-stu-id="a3280-106">These failures, while not common language runtime (CLR) bugs, may appear to be so because the access violation occurs in the CLR code.</span></span>  
  
 <span data-ttu-id="a3280-107">A falha não é consistente; às vezes, a chamada no ponteiro de função é bem-sucedida e, às vezes, ela falha.</span><span class="sxs-lookup"><span data-stu-id="a3280-107">The failure is not consistent; sometimes the call on the function pointer succeeds and sometimes it fails.</span></span> <span data-ttu-id="a3280-108">A falha pode ocorrer somente sob carga pesada ou em um número aleatório de tentativas.</span><span class="sxs-lookup"><span data-stu-id="a3280-108">The failure might occur only under heavy load or on a random number of attempts.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a3280-109">Causa</span><span class="sxs-lookup"><span data-stu-id="a3280-109">Cause</span></span>  
 <span data-ttu-id="a3280-110">O representante do qual o ponteiro de função foi criado e exposto ao código não gerenciado foi coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="a3280-110">The delegate from which the function pointer was created and exposed to unmanaged code was garbage collected.</span></span> <span data-ttu-id="a3280-111">Quando o componente não gerenciado tenta chamar no ponteiro de função, ele gera uma violação de acesso.</span><span class="sxs-lookup"><span data-stu-id="a3280-111">When the unmanaged component tries to call on the function pointer, it generates an access violation.</span></span>  
  
 <span data-ttu-id="a3280-112">A falha parece aleatória porque ela depende de quando ocorre a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a3280-112">The failure appears random because it depends on when garbage collection occurs.</span></span> <span data-ttu-id="a3280-113">Se um representante é qualificado para a coleta, a coleta de lixo pode ocorrer após o retorno de chamada e depois que a chamada é bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="a3280-113">If a delegate is eligible for collection, the garbage collection can occur after the callback and the call succeeds.</span></span> <span data-ttu-id="a3280-114">Em outras ocasiões, a coleta de lixo ocorre antes do retorno de chamada, o retorno de chamada gera uma violação de acesso e o programa é interrompido.</span><span class="sxs-lookup"><span data-stu-id="a3280-114">At other times, the garbage collection occurs before the callback, the callback generates an access violation, and the program stops.</span></span>  
  
 <span data-ttu-id="a3280-115">A probabilidade da falha depende do tempo entre o marshaling do representante e o retorno de chamada no ponteiro de função, bem como a frequência das coletas de lixo.</span><span class="sxs-lookup"><span data-stu-id="a3280-115">The probability of the failure depends on the time between marshaling the delegate and the callback on the function pointer as well as the frequency of garbage collections.</span></span> <span data-ttu-id="a3280-116">A falha é esporádica se o tempo entre o marshaling do representante e o retorno de chamada resultante é curto.</span><span class="sxs-lookup"><span data-stu-id="a3280-116">The failure is sporadic if the time between marshaling the delegate and the ensuing callback is short.</span></span> <span data-ttu-id="a3280-117">Esse geralmente é o caso se o método não gerenciado que recebe o ponteiro de função não salva o ponteiro de função para uso posterior, mas em vez disso, realiza uma chamada novamente no ponteiro de função imediatamente para concluir sua operação antes de retornar.</span><span class="sxs-lookup"><span data-stu-id="a3280-117">This is usually the case if the unmanaged method receiving the function pointer does not save the function pointer for later use but instead calls back on the function pointer immediately to complete its operation before returning.</span></span> <span data-ttu-id="a3280-118">Da mesma forma, mais coletas de lixo ocorrem quando um sistema está sob carga pesada, o que torna mais provável que ocorra uma coleta de lixo antes do retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="a3280-118">Similarly, more garbage collections occur when a system is under heavy load, which makes it more likely that a garbage collection will occur before the callback.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a3280-119">Resolução</span><span class="sxs-lookup"><span data-stu-id="a3280-119">Resolution</span></span>  
 <span data-ttu-id="a3280-120">Depois que um representante tem o marshaling realizado como um ponteiro de função não gerenciada, o coletor de lixo não pode acompanhar seu tempo de vida.</span><span class="sxs-lookup"><span data-stu-id="a3280-120">Once a delegate has been marshaled out as an unmanaged function pointer, the garbage collector cannot track its lifetime.</span></span> <span data-ttu-id="a3280-121">Em vez disso, o código deve manter uma referência ao representante durante o tempo de vida do ponteiro de função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="a3280-121">Instead, your code must keep a reference to the delegate for the lifetime of the unmanaged function pointer.</span></span> <span data-ttu-id="a3280-122">Porém, antes de poder fazer isso, primeiro você deve identificar qual representante foi coletado.</span><span class="sxs-lookup"><span data-stu-id="a3280-122">But before you can do that, you first must identify which delegate was collected.</span></span> <span data-ttu-id="a3280-123">Quando o MDA é ativado, ele fornece o nome do tipo do representante.</span><span class="sxs-lookup"><span data-stu-id="a3280-123">When the MDA is activated, it provides the type name of the delegate.</span></span> <span data-ttu-id="a3280-124">Use esse nome para pesquisar o código em busca da invocação de plataforma ou de assinaturas COM que passam o representante para o código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a3280-124">Use this name to search your code for platform invoke or COM signatures that pass that delegate out to unmanaged code.</span></span> <span data-ttu-id="a3280-125">O representante inválido é passado por meio de um desses sites de chamada.</span><span class="sxs-lookup"><span data-stu-id="a3280-125">The offending delegate is passed out through one of these call sites.</span></span> <span data-ttu-id="a3280-126">Você também pode habilitar o MDA `gcUnmanagedToManaged` a forçar uma coleta de lixo antes de cada retorno de chamada no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a3280-126">You can also enable the `gcUnmanagedToManaged` MDA to force a garbage collection before every callback into the runtime.</span></span> <span data-ttu-id="a3280-127">Isso removerá a incerteza introduzida pela coleta de lixo, garantindo que uma coleta de lixo sempre ocorra antes do retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="a3280-127">This will remove the uncertainty introduced by the garbage collection by ensuring that a garbage collection always occurs before the callback.</span></span> <span data-ttu-id="a3280-128">Depois de saber qual representante foi coletado, altere o código para manter uma referência ao representante no lado gerenciado durante o tempo de vida do ponteiro de função não gerenciada com marshaling.</span><span class="sxs-lookup"><span data-stu-id="a3280-128">Once you know what delegate was collected, change your code to keep a reference to that delegate on the managed side for the lifetime of the marshaled unmanaged function pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a3280-129">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="a3280-129">Effect on the Runtime</span></span>  
 <span data-ttu-id="a3280-130">Quando os representantes têm o marshaling realizado como ponteiros de função, o tempo de execução aloca uma conversão que faz a transição do não gerenciado para o gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a3280-130">When delegates are marshaled as function pointers, the runtime allocates a thunk that does the transition from unmanaged to managed.</span></span> <span data-ttu-id="a3280-131">Essa conversão é o que o código não gerenciado, na verdade, chama antes que o representante gerenciado seja finalmente invocado.</span><span class="sxs-lookup"><span data-stu-id="a3280-131">This thunk is what the unmanaged code actually calls before the managed delegate is finally invoked.</span></span> <span data-ttu-id="a3280-132">Sem o MDA `callbackOnCollectedDelegate` habilitado, o código de marshaling não gerenciado é excluído quando o representante é coletado.</span><span class="sxs-lookup"><span data-stu-id="a3280-132">Without the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is deleted when the delegate is collected.</span></span> <span data-ttu-id="a3280-133">Com o MDA `callbackOnCollectedDelegate` habilitado, o código de marshaling não gerenciado não é excluído imediatamente quando o representante é coletado.</span><span class="sxs-lookup"><span data-stu-id="a3280-133">With the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is not immediately deleted when the delegate is collected.</span></span> <span data-ttu-id="a3280-134">Em vez disso, as últimas 1.000 instâncias são mantidas ativas por padrão e alteradas para ativar o MDA quando chamadas.</span><span class="sxs-lookup"><span data-stu-id="a3280-134">Instead, the last 1,000 instances are kept alive by default and changed to activate the MDA when called.</span></span> <span data-ttu-id="a3280-135">A conversão é, no final das contas, excluída depois que 1.001 representantes com marshaling são coletados.</span><span class="sxs-lookup"><span data-stu-id="a3280-135">The thunk is eventually deleted after 1,001 more marshaled delegates are collected.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a3280-136">Saída</span><span class="sxs-lookup"><span data-stu-id="a3280-136">Output</span></span>  
 <span data-ttu-id="a3280-137">O MDA relata o nome do tipo do representante que foi coletado antes da tentativa de um retorno de chamada em seu ponteiro de função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="a3280-137">The MDA reports the type name of the delegate that was collected before a callback was attempted on its unmanaged function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a3280-138">Configuração</span><span class="sxs-lookup"><span data-stu-id="a3280-138">Configuration</span></span>  
 <span data-ttu-id="a3280-139">O exemplo a seguir mostra as opções de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a3280-139">The following example shows the application configuration options.</span></span> <span data-ttu-id="a3280-140">Ele define o número de conversões que o MDA mantém ativas como 1.500.</span><span class="sxs-lookup"><span data-stu-id="a3280-140">It sets the number of thunks the MDA keeps alive to 1,500.</span></span> <span data-ttu-id="a3280-141">O valor padrão `listSize` é 1.000, o mínimo é 50 e o máximo é 2.000.</span><span class="sxs-lookup"><span data-stu-id="a3280-141">The default `listSize` value is 1,000, the minimum is 50, and the maximum is 2,000.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="a3280-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a3280-142">Example</span></span>  
 <span data-ttu-id="a3280-143">O seguinte exemplo demonstra uma situação que pode ativar esse MDA:</span><span class="sxs-lookup"><span data-stu-id="a3280-143">The following example demonstrates a situation that can activate this MDA:</span></span>  
  
```  
// Library.cpp : Defines the unmanaged entry point for the DLL application.  
#include "windows.h"  
#include "stdio.h"  
  
void (__stdcall *g_pfTarget)();  
  
void __stdcall Initialize(void __stdcall pfTarget())  
{  
    g_pfTarget = pfTarget;  
}  
  
void __stdcall Callback()  
{  
    g_pfTarget();  
}  
// ---------------------------------------------------  
// C# Client  
using System;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public delegate void DCallback();  
  
    public static void Main()  
    {  
        new Entry();  
        Initialize(Target);  
        GC.Collect();  
        GC.WaitForPendingFinalizers();  
        Callback();  
    }  
  
    public static void Target()  
    {          
    }  
  
    [DllImport("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Initialize(DCallback pfDelegate);  
  
    [DllImport ("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Callback();  
  
    ~Entry() { Console.Error.WriteLine("Entry Collected"); }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3280-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3280-144">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="a3280-145">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="a3280-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="a3280-146">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="a3280-146">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)  
 [<span data-ttu-id="a3280-147">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="a3280-147">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
