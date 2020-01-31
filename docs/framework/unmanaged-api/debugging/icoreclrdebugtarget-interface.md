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
ms.openlocfilehash: 190671b4f690f8c2cad43cf446a1196985ec5a42
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790747"
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="1660a-102">Interface ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="1660a-102">ICoreClrDebugTarget Interface</span></span>
<span data-ttu-id="1660a-103">Fornece métodos que controlam contagens de referência, enumeram processos e liberam a memória associada a um depurador que é anexado a um destino do Silverlight do Macintosh remoto.</span><span class="sxs-lookup"><span data-stu-id="1660a-103">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1660a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1660a-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="1660a-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="1660a-105">Methods</span></span>  
  
|<span data-ttu-id="1660a-106">Método</span><span class="sxs-lookup"><span data-stu-id="1660a-106">Method</span></span>|<span data-ttu-id="1660a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1660a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1660a-108">Método ICoreClrDebugTarget::EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="1660a-108">ICoreClrDebugTarget::EnumProcesses Method</span></span>](icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="1660a-109">Enumera os processos que estão sendo executados em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="1660a-109">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="1660a-110">Método ICoreClrDebugTarget::EnumRuntimes</span><span class="sxs-lookup"><span data-stu-id="1660a-110">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="1660a-111">Enumera os Common Language runtimes (CLRs) no processo especificado em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="1660a-111">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="1660a-112">Método ICoreClrDebugTarget::FreeMemory</span><span class="sxs-lookup"><span data-stu-id="1660a-112">ICoreClrDebugTarget::FreeMemory Method</span></span>](icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="1660a-113">Libera a memória alocada pelos métodos de enumeração nesta classe.</span><span class="sxs-lookup"><span data-stu-id="1660a-113">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1660a-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="1660a-114">Remarks</span></span>  
 <span data-ttu-id="1660a-115">Atualmente, essa funcionalidade tem suporte apenas para a depuração de um destino de aplicativo baseado no Silverlight que está sendo executado em um computador Macintosh remoto.</span><span class="sxs-lookup"><span data-stu-id="1660a-115">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1660a-116">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="1660a-116">Requirements</span></span>  
 <span data-ttu-id="1660a-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1660a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1660a-118">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="1660a-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="1660a-119">**Biblioteca:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="1660a-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="1660a-120">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="1660a-120">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1660a-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="1660a-121">See also</span></span>

- [<span data-ttu-id="1660a-122">Interface ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="1660a-122">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="1660a-123">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="1660a-123">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="1660a-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1660a-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
