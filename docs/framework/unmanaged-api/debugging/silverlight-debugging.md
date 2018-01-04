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
ms.workload: dotnet
ms.openlocfilehash: f6869e58ca47b7b55a5b988e0f6ae4a224f0f35a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="silverlight-debugging"></a><span data-ttu-id="6cd6b-102">Depuração Silverlight</span><span class="sxs-lookup"><span data-stu-id="6cd6b-102">Silverlight Debugging</span></span>
<span data-ttu-id="6cd6b-103">Os tópicos nesta seção descrevem o ambiente e interfaces que fornece o common language runtime (CLR) para dar suporte a depuração de aplicativos baseados no Silverlight que estão executando o sistema operacional Windows, ou na plataforma Macintosh.</span><span class="sxs-lookup"><span data-stu-id="6cd6b-103">The topics in this section describe the environment and interfaces that the common language runtime (CLR) provides to support debugging Silverlight-based applications that are running on the Windows operating system, or on the Macintosh platform.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6cd6b-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="6cd6b-104">In This Section</span></span>  
 [<span data-ttu-id="6cd6b-105">Função EnumerateCLRs</span><span class="sxs-lookup"><span data-stu-id="6cd6b-105">EnumerateCLRs Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 <span data-ttu-id="6cd6b-106">Fornece um mecanismo para enumerar CLRs em um processo.</span><span class="sxs-lookup"><span data-stu-id="6cd6b-106">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
 [<span data-ttu-id="6cd6b-107">Função CloseCLREnumeration</span><span class="sxs-lookup"><span data-stu-id="6cd6b-107">CloseCLREnumeration Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 <span data-ttu-id="6cd6b-108">Fecha qualquer evento de inicialização continuar CLR válido localizado em uma matriz de identificadores retornado pelo [função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)e libera a memória para as matrizes de caminho do identificador e a cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6cd6b-108">Closes any valid CLR continue-startup events located in an array of handles returned by the [EnumerateCLRs Function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
 [<span data-ttu-id="6cd6b-109">Função CreateCoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="6cd6b-109">CreateCoreClrDebugTarget Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 <span data-ttu-id="6cd6b-110">Cria uma conexão para um destino remoto para enumeração de processo e o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6cd6b-110">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="6cd6b-111">Função CreateCordbObject</span><span class="sxs-lookup"><span data-stu-id="6cd6b-111">CreateCordbObject Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 <span data-ttu-id="6cd6b-112">Cria uma interface de depurador que fornece funcionalidade para criar uma instância de uma sessão de depuração gerenciada em um processo remoto.</span><span class="sxs-lookup"><span data-stu-id="6cd6b-112">Creates a debugger interface that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
 [<span data-ttu-id="6cd6b-113">Função CreateVersionStringFromModule</span><span class="sxs-lookup"><span data-stu-id="6cd6b-113">CreateVersionStringFromModule Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 <span data-ttu-id="6cd6b-114">Cria uma cadeia de caracteres de versão de um caminho CLR em um processo de destino.</span><span class="sxs-lookup"><span data-stu-id="6cd6b-114">Creates a version string from a CLR path in a target process.</span></span>  
  
 [<span data-ttu-id="6cd6b-115">Função CreateDebuggingInterfaceFromVersion</span><span class="sxs-lookup"><span data-stu-id="6cd6b-115">CreateDebuggingInterfaceFromVersion Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 <span data-ttu-id="6cd6b-116">Aceita uma cadeia de caracteres de versão do CLR retornado de [função CreateVersionStringFromModule](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)de função e retorna uma interface de depurador correspondente.</span><span class="sxs-lookup"><span data-stu-id="6cd6b-116">Accepts a CLR version string returned from [CreateVersionStringFromModule Function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)function, and returns a corresponding debugger interface.</span></span>  
  
 [<span data-ttu-id="6cd6b-117">Estrutura CoreClrDebugProcInfo</span><span class="sxs-lookup"><span data-stu-id="6cd6b-117">CoreClrDebugProcInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 <span data-ttu-id="6cd6b-118">Representa um processo que está em execução em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="6cd6b-118">Represents a process that is running on a remote machine.</span></span>  
  
 [<span data-ttu-id="6cd6b-119">Estrutura CoreClrDebugRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="6cd6b-119">CoreClrDebugRuntimeInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 <span data-ttu-id="6cd6b-120">Representa uma instância do CLR que é carregada em um processo em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="6cd6b-120">Represents a CLR instance that is loaded in a process on a remote machine.</span></span>  
  
 [<span data-ttu-id="6cd6b-121">Função GetStartupNotificationEvent</span><span class="sxs-lookup"><span data-stu-id="6cd6b-121">GetStartupNotificationEvent Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 <span data-ttu-id="6cd6b-122">Cria ou abre um identificador de evento será sinalizado após qualquer common language runtime (CLR) que está sendo carregado no processo de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="6cd6b-122">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
 [<span data-ttu-id="6cd6b-123">Interface ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="6cd6b-123">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 <span data-ttu-id="6cd6b-124">Cria uma conexão para um destino remoto para enumeração de processo e o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6cd6b-124">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="6cd6b-125">Função InitDbgTransportManager</span><span class="sxs-lookup"><span data-stu-id="6cd6b-125">InitDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 <span data-ttu-id="6cd6b-126">Inicializa o Gerenciador de transporte para se conectar a um destino remoto para enumeração de processo e o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6cd6b-126">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="6cd6b-127">Função ShutdownDbgTransportManager</span><span class="sxs-lookup"><span data-stu-id="6cd6b-127">ShutdownDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 <span data-ttu-id="6cd6b-128">Desliga o Gerenciador de transporte para uma conexão a uma máquina de destino remoto.</span><span class="sxs-lookup"><span data-stu-id="6cd6b-128">Shuts down the transport manager for a connection to a remote target machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cd6b-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6cd6b-129">See Also</span></span>  
 [<span data-ttu-id="6cd6b-130">Depurando coclasses</span><span class="sxs-lookup"><span data-stu-id="6cd6b-130">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
 [<span data-ttu-id="6cd6b-131">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6cd6b-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6cd6b-132">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="6cd6b-132">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
 [<span data-ttu-id="6cd6b-133">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="6cd6b-133">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="6cd6b-134">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="6cd6b-134">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
