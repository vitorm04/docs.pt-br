---
title: Interface ICoreClrDebugTarget
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICoreClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 62d43121efbc039b8fad0b78bed7ec4a655efabb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="91050-102">Interface ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="91050-102">ICoreClrDebugTarget Interface</span></span>
<span data-ttu-id="91050-103">Fornece métodos que controlam as contagens de referência, enumerar os processos e liberar a memória associada a um depurador anexado a um destino Macintosh Silverlight remoto.</span><span class="sxs-lookup"><span data-stu-id="91050-103">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91050-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="91050-104">Syntax</span></span>  
  
```  
class ICoreClrDebugTarget {  
      HRESULT EnumProcesses (  
          [out] DWORD*                    pcProcs,  
          [out] CoreClrDebugProcInfo**    ppProcs  
      );  
  
      HRESULT EnumRuntimes (  
      [in]  DWORD                      dwInternalProcessID,  
      [out] DWORD*                     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**  ppRuntimes  
      );  
  
      void FreeMemory (  
      [in] void*      pMemory  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="91050-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="91050-105">Methods</span></span>  
  
|<span data-ttu-id="91050-106">Método</span><span class="sxs-lookup"><span data-stu-id="91050-106">Method</span></span>|<span data-ttu-id="91050-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="91050-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="91050-108">Método ICoreClrDebugTarget::EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="91050-108">ICoreClrDebugTarget::EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="91050-109">Enumera os processos em execução em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="91050-109">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="91050-110">Método ICoreClrDebugTarget::EnumRuntimes</span><span class="sxs-lookup"><span data-stu-id="91050-110">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="91050-111">Enumera os tempos de execução de linguagem comum (CLRs) do processo especificado em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="91050-111">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="91050-112">Método ICoreClrDebugTarget::FreeMemory</span><span class="sxs-lookup"><span data-stu-id="91050-112">ICoreClrDebugTarget::FreeMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="91050-113">Libera a memória alocada por métodos de enumeração nesta classe.</span><span class="sxs-lookup"><span data-stu-id="91050-113">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91050-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="91050-114">Remarks</span></span>  
 <span data-ttu-id="91050-115">Atualmente, essa funcionalidade tem suporte somente para um destino de aplicativo baseado em Silverlight que está em execução em um computador Macintosh remoto de depuração.</span><span class="sxs-lookup"><span data-stu-id="91050-115">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91050-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="91050-116">Requirements</span></span>  
 <span data-ttu-id="91050-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91050-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91050-118">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="91050-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="91050-119">**Biblioteca:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="91050-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="91050-120">**Versões do .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="91050-120">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91050-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91050-121">See Also</span></span>  
 [<span data-ttu-id="91050-122">Interface ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="91050-122">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="91050-123">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="91050-123">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="91050-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="91050-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
