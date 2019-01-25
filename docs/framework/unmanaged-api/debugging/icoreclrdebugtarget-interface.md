---
title: Interface ICoreClrDebugTarget
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4576d8ea7d601e1b37d0cb6f54802f93bc128622
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54593778"
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="9f1c8-102">Interface ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="9f1c8-102">ICoreClrDebugTarget Interface</span></span>
<span data-ttu-id="9f1c8-103">Fornece métodos que controlam as contagens de referência, enumerar os processos e liberar a memória associada a um depurador anexado a um destino remoto do Silverlight do Macintosh.</span><span class="sxs-lookup"><span data-stu-id="9f1c8-103">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f1c8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f1c8-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="9f1c8-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="9f1c8-105">Methods</span></span>  
  
|<span data-ttu-id="9f1c8-106">Método</span><span class="sxs-lookup"><span data-stu-id="9f1c8-106">Method</span></span>|<span data-ttu-id="9f1c8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f1c8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9f1c8-108">Método ICoreClrDebugTarget::EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="9f1c8-108">ICoreClrDebugTarget::EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="9f1c8-109">Enumera os processos que estão em execução em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="9f1c8-109">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="9f1c8-110">Método ICoreClrDebugTarget::EnumRuntimes</span><span class="sxs-lookup"><span data-stu-id="9f1c8-110">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="9f1c8-111">Enumera os tempos de execução de linguagem comum (CLRs) no processo especificado em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="9f1c8-111">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="9f1c8-112">Método ICoreClrDebugTarget::FreeMemory</span><span class="sxs-lookup"><span data-stu-id="9f1c8-112">ICoreClrDebugTarget::FreeMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="9f1c8-113">Libera a memória alocada pelos métodos de enumeração nessa classe.</span><span class="sxs-lookup"><span data-stu-id="9f1c8-113">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f1c8-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="9f1c8-114">Remarks</span></span>  
 <span data-ttu-id="9f1c8-115">Atualmente, essa funcionalidade tem suporte somente para depuração de um destino de aplicativo baseado em Silverlight que está em execução em um computador remoto do Macintosh.</span><span class="sxs-lookup"><span data-stu-id="9f1c8-115">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f1c8-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9f1c8-116">Requirements</span></span>  
 <span data-ttu-id="9f1c8-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f1c8-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f1c8-118">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="9f1c8-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="9f1c8-119">**Biblioteca:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="9f1c8-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="9f1c8-120">**Versões do .NET framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="9f1c8-120">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f1c8-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f1c8-121">See also</span></span>
- [<span data-ttu-id="9f1c8-122">Interface ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="9f1c8-122">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="9f1c8-123">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="9f1c8-123">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="9f1c8-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="9f1c8-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
