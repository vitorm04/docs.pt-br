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
ms.openlocfilehash: c44a12ef377d29e0b33b8be86aa1d8f0aa9d26bd
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397150"
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="49cad-102">Interface ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="49cad-102">ICoreClrDebugTarget Interface</span></span>
<span data-ttu-id="49cad-103">Fornece métodos que controlam contagens de referência, enumeram processos e liberam a memória associada a um depurador que é anexado a um destino do Silverlight do Macintosh remoto.</span><span class="sxs-lookup"><span data-stu-id="49cad-103">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49cad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="49cad-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="49cad-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="49cad-105">Methods</span></span>  
  
|<span data-ttu-id="49cad-106">Método</span><span class="sxs-lookup"><span data-stu-id="49cad-106">Method</span></span>|<span data-ttu-id="49cad-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="49cad-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="49cad-108">Método ICoreClrDebugTarget::EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="49cad-108">ICoreClrDebugTarget::EnumProcesses Method</span></span>](icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="49cad-109">Enumera os processos que estão sendo executados em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="49cad-109">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="49cad-110">Método ICoreClrDebugTarget::EnumRuntimes</span><span class="sxs-lookup"><span data-stu-id="49cad-110">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="49cad-111">Enumera os Common Language runtimes (CLRs) no processo especificado em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="49cad-111">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="49cad-112">Método ICoreClrDebugTarget::FreeMemory</span><span class="sxs-lookup"><span data-stu-id="49cad-112">ICoreClrDebugTarget::FreeMemory Method</span></span>](icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="49cad-113">Libera a memória alocada pelos métodos de enumeração nesta classe.</span><span class="sxs-lookup"><span data-stu-id="49cad-113">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49cad-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="49cad-114">Remarks</span></span>  
 <span data-ttu-id="49cad-115">Atualmente, essa funcionalidade tem suporte apenas para a depuração de um destino de aplicativo baseado no Silverlight que está sendo executado em um computador Macintosh remoto.</span><span class="sxs-lookup"><span data-stu-id="49cad-115">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49cad-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="49cad-116">Requirements</span></span>  
 <span data-ttu-id="49cad-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49cad-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49cad-118">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="49cad-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="49cad-119">**Biblioteca:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="49cad-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="49cad-120">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="49cad-120">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49cad-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="49cad-121">See also</span></span>

- [<span data-ttu-id="49cad-122">Interface ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="49cad-122">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="49cad-123">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="49cad-123">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="49cad-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="49cad-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
