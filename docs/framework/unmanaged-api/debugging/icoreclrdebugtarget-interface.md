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
ms.openlocfilehash: 83afe121b6bf0de3c5542695e38b6605db7a8b6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121826"
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="51c74-102">Interface ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="51c74-102">ICoreClrDebugTarget Interface</span></span>
<span data-ttu-id="51c74-103">Fornece métodos que controlam contagens de referência, enumeram processos e liberam a memória associada a um depurador que é anexado a um destino do Silverlight do Macintosh remoto.</span><span class="sxs-lookup"><span data-stu-id="51c74-103">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51c74-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51c74-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="methods"></a><span data-ttu-id="51c74-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="51c74-105">Methods</span></span>  
  
|<span data-ttu-id="51c74-106">Método</span><span class="sxs-lookup"><span data-stu-id="51c74-106">Method</span></span>|<span data-ttu-id="51c74-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="51c74-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="51c74-108">Método ICoreClrDebugTarget::EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="51c74-108">ICoreClrDebugTarget::EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="51c74-109">Enumera os processos que estão sendo executados em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="51c74-109">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="51c74-110">Método ICoreClrDebugTarget::EnumRuntimes</span><span class="sxs-lookup"><span data-stu-id="51c74-110">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="51c74-111">Enumera os Common Language runtimes (CLRs) no processo especificado em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="51c74-111">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="51c74-112">Método ICoreClrDebugTarget::FreeMemory</span><span class="sxs-lookup"><span data-stu-id="51c74-112">ICoreClrDebugTarget::FreeMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="51c74-113">Libera a memória alocada pelos métodos de enumeração nesta classe.</span><span class="sxs-lookup"><span data-stu-id="51c74-113">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51c74-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="51c74-114">Remarks</span></span>  
 <span data-ttu-id="51c74-115">Atualmente, essa funcionalidade tem suporte apenas para a depuração de um destino de aplicativo baseado no Silverlight que está sendo executado em um computador Macintosh remoto.</span><span class="sxs-lookup"><span data-stu-id="51c74-115">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51c74-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="51c74-116">Requirements</span></span>  
 <span data-ttu-id="51c74-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51c74-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51c74-118">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="51c74-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="51c74-119">**Biblioteca:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="51c74-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="51c74-120">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="51c74-120">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51c74-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51c74-121">See also</span></span>

- [<span data-ttu-id="51c74-122">Interface ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="51c74-122">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="51c74-123">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="51c74-123">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="51c74-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="51c74-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
