---
title: MDA contextSwitchDeadlock
description: Leia sobre o MDA (Assistente de depuração gerenciada) do contextSwitchDeadlock no .NET, que é ativado quando um deadlock é detectado durante uma transição de contexto COM.
ms.date: 03/30/2017
helpviewer_keywords:
- deadlocks [.NET Framework]
- pumping messages
- STA message pumping
- single-threaded COM components
- MDAs (managed debugging assistants), context switching deadlocks
- managed debugging assistants (MDAs), context switching deadlocks
- ContextSwitchDeadlock MDA
- message pumping
- context switching deadlocks
ms.assetid: 26dfaa15-9ddb-4b0a-b6da-999bba664fa6
ms.openlocfilehash: 52db4f2c88bac4e8cac621cca989fa10acb43f94
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416012"
---
# <a name="contextswitchdeadlock-mda"></a><span data-ttu-id="c8109-103">MDA contextSwitchDeadlock</span><span class="sxs-lookup"><span data-stu-id="c8109-103">contextSwitchDeadlock MDA</span></span>

<span data-ttu-id="c8109-104">O MDA (assistente para depuração gerenciada) `contextSwitchDeadlock` é ativado quando um deadlock é detectado durante uma tentativa de transição de contexto COM.</span><span class="sxs-lookup"><span data-stu-id="c8109-104">The `contextSwitchDeadlock` managed debugging assistant (MDA) is activated when a deadlock is detected during an attempted COM context transition.</span></span>

## <a name="symptoms"></a><span data-ttu-id="c8109-105">Sintomas</span><span class="sxs-lookup"><span data-stu-id="c8109-105">Symptoms</span></span>

<span data-ttu-id="c8109-106">O sintoma mais comum é que uma chamada em um componente COM não gerenciado de um código gerenciado não retorna.</span><span class="sxs-lookup"><span data-stu-id="c8109-106">The most common symptom is that a call on an unmanaged COM component from managed code does not return.</span></span>  <span data-ttu-id="c8109-107">Outro sintoma é que o uso da memória aumenta com o tempo.</span><span class="sxs-lookup"><span data-stu-id="c8109-107">Another symptom is memory usage increasing over time.</span></span>

## <a name="cause"></a><span data-ttu-id="c8109-108">Causa</span><span class="sxs-lookup"><span data-stu-id="c8109-108">Cause</span></span>

<span data-ttu-id="c8109-109">A causa mais provável é que um thread de STA (single-threaded apartment) não está bombeando as mensagens.</span><span class="sxs-lookup"><span data-stu-id="c8109-109">The most probable cause is that a single-threaded apartment (STA) thread is not pumping messages.</span></span> <span data-ttu-id="c8109-110">O thread de STA está esperando sem bombear as mensagens ou está realizando operações longas e não está permitindo o bombeamento da fila de mensagens.</span><span class="sxs-lookup"><span data-stu-id="c8109-110">The STA thread is either waiting without pumping messages or is performing lengthy operations and is not allowing the message queue to pump.</span></span>

<span data-ttu-id="c8109-111">O aumento do uso da memória com o tempo é causado por uma tentativa do thread do finalizador de chamar `Release` em um componente COM não gerenciado e pela falta de retorno desse componente.</span><span class="sxs-lookup"><span data-stu-id="c8109-111">Memory usage increasing over time is caused by the finalizer thread attempting to call `Release` on an unmanaged COM component and that component is not returning.</span></span>  <span data-ttu-id="c8109-112">Isso impede que o finalizador recupere outros objetos.</span><span class="sxs-lookup"><span data-stu-id="c8109-112">This prevents the finalizer from reclaiming other objects.</span></span>

<span data-ttu-id="c8109-113">Por padrão, STA é o modelo de threading para o thread principal dos aplicativos do console do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c8109-113">By default, the threading model for the main thread of Visual Basic console applications is STA.</span></span> <span data-ttu-id="c8109-114">Esse MDA é ativado se um thread de STA usar a interoperabilidade de COM direta ou indiretamente por meio do Common Language Runtime ou de um controle de terceiros.</span><span class="sxs-lookup"><span data-stu-id="c8109-114">This MDA is activated if an STA thread uses COM interoperability either directly or indirectly through the common language runtime or a third-party control.</span></span>  <span data-ttu-id="c8109-115">Para evitar a ativação desse MDA em um aplicativo do console do Visual Basic, aplique o atributo <xref:System.MTAThreadAttribute> ao método principal ou modifique o aplicativo para bombear as mensagens.</span><span class="sxs-lookup"><span data-stu-id="c8109-115">To avoid activating this MDA in a Visual Basic console application, apply the <xref:System.MTAThreadAttribute> attribute to the main method or modify the application to pump messages.</span></span>

<span data-ttu-id="c8109-116">É possível que esse MDA seja ativado erroneamente quando todas as condições a seguir forem atendidas:</span><span class="sxs-lookup"><span data-stu-id="c8109-116">It is possible for this MDA to be falsely activated when all of the following conditions are met:</span></span>

- <span data-ttu-id="c8109-117">Um aplicativo cria componentes COM de threads de STA direta ou indiretamente por meio das bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="c8109-117">An application creates COM components from STA threads either directly or indirectly through libraries.</span></span>

- <span data-ttu-id="c8109-118">O aplicativo foi interrompido no depurador e o usuário continuou o aplicativo ou realizou uma operação de etapa.</span><span class="sxs-lookup"><span data-stu-id="c8109-118">The application was stopped in the debugger and the user either continued the application or performed a step operation.</span></span>

- <span data-ttu-id="c8109-119">A depuração não gerenciada não está habilitada.</span><span class="sxs-lookup"><span data-stu-id="c8109-119">Unmanaged debugging is not enabled.</span></span>

<span data-ttu-id="c8109-120">Para determinar se o MDA está sendo ativado erroneamente, desabilite todos os pontos de interrupção, reinicie o aplicativo e permita que ele seja executado sem parar.</span><span class="sxs-lookup"><span data-stu-id="c8109-120">To determine if the MDA is being falsely activated, disable all breakpoints, restart the application, and allow it to run without stopping.</span></span> <span data-ttu-id="c8109-121">Se o MDA não for ativado, é provável que a ativação inicial era falsa.</span><span class="sxs-lookup"><span data-stu-id="c8109-121">If the MDA is not activated, it is likely the initial activation was false.</span></span> <span data-ttu-id="c8109-122">Nesse caso, desabilite o MDA para evitar interferências na sessão de depuração.</span><span class="sxs-lookup"><span data-stu-id="c8109-122">In this case, disable the MDA to avoid interference with the debugging session.</span></span>

> [!NOTE]
> <span data-ttu-id="c8109-123">Este MDA está no conjunto padrão para o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c8109-123">This MDA is in the default set for Visual Studio.</span></span> <span data-ttu-id="c8109-124">Para obter informações sobre como desabilitar o MDAs, consulte [diagnosticando erros com assistentes de depuração gerenciada](diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span><span class="sxs-lookup"><span data-stu-id="c8109-124">For information about how to disable MDAs, see [Diagnosing Errors with Managed Debugging Assistants](diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span></span>

## <a name="resolution"></a><span data-ttu-id="c8109-125">Resolução</span><span class="sxs-lookup"><span data-stu-id="c8109-125">Resolution</span></span>

<span data-ttu-id="c8109-126">Siga as regras de COM em relação ao bombeamento das mensagens de STA.</span><span class="sxs-lookup"><span data-stu-id="c8109-126">Follow COM rules regarding STA message pumping.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="c8109-127">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="c8109-127">Effect on the Runtime</span></span>

<span data-ttu-id="c8109-128">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="c8109-128">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="c8109-129">Ele apenas relata dados sobre contextos de COM.</span><span class="sxs-lookup"><span data-stu-id="c8109-129">It only reports data about COM contexts.</span></span>

## <a name="output"></a><span data-ttu-id="c8109-130">Saída</span><span class="sxs-lookup"><span data-stu-id="c8109-130">Output</span></span>

<span data-ttu-id="c8109-131">Uma mensagem descrevendo o contexto atual e o contexto de destino.</span><span class="sxs-lookup"><span data-stu-id="c8109-131">A message describing the current context and the target context.</span></span>

## <a name="configuration"></a><span data-ttu-id="c8109-132">Configuração</span><span class="sxs-lookup"><span data-stu-id="c8109-132">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <contextSwitchDeadlock />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="c8109-133">Veja também</span><span class="sxs-lookup"><span data-stu-id="c8109-133">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="c8109-134">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="c8109-134">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c8109-135">Realizando marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="c8109-135">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
