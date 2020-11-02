---
title: Exceções em threads gerenciados
description: Veja como as exceções não tratadas são tratadas no .NET. A maioria das exceções de thread sem tratamento prossegue naturalmente e leva ao encerramento do aplicativo.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET],unhandled exceptions
- threading [.NET],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
ms.openlocfilehash: b7cf7e94156eedc82c7ec5c863ee013b75d22e73
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188322"
---
# <a name="exceptions-in-managed-threads"></a><span data-ttu-id="8bec9-104">Exceções em threads gerenciados</span><span class="sxs-lookup"><span data-stu-id="8bec9-104">Exceptions in managed threads</span></span>

<span data-ttu-id="8bec9-105">O Common Language Runtime permite que a maioria das exceções não tratadas em threads prossiga naturalmente.</span><span class="sxs-lookup"><span data-stu-id="8bec9-105">The common language runtime allows most unhandled exceptions in threads to proceed naturally.</span></span> <span data-ttu-id="8bec9-106">Na maioria dos casos, isso significa que a exceção sem tratamento causa o encerramento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8bec9-106">In most cases this means that the unhandled exception causes the application to terminate.</span></span>
  
<span data-ttu-id="8bec9-107">O common language runtime fornece uma barreira para certas exceções sem tratamento que são usados para controlar o fluxo do programa:</span><span class="sxs-lookup"><span data-stu-id="8bec9-107">The common language runtime provides a backstop for certain unhandled exceptions that are used for controlling program flow:</span></span>  
  
- <span data-ttu-id="8bec9-108">Uma <xref:System.Threading.ThreadAbortException> é gerada em um thread porque <xref:System.Threading.Thread.Abort%2A> foi chamado.</span><span class="sxs-lookup"><span data-stu-id="8bec9-108">A <xref:System.Threading.ThreadAbortException> is thrown in a thread because <xref:System.Threading.Thread.Abort%2A> was called.</span></span>  
  
- <span data-ttu-id="8bec9-109">Um <xref:System.AppDomainUnloadedException> é gerado em um thread, pois o domínio do aplicativo no qual o thread está em execução está sendo descarregado.</span><span class="sxs-lookup"><span data-stu-id="8bec9-109">An <xref:System.AppDomainUnloadedException> is thrown in a thread because the application domain in which the thread is executing is being unloaded.</span></span>  
  
- <span data-ttu-id="8bec9-110">O Common Language Runtime ou um processo de host encerra o thread lançando uma exceção interna.</span><span class="sxs-lookup"><span data-stu-id="8bec9-110">The common language runtime or a host process terminates the thread by throwing an internal exception.</span></span>  
  
 <span data-ttu-id="8bec9-111">Se qualquer uma dessas exceções não tiver tratamento em threads criados pelo common language runtime, a exceção encerrará o thread, mas o common language runtime não permitirá que a exceção prossiga.</span><span class="sxs-lookup"><span data-stu-id="8bec9-111">If any of these exceptions are unhandled in threads created by the common language runtime, the exception terminates the thread, but the common language runtime does not allow the exception to proceed further.</span></span>  
  
 <span data-ttu-id="8bec9-112">Se essas exceções não tiverem tratamento no thread principal, ou em threads que entraram no runtime a partir do código não gerenciado, elas prosseguirão normalmente, resultando no encerramento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8bec9-112">If these exceptions are unhandled in the main thread, or in threads that entered the runtime from unmanaged code, they proceed normally, resulting in termination of the application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8bec9-113">É possível que o runtime lance uma exceção não tratada antes que qualquer código gerenciado tenha a oportunidade de instalar um manipulador de exceção.</span><span class="sxs-lookup"><span data-stu-id="8bec9-113">It is possible for the runtime to throw an unhandled exception before any managed code has had a chance to install an exception handler.</span></span> <span data-ttu-id="8bec9-114">Mesmo que o código gerenciado não tivesse possibilidade de manipular essa exceção, a exceção recebe a permissão para prosseguir naturalmente.</span><span class="sxs-lookup"><span data-stu-id="8bec9-114">Even though managed code had no chance to handle such an exception, the exception is allowed to proceed naturally.</span></span>  
  
## <a name="exposing-threading-problems-during-development"></a><span data-ttu-id="8bec9-115">Exposição de problemas de threading durante o desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="8bec9-115">Exposing Threading Problems During Development</span></span>  
 <span data-ttu-id="8bec9-116">Quando os threads recebem a permissão para falhar em modo silencioso, sem encerrar o aplicativo, problemas graves de programação podem passar sem detecção.</span><span class="sxs-lookup"><span data-stu-id="8bec9-116">When threads are allowed to fail silently, without terminating the application, serious programming problems can go undetected.</span></span> <span data-ttu-id="8bec9-117">Esse é um problema específico para serviços e outros aplicativos que são executados por longos períodos.</span><span class="sxs-lookup"><span data-stu-id="8bec9-117">This is a particular problem for services and other applications that run for extended periods.</span></span> <span data-ttu-id="8bec9-118">À medida que os threads falham, o estado do programa se torna cada vez mais corrompido.</span><span class="sxs-lookup"><span data-stu-id="8bec9-118">As threads fail, program state gradually becomes corrupted.</span></span> <span data-ttu-id="8bec9-119">O desempenho do aplicativo pode piorar ou o aplicativo pode parar de responder.</span><span class="sxs-lookup"><span data-stu-id="8bec9-119">Application performance may degrade, or the application might become unresponsive.</span></span>  
  
 <span data-ttu-id="8bec9-120">Permitir que exceções sem tratamento em threads prossigam naturalmente, até que o sistema operacional encerre o programa, expõe esses problemas durante o desenvolvimento e teste.</span><span class="sxs-lookup"><span data-stu-id="8bec9-120">Allowing unhandled exceptions in threads to proceed naturally, until the operating system terminates the program, exposes such problems during development and testing.</span></span> <span data-ttu-id="8bec9-121">Relatórios de erros em depuração de suporte de encerramentos do programa.</span><span class="sxs-lookup"><span data-stu-id="8bec9-121">Error reports on program terminations support debugging.</span></span>  
  
## <a name="change-from-previous-versions"></a><span data-ttu-id="8bec9-122">Alterar de versões anteriores</span><span class="sxs-lookup"><span data-stu-id="8bec9-122">Change from previous versions</span></span>

<span data-ttu-id="8bec9-123">No .NET Framework versões 1,0 e 1,1, o Common Language Runtime fornece um Backstop para exceções sem tratamento nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="8bec9-123">In .NET Framework versions 1.0 and 1.1, the common language runtime provides a backstop for unhandled exceptions in the following situations:</span></span>  
  
- <span data-ttu-id="8bec9-124">Não existe exceção sem tratamento em um thread de pool de threads.</span><span class="sxs-lookup"><span data-stu-id="8bec9-124">There is no such thing as an unhandled exception on a thread pool thread.</span></span> <span data-ttu-id="8bec9-125">Quando uma tarefa gera uma exceção sem tratamento, o runtime imprime o rastreamento de pilha da exceção para o console e, depois, retorna o thread para o pool de threads.</span><span class="sxs-lookup"><span data-stu-id="8bec9-125">When a task throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then returns the thread to the thread pool.</span></span>  
  
- <span data-ttu-id="8bec9-126">Não existe exceção sem tratamento em um thread criado com o método <xref:System.Threading.Thread.Start%2A> da classe <xref:System.Threading.Thread>.</span><span class="sxs-lookup"><span data-stu-id="8bec9-126">There is no such thing as an unhandled exception on a thread created with the <xref:System.Threading.Thread.Start%2A> method of the <xref:System.Threading.Thread> class.</span></span> <span data-ttu-id="8bec9-127">Quando um código em execução em um thread como esse gera uma exceção sem tratamento, o runtime imprime o rastreamento de pilha da exceção para o console e, depois, encerra normalmente o thread.</span><span class="sxs-lookup"><span data-stu-id="8bec9-127">When code running on such a thread throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then gracefully terminates the thread.</span></span>  
  
- <span data-ttu-id="8bec9-128">Não existe exceção sem tratamento no thread finalizador.</span><span class="sxs-lookup"><span data-stu-id="8bec9-128">There is no such thing as an unhandled exception on the finalizer thread.</span></span> <span data-ttu-id="8bec9-129">Quando um finalizar gera uma exceção sem tratamento, o runtime imprime o rastreamento de pilha da exceção para o console e, depois, permite que o thread finalizador retome a execução dos finalizadores.</span><span class="sxs-lookup"><span data-stu-id="8bec9-129">When a finalizer throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then allows the finalizer thread to resume running finalizers.</span></span>  
  
 <span data-ttu-id="8bec9-130">O status de primeiro plano ou segundo plano de um thread gerenciado não afeta esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="8bec9-130">The foreground or background status of a managed thread does not affect this behavior.</span></span>  
  
 <span data-ttu-id="8bec9-131">Para as exceções sem tratamento em threads com origem em código não gerenciado, a diferença é mais sutil.</span><span class="sxs-lookup"><span data-stu-id="8bec9-131">For unhandled exceptions on threads originating in unmanaged code, the difference is more subtle.</span></span> <span data-ttu-id="8bec9-132">A caixa de diálogo de anexação JIT do runtime impede a caixa de diálogo do sistema operacional para exceções gerenciadas ou exceções nativas em threads que passaram por código nativo.</span><span class="sxs-lookup"><span data-stu-id="8bec9-132">The runtime JIT-attach dialog preempts the operating system dialog for managed exceptions or native exceptions on threads that have passed through native code.</span></span> <span data-ttu-id="8bec9-133">O processo é encerrado em todos os casos.</span><span class="sxs-lookup"><span data-stu-id="8bec9-133">The process terminates in all cases.</span></span>

### <a name="migration"></a><span data-ttu-id="8bec9-134">Migração</span><span class="sxs-lookup"><span data-stu-id="8bec9-134">Migration</span></span>

<span data-ttu-id="8bec9-135">Se você estiver migrando do .NET Framework 1,0 ou 1,1 e tirar proveito da backstop de tempo de execução, por exemplo, para encerrar threads, considere uma das seguintes estratégias de migração:</span><span class="sxs-lookup"><span data-stu-id="8bec9-135">If you are migrating from .NET Framework 1.0 or 1.1 and took advantage of the runtime backstop, for example to terminate threads, consider one of the following migration strategies:</span></span>  
  
- <span data-ttu-id="8bec9-136">Reestruturar o código para que o thread feche normalmente quando receber um sinal.</span><span class="sxs-lookup"><span data-stu-id="8bec9-136">Restructure the code so the thread exits gracefully when a signal is received.</span></span>  
  
- <span data-ttu-id="8bec9-137">Use o método <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> para anular o thread.</span><span class="sxs-lookup"><span data-stu-id="8bec9-137">Use the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method to abort the thread.</span></span>  
  
- <span data-ttu-id="8bec9-138">Se um thread precisar ser interrompido para que o encerramento do processo possa continuar, torne o thread um thread em segundo plano para que ela seja encerrado automaticamente no encerramento do processo.</span><span class="sxs-lookup"><span data-stu-id="8bec9-138">If a thread must be stopped so that process termination can proceed, make the thread a background thread so that it is automatically terminated on process exit.</span></span>  
  
<span data-ttu-id="8bec9-139">Em todos os casos, a estratégia deve seguir as diretrizes de design para exceções.</span><span class="sxs-lookup"><span data-stu-id="8bec9-139">In all cases, the strategy should follow the design guidelines for exceptions.</span></span> <span data-ttu-id="8bec9-140">Confira [Diretrizes de design para exceções](../design-guidelines/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="8bec9-140">See [Design Guidelines for Exceptions](../design-guidelines/exceptions.md).</span></span>  
  
<span data-ttu-id="8bec9-141">Como uma medida temporária de compatibilidade, os administradores podem colocar um sinalizador de compatibilidade na seção `<runtime>` do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8bec9-141">As a temporary compatibility measure, administrators can place a compatibility flag in the `<runtime>` section of the application configuration file.</span></span> <span data-ttu-id="8bec9-142">Isso faz com que o common language runtime reverta para o comportamento das versões 1.0 e 1.1.</span><span class="sxs-lookup"><span data-stu-id="8bec9-142">This causes the common language runtime to revert to the behavior of versions 1.0 and 1.1.</span></span>  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a><span data-ttu-id="8bec9-143">Substituição do host</span><span class="sxs-lookup"><span data-stu-id="8bec9-143">Host Override</span></span>

<span data-ttu-id="8bec9-144">Um host não gerenciado pode usar a interface [ICLRPolicyManager](../../framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) na API de hospedagem para substituir a política de exceção padrão sem tratamento do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="8bec9-144">An unmanaged host can use the [ICLRPolicyManager](../../framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface in the Hosting API to override the default unhandled exception policy of the common language runtime.</span></span> <span data-ttu-id="8bec9-145">A função [ICLRPolicyManager::SetUnhandledExceptionPolicy](../../framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) é usada para definir a política para exceções sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="8bec9-145">The [ICLRPolicyManager::SetUnhandledExceptionPolicy](../../framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) function is used to set the policy for unhandled exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bec9-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="8bec9-146">See also</span></span>

- [<span data-ttu-id="8bec9-147">Noções básicas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="8bec9-147">Managed Threading Basics</span></span>](managed-threading-basics.md)
