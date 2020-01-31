---
title: Depuração Silverlight
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
ms.openlocfilehash: 91f311818b615ea8f166bb3362ec52d39fcd0297
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790321"
---
# <a name="silverlight-debugging"></a><span data-ttu-id="ffe33-102">Depuração Silverlight</span><span class="sxs-lookup"><span data-stu-id="ffe33-102">Silverlight Debugging</span></span>
<span data-ttu-id="ffe33-103">Os tópicos nesta seção descrevem o ambiente e as interfaces que o Common Language Runtime (CLR) fornece para dar suporte à depuração de aplicativos baseados no Silverlight que estão em execução no sistema operacional Windows ou na plataforma Macintosh.</span><span class="sxs-lookup"><span data-stu-id="ffe33-103">The topics in this section describe the environment and interfaces that the common language runtime (CLR) provides to support debugging Silverlight-based applications that are running on the Windows operating system, or on the Macintosh platform.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ffe33-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ffe33-104">In This Section</span></span>  
 [<span data-ttu-id="ffe33-105">Função EnumerateCLRs</span><span class="sxs-lookup"><span data-stu-id="ffe33-105">EnumerateCLRs Function</span></span>](enumerateclrs-function.md)  
 <span data-ttu-id="ffe33-106">Fornece um mecanismo para enumerar o CLRs em um processo.</span><span class="sxs-lookup"><span data-stu-id="ffe33-106">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
 [<span data-ttu-id="ffe33-107">Função CloseCLREnumeration</span><span class="sxs-lookup"><span data-stu-id="ffe33-107">CloseCLREnumeration Function</span></span>](closeclrenumeration-function.md)  
 <span data-ttu-id="ffe33-108">Fecha qualquer evento válido de inicialização de continuidade do CLR localizado em uma matriz de identificadores retornada pela [função EnumerateCLRs](enumerateclrs-function.md)e libera a memória para as matrizes de caminho de cadeia de caracteres e identificador.</span><span class="sxs-lookup"><span data-stu-id="ffe33-108">Closes any valid CLR continue-startup events located in an array of handles returned by the [EnumerateCLRs Function](enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
 [<span data-ttu-id="ffe33-109">Função CreateCoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="ffe33-109">CreateCoreClrDebugTarget Function</span></span>](createcoreclrdebugtarget-function.md)  
 <span data-ttu-id="ffe33-110">Cria uma conexão com um destino remoto para enumeração de processo e tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ffe33-110">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="ffe33-111">Função CreateCordbObject</span><span class="sxs-lookup"><span data-stu-id="ffe33-111">CreateCordbObject Function</span></span>](createcordbobject-function.md)  
 <span data-ttu-id="ffe33-112">Cria uma interface do depurador que fornece funcionalidade para instanciar uma sessão de depuração gerenciada em um processo remoto.</span><span class="sxs-lookup"><span data-stu-id="ffe33-112">Creates a debugger interface that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
 [<span data-ttu-id="ffe33-113">Função CreateVersionStringFromModule</span><span class="sxs-lookup"><span data-stu-id="ffe33-113">CreateVersionStringFromModule Function</span></span>](createversionstringfrommodule-function.md)  
 <span data-ttu-id="ffe33-114">Cria uma cadeia de caracteres de versão a partir de um caminho CLR em um processo de destino.</span><span class="sxs-lookup"><span data-stu-id="ffe33-114">Creates a version string from a CLR path in a target process.</span></span>  
  
 [<span data-ttu-id="ffe33-115">Função CreateDebuggingInterfaceFromVersion</span><span class="sxs-lookup"><span data-stu-id="ffe33-115">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function-for-silverlight.md)  
 <span data-ttu-id="ffe33-116">Aceita uma cadeia de caracteres de versão do CLR retornada da função de [função CreateVersionStringFromModule](createversionstringfrommodule-function.md)e retorna uma interface de depurador correspondente.</span><span class="sxs-lookup"><span data-stu-id="ffe33-116">Accepts a CLR version string returned from [CreateVersionStringFromModule Function](createversionstringfrommodule-function.md)function, and returns a corresponding debugger interface.</span></span>  
  
 [<span data-ttu-id="ffe33-117">Estrutura CoreClrDebugProcInfo</span><span class="sxs-lookup"><span data-stu-id="ffe33-117">CoreClrDebugProcInfo Structure</span></span>](coreclrdebugprocinfo-structure.md)  
 <span data-ttu-id="ffe33-118">Representa um processo que está sendo executado em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="ffe33-118">Represents a process that is running on a remote machine.</span></span>  
  
 [<span data-ttu-id="ffe33-119">Estrutura CoreClrDebugRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="ffe33-119">CoreClrDebugRuntimeInfo Structure</span></span>](coreclrdebugruntimeinfo-structure.md)  
 <span data-ttu-id="ffe33-120">Representa uma instância do CLR que é carregada em um processo em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="ffe33-120">Represents a CLR instance that is loaded in a process on a remote machine.</span></span>  
  
 [<span data-ttu-id="ffe33-121">Função GetStartupNotificationEvent</span><span class="sxs-lookup"><span data-stu-id="ffe33-121">GetStartupNotificationEvent Function</span></span>](getstartupnotificationevent-function.md)  
 <span data-ttu-id="ffe33-122">Cria ou abre um identificador de evento que será sinalizado por qualquer Common Language Runtime (CLR) que esteja carregando no processo de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="ffe33-122">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
 [<span data-ttu-id="ffe33-123">Interface ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="ffe33-123">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)  
 <span data-ttu-id="ffe33-124">Cria uma conexão com um destino remoto para enumeração de processo e tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ffe33-124">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="ffe33-125">Função InitDbgTransportManager</span><span class="sxs-lookup"><span data-stu-id="ffe33-125">InitDbgTransportManager Function</span></span>](initdbgtransportmanager-function.md)  
 <span data-ttu-id="ffe33-126">Inicializa o Gerenciador de transporte para se conectar a um destino remoto para enumeração de processo e tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ffe33-126">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="ffe33-127">Função ShutdownDbgTransportManager</span><span class="sxs-lookup"><span data-stu-id="ffe33-127">ShutdownDbgTransportManager Function</span></span>](shutdowndbgtransportmanager-function.md)  
 <span data-ttu-id="ffe33-128">Desliga o Gerenciador de transporte para uma conexão a um computador de destino remoto.</span><span class="sxs-lookup"><span data-stu-id="ffe33-128">Shuts down the transport manager for a connection to a remote target machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffe33-129">Veja também</span><span class="sxs-lookup"><span data-stu-id="ffe33-129">See also</span></span>

- [<span data-ttu-id="ffe33-130">Depurando coclasses</span><span class="sxs-lookup"><span data-stu-id="ffe33-130">Debugging Coclasses</span></span>](debugging-coclasses.md)
- [<span data-ttu-id="ffe33-131">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ffe33-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ffe33-132">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="ffe33-132">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
- [<span data-ttu-id="ffe33-133">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="ffe33-133">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="ffe33-134">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="ffe33-134">Debugging Structures</span></span>](debugging-structures.md)
