---
title: "Depuração Silverlight"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bf39d2dd12207d594c7bf5bd5b249d82c3f15d3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="silverlight-debugging"></a><span data-ttu-id="cd668-102">Depuração Silverlight</span><span class="sxs-lookup"><span data-stu-id="cd668-102">Silverlight Debugging</span></span>
<span data-ttu-id="cd668-103">Os tópicos nesta seção descrevem o ambiente e interfaces que fornece o common language runtime (CLR) para dar suporte a depuração de aplicativos baseados no Silverlight que estão executando o sistema operacional Windows, ou na plataforma Macintosh.</span><span class="sxs-lookup"><span data-stu-id="cd668-103">The topics in this section describe the environment and interfaces that the common language runtime (CLR) provides to support debugging Silverlight-based applications that are running on the Windows operating system, or on the Macintosh platform.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cd668-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="cd668-104">In This Section</span></span>  
 [<span data-ttu-id="cd668-105">Função EnumerateCLRs</span><span class="sxs-lookup"><span data-stu-id="cd668-105">EnumerateCLRs Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 <span data-ttu-id="cd668-106">Fornece um mecanismo para enumerar CLRs em um processo.</span><span class="sxs-lookup"><span data-stu-id="cd668-106">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
 [<span data-ttu-id="cd668-107">Função CloseCLREnumeration</span><span class="sxs-lookup"><span data-stu-id="cd668-107">CloseCLREnumeration Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 <span data-ttu-id="cd668-108">Fecha qualquer evento de inicialização continuar CLR válido localizado em uma matriz de identificadores retornado pelo [função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)e libera a memória para as matrizes de caminho do identificador e a cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="cd668-108">Closes any valid CLR continue-startup events located in an array of handles returned by the [EnumerateCLRs Function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
 [<span data-ttu-id="cd668-109">Função CreateCoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="cd668-109">CreateCoreClrDebugTarget Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 <span data-ttu-id="cd668-110">Cria uma conexão para um destino remoto para enumeração de processo e o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="cd668-110">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="cd668-111">Função CreateCordbObject</span><span class="sxs-lookup"><span data-stu-id="cd668-111">CreateCordbObject Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 <span data-ttu-id="cd668-112">Cria uma interface de depurador que fornece funcionalidade para criar uma instância de uma sessão de depuração gerenciada em um processo remoto.</span><span class="sxs-lookup"><span data-stu-id="cd668-112">Creates a debugger interface that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
 [<span data-ttu-id="cd668-113">Função CreateVersionStringFromModule</span><span class="sxs-lookup"><span data-stu-id="cd668-113">CreateVersionStringFromModule Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 <span data-ttu-id="cd668-114">Cria uma cadeia de caracteres de versão de um caminho CLR em um processo de destino.</span><span class="sxs-lookup"><span data-stu-id="cd668-114">Creates a version string from a CLR path in a target process.</span></span>  
  
 [<span data-ttu-id="cd668-115">Função CreateDebuggingInterfaceFromVersion</span><span class="sxs-lookup"><span data-stu-id="cd668-115">CreateDebuggingInterfaceFromVersion Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 <span data-ttu-id="cd668-116">Aceita uma cadeia de caracteres de versão do CLR retornado de [função CreateVersionStringFromModule](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)de função e retorna uma interface de depurador correspondente.</span><span class="sxs-lookup"><span data-stu-id="cd668-116">Accepts a CLR version string returned from [CreateVersionStringFromModule Function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)function, and returns a corresponding debugger interface.</span></span>  
  
 [<span data-ttu-id="cd668-117">Estrutura CoreClrDebugProcInfo</span><span class="sxs-lookup"><span data-stu-id="cd668-117">CoreClrDebugProcInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 <span data-ttu-id="cd668-118">Representa um processo que está em execução em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="cd668-118">Represents a process that is running on a remote machine.</span></span>  
  
 [<span data-ttu-id="cd668-119">Estrutura CoreClrDebugRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="cd668-119">CoreClrDebugRuntimeInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 <span data-ttu-id="cd668-120">Representa uma instância do CLR que é carregada em um processo em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="cd668-120">Represents a CLR instance that is loaded in a process on a remote machine.</span></span>  
  
 [<span data-ttu-id="cd668-121">Função GetStartupNotificationEvent</span><span class="sxs-lookup"><span data-stu-id="cd668-121">GetStartupNotificationEvent Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 <span data-ttu-id="cd668-122">Cria ou abre um identificador de evento será sinalizado após qualquer common language runtime (CLR) que está sendo carregado no processo de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="cd668-122">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
 [<span data-ttu-id="cd668-123">Interface ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="cd668-123">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 <span data-ttu-id="cd668-124">Cria uma conexão para um destino remoto para enumeração de processo e o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="cd668-124">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="cd668-125">Função InitDbgTransportManager</span><span class="sxs-lookup"><span data-stu-id="cd668-125">InitDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 <span data-ttu-id="cd668-126">Inicializa o Gerenciador de transporte para se conectar a um destino remoto para enumeração de processo e o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="cd668-126">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="cd668-127">Função ShutdownDbgTransportManager</span><span class="sxs-lookup"><span data-stu-id="cd668-127">ShutdownDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 <span data-ttu-id="cd668-128">Desliga o Gerenciador de transporte para uma conexão a uma máquina de destino remoto.</span><span class="sxs-lookup"><span data-stu-id="cd668-128">Shuts down the transport manager for a connection to a remote target machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd668-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd668-129">See Also</span></span>  
 [<span data-ttu-id="cd668-130">Coclasses de depuração</span><span class="sxs-lookup"><span data-stu-id="cd668-130">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
 [<span data-ttu-id="cd668-131">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="cd668-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="cd668-132">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="cd668-132">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
 [<span data-ttu-id="cd668-133">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="cd668-133">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="cd668-134">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="cd668-134">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
