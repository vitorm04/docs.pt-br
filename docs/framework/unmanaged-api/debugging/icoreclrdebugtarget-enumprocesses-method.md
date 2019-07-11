---
title: Método ICoreClrDebugTarget::EnumProcesses
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumProcesses
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 301e6cc153f905bc5c15e1b526e6fb1a492a76d6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774442"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="b046e-102">Método ICoreClrDebugTarget::EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="b046e-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="b046e-103">Enumera os processos que estão em execução em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="b046e-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b046e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b046e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b046e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b046e-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="b046e-106">[out] O número de processos retornados em `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="b046e-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="b046e-107">Esse valor pode ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="b046e-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="b046e-108">[out] Uma matriz de [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) estruturas que representam os processos em execução no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="b046e-108">[out] An array of [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b046e-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b046e-109">Return Value</span></span>  
 <span data-ttu-id="b046e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b046e-110">S_OK</span></span>  
 <span data-ttu-id="b046e-111">Êxito.</span><span class="sxs-lookup"><span data-stu-id="b046e-111">Success.</span></span>  
  
 <span data-ttu-id="b046e-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b046e-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="b046e-113">Não é possível alocar memória suficiente para `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="b046e-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="b046e-114">E_FAIL (ou outros códigos de retorno e _)</span><span class="sxs-lookup"><span data-stu-id="b046e-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="b046e-115">Outras falhas.</span><span class="sxs-lookup"><span data-stu-id="b046e-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b046e-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="b046e-116">Remarks</span></span>  
 <span data-ttu-id="b046e-117">Para liberar a memória alocada por esse método, chame o [icoreclrdebugtarget:: freeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="b046e-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b046e-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b046e-118">Requirements</span></span>  
 <span data-ttu-id="b046e-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b046e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b046e-120">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="b046e-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="b046e-121">**Biblioteca:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="b046e-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="b046e-122">**Versões do .NET framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="b046e-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b046e-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b046e-123">See also</span></span>

- [<span data-ttu-id="b046e-124">Interface ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="b046e-124">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
