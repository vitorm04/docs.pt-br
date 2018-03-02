---
title: "Exceções em threads gerenciados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET Framework],unhandled exceptions
- threading [.NET Framework],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4f68a7aebdb1625b149287d70fd91c2108a658b9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="exceptions-in-managed-threads"></a><span data-ttu-id="00138-102">Exceções em threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="00138-102">Exceptions in Managed Threads</span></span>
<span data-ttu-id="00138-103">A partir do .NET Framework versão 2.0, o common language runtime permite que a maioria das exceções sem tratamento em threads prossiga naturalmente.</span><span class="sxs-lookup"><span data-stu-id="00138-103">Starting with the .NET Framework version 2.0, the common language runtime allows most unhandled exceptions in threads to proceed naturally.</span></span> <span data-ttu-id="00138-104">Na maioria dos casos, isso significa que a exceção sem tratamento causa o encerramento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00138-104">In most cases this means that the unhandled exception causes the application to terminate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00138-105">Essa é uma alteração significativa das versões do .NET Framework 1.0 e 1.1, que fornece uma barreira para várias exceções sem tratamento, por exemplo, exceção sem tratamento em threads de pool de threads.</span><span class="sxs-lookup"><span data-stu-id="00138-105">This is a significant change from the .NET Framework versions 1.0 and 1.1, which provide a backstop for many unhandled exceptions — for example, unhandled exceptions in thread pool threads.</span></span> <span data-ttu-id="00138-106">Confira [Alterar de versões anteriores](#ChangeFromPreviousVersions) mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="00138-106">See [Change from Previous Versions](#ChangeFromPreviousVersions) later in this topic.</span></span>  
  
 <span data-ttu-id="00138-107">O common language runtime fornece uma barreira para certas exceções sem tratamento que são usados para controlar o fluxo do programa:</span><span class="sxs-lookup"><span data-stu-id="00138-107">The common language runtime provides a backstop for certain unhandled exceptions that are used for controlling program flow:</span></span>  
  
-   <span data-ttu-id="00138-108">Uma <xref:System.Threading.ThreadAbortException> é gerada em um thread porque <xref:System.Threading.Thread.Abort%2A> foi chamado.</span><span class="sxs-lookup"><span data-stu-id="00138-108">A <xref:System.Threading.ThreadAbortException> is thrown in a thread because <xref:System.Threading.Thread.Abort%2A> was called.</span></span>  
  
-   <span data-ttu-id="00138-109">Um <xref:System.AppDomainUnloadedException> é gerado em um thread, pois o domínio do aplicativo no qual o thread está em execução está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="00138-109">An <xref:System.AppDomainUnloadedException> is thrown in a thread because the application domain in which the thread is executing is being unloaded.</span></span>  
  
-   <span data-ttu-id="00138-110">O Common Language Runtime ou um processo de host encerra o thread lançando uma exceção interna.</span><span class="sxs-lookup"><span data-stu-id="00138-110">The common language runtime or a host process terminates the thread by throwing an internal exception.</span></span>  
  
 <span data-ttu-id="00138-111">Se qualquer uma dessas exceções não tiver tratamento em threads criados pelo common language runtime, a exceção encerrará o thread, mas o common language runtime não permitirá que a exceção prossiga.</span><span class="sxs-lookup"><span data-stu-id="00138-111">If any of these exceptions are unhandled in threads created by the common language runtime, the exception terminates the thread, but the common language runtime does not allow the exception to proceed further.</span></span>  
  
 <span data-ttu-id="00138-112">Se essas exceções não tiverem tratamento no thread principal, ou em threads que entraram no runtime a partir do código não gerenciado, elas prosseguirão normalmente, resultando no encerramento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00138-112">If these exceptions are unhandled in the main thread, or in threads that entered the runtime from unmanaged code, they proceed normally, resulting in termination of the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00138-113">É possível que o runtime lance uma exceção não tratada antes que qualquer código gerenciado tenha a oportunidade de instalar um manipulador de exceção.</span><span class="sxs-lookup"><span data-stu-id="00138-113">It is possible for the runtime to throw an unhandled exception before any managed code has had a chance to install an exception handler.</span></span> <span data-ttu-id="00138-114">Mesmo que o código gerenciado não tivesse possibilidade de manipular essa exceção, a exceção recebe a permissão para prosseguir naturalmente.</span><span class="sxs-lookup"><span data-stu-id="00138-114">Even though managed code had no chance to handle such an exception, the exception is allowed to proceed naturally.</span></span>  
  
## <a name="exposing-threading-problems-during-development"></a><span data-ttu-id="00138-115">Exposição de problemas de threading durante o desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="00138-115">Exposing Threading Problems During Development</span></span>  
 <span data-ttu-id="00138-116">Quando os threads recebem a permissão para falhar em modo silencioso, sem encerrar o aplicativo, problemas graves de programação podem passar sem detecção.</span><span class="sxs-lookup"><span data-stu-id="00138-116">When threads are allowed to fail silently, without terminating the application, serious programming problems can go undetected.</span></span> <span data-ttu-id="00138-117">Este é um problema específico para serviços e outros aplicativos executados por longos períodos.</span><span class="sxs-lookup"><span data-stu-id="00138-117">This is a particular problem for services and other applications which run for extended periods.</span></span> <span data-ttu-id="00138-118">À medida que os threads falham, o estado do programa se torna cada vez mais corrompido.</span><span class="sxs-lookup"><span data-stu-id="00138-118">As threads fail, program state gradually becomes corrupted.</span></span> <span data-ttu-id="00138-119">O desempenho do aplicativo pode piorar, ou o aplicativo pode travar.</span><span class="sxs-lookup"><span data-stu-id="00138-119">Application performance may degrade, or the application might hang.</span></span>  
  
 <span data-ttu-id="00138-120">Permitir que exceções sem tratamento em threads prossigam naturalmente, até que o sistema operacional encerre o programa, expõe esses problemas durante o desenvolvimento e teste.</span><span class="sxs-lookup"><span data-stu-id="00138-120">Allowing unhandled exceptions in threads to proceed naturally, until the operating system terminates the program, exposes such problems during development and testing.</span></span> <span data-ttu-id="00138-121">Relatórios de erros em depuração de suporte de encerramentos do programa.</span><span class="sxs-lookup"><span data-stu-id="00138-121">Error reports on program terminations support debugging.</span></span>  
  
<a name="ChangeFromPreviousVersions"></a>   
## <a name="change-from-previous-versions"></a><span data-ttu-id="00138-122">Alterar de versões anteriores</span><span class="sxs-lookup"><span data-stu-id="00138-122">Change from Previous Versions</span></span>  
 <span data-ttu-id="00138-123">A alteração mais significativa se refere aos threads gerenciados.</span><span class="sxs-lookup"><span data-stu-id="00138-123">The most significant change pertains to managed threads.</span></span> <span data-ttu-id="00138-124">Nas versões do .NET Framework 1.0 e 1.1, o CLR fornece uma barreira para exceções sem tratamento nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="00138-124">In the .NET Framework versions 1.0 and 1.1, the common language runtime provides a backstop for unhandled exceptions in the following situations:</span></span>  
  
-   <span data-ttu-id="00138-125">Não existe exceção sem tratamento em um thread de pool de threads.</span><span class="sxs-lookup"><span data-stu-id="00138-125">There is no such thing as an unhandled exception on a thread pool thread.</span></span> <span data-ttu-id="00138-126">Quando uma tarefa gera uma exceção sem tratamento, o runtime imprime o rastreamento de pilha da exceção para o console e, depois, retorna o thread para o pool de threads.</span><span class="sxs-lookup"><span data-stu-id="00138-126">When a task throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then returns the thread to the thread pool.</span></span>  
  
-   <span data-ttu-id="00138-127">Não existe exceção sem tratamento em um thread criado com o método <xref:System.Threading.Thread.Start%2A> da classe <xref:System.Threading.Thread>.</span><span class="sxs-lookup"><span data-stu-id="00138-127">There is no such thing as an unhandled exception on a thread created with the <xref:System.Threading.Thread.Start%2A> method of the <xref:System.Threading.Thread> class.</span></span> <span data-ttu-id="00138-128">Quando um código em execução em um thread como esse gera uma exceção sem tratamento, o runtime imprime o rastreamento de pilha da exceção para o console e, depois, encerra normalmente o thread.</span><span class="sxs-lookup"><span data-stu-id="00138-128">When code running on such a thread throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then gracefully terminates the thread.</span></span>  
  
-   <span data-ttu-id="00138-129">Não existe exceção sem tratamento no thread finalizador.</span><span class="sxs-lookup"><span data-stu-id="00138-129">There is no such thing as an unhandled exception on the finalizer thread.</span></span> <span data-ttu-id="00138-130">Quando um finalizar gera uma exceção sem tratamento, o runtime imprime o rastreamento de pilha da exceção para o console e, depois, permite que o thread finalizador retome a execução dos finalizadores.</span><span class="sxs-lookup"><span data-stu-id="00138-130">When a finalizer throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then allows the finalizer thread to resume running finalizers.</span></span>  
  
 <span data-ttu-id="00138-131">O status de primeiro plano ou segundo plano de um thread gerenciado não afeta esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="00138-131">The foreground or background status of a managed thread does not affect this behavior.</span></span>  
  
 <span data-ttu-id="00138-132">Para as exceções sem tratamento em threads com origem em código não gerenciado, a diferença é mais sutil.</span><span class="sxs-lookup"><span data-stu-id="00138-132">For unhandled exceptions on threads originating in unmanaged code, the difference is more subtle.</span></span> <span data-ttu-id="00138-133">A caixa de diálogo de anexação JIT do runtime impede a caixa de diálogo do sistema operacional para exceções gerenciadas ou exceções nativas em threads que passaram por código nativo.</span><span class="sxs-lookup"><span data-stu-id="00138-133">The runtime JIT-attach dialog preempts the operating system dialog for managed exceptions or native exceptions on threads that have passed through native code.</span></span> <span data-ttu-id="00138-134">O processo é encerrado em todos os casos.</span><span class="sxs-lookup"><span data-stu-id="00138-134">The process terminates in all cases.</span></span>  
  
### <a name="migrating-code"></a><span data-ttu-id="00138-135">Migrar o código</span><span class="sxs-lookup"><span data-stu-id="00138-135">Migrating Code</span></span>  
 <span data-ttu-id="00138-136">Em geral, a alteração vai expor problemas de programação não reconhecidos anteriormente, para que possam ser corrigidos.</span><span class="sxs-lookup"><span data-stu-id="00138-136">In general, the change will expose previously unrecognized programming problems so that they can be fixed.</span></span> <span data-ttu-id="00138-137">No entanto, em alguns casos, os programadores podem ter aproveitado a barreira do runtime, por exemplo, para encerrar threads.</span><span class="sxs-lookup"><span data-stu-id="00138-137">In some cases, however, programmers might have taken advantage of the runtime backstop, for example to terminate threads.</span></span> <span data-ttu-id="00138-138">Dependendo da situação, eles devem considerar uma das seguintes estratégias de migração:</span><span class="sxs-lookup"><span data-stu-id="00138-138">Depending on the situation, they should consider one of the following migration strategies:</span></span>  
  
-   <span data-ttu-id="00138-139">Reestruturar o código para que o thread feche normalmente quando receber um sinal.</span><span class="sxs-lookup"><span data-stu-id="00138-139">Restructure the code so the thread exits gracefully when a signal is received.</span></span>  
  
-   <span data-ttu-id="00138-140">Use o método <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> para anular o thread.</span><span class="sxs-lookup"><span data-stu-id="00138-140">Use the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method to abort the thread.</span></span>  
  
-   <span data-ttu-id="00138-141">Se um thread precisar ser interrompido para que o encerramento do processo possa continuar, torne o thread um thread em segundo plano para que ela seja encerrado automaticamente no encerramento do processo.</span><span class="sxs-lookup"><span data-stu-id="00138-141">If a thread must be stopped so that process termination can proceed, make the thread a background thread so that it is automatically terminated on process exit.</span></span>  
  
 <span data-ttu-id="00138-142">Em todos os casos, a estratégia deve seguir as diretrizes de design para exceções.</span><span class="sxs-lookup"><span data-stu-id="00138-142">In all cases, the strategy should follow the design guidelines for exceptions.</span></span> <span data-ttu-id="00138-143">Confira [Diretrizes de design para exceções](../../../docs/standard/design-guidelines/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="00138-143">See [Design Guidelines for Exceptions](../../../docs/standard/design-guidelines/exceptions.md).</span></span>  
  
### <a name="application-compatibility-flag"></a><span data-ttu-id="00138-144">Sinalizador de compatibilidade de aplicativos</span><span class="sxs-lookup"><span data-stu-id="00138-144">Application Compatibility Flag</span></span>  
 <span data-ttu-id="00138-145">Como uma medida temporária de compatibilidade, os administradores podem colocar um sinalizador de compatibilidade na seção `<runtime>` do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00138-145">As a temporary compatibility measure, administrators can place a compatibility flag in the `<runtime>` section of the application configuration file.</span></span> <span data-ttu-id="00138-146">Isso faz com que o common language runtime reverta para o comportamento das versões 1.0 e 1.1.</span><span class="sxs-lookup"><span data-stu-id="00138-146">This causes the common language runtime to revert to the behavior of versions 1.0 and 1.1.</span></span>  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a><span data-ttu-id="00138-147">Substituição do host</span><span class="sxs-lookup"><span data-stu-id="00138-147">Host Override</span></span>  
 <span data-ttu-id="00138-148">No .NET Framework versão 2.0, um host não gerenciado pode usar a interface [ICLRPolicyManager](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) na API de hospedagem para substituir a política de exceções sem tratamento padrão do common language runtime.</span><span class="sxs-lookup"><span data-stu-id="00138-148">In the .NET Framework version 2.0, an unmanaged host can use the [ICLRPolicyManager](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface in the Hosting API to override the default unhandled exception policy of the common language runtime.</span></span> <span data-ttu-id="00138-149">A função [ICLRPolicyManager::SetUnhandledExceptionPolicy](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) é usada para definir a política para exceções sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="00138-149">The [ICLRPolicyManager::SetUnhandledExceptionPolicy](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) function is used to set the policy for unhandled exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00138-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00138-150">See Also</span></span>  
 [<span data-ttu-id="00138-151">Noções básicas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="00138-151">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)
