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
ms.openlocfilehash: 98758ce2c1fb0373ce5a94ad153c0f07144616e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729888"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="b1a09-102">Método ICoreClrDebugTarget::EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="b1a09-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="b1a09-103">Enumera os processos que estão em execução em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="b1a09-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1a09-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1a09-104">Syntax</span></span>  
  
```  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1a09-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b1a09-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="b1a09-106">[out] O número de processos retornados em `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="b1a09-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="b1a09-107">Esse valor pode ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="b1a09-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="b1a09-108">[out] Uma matriz de [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) estruturas que representam os processos em execução no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="b1a09-108">[out] An array of [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1a09-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b1a09-109">Return Value</span></span>  
 <span data-ttu-id="b1a09-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b1a09-110">S_OK</span></span>  
 <span data-ttu-id="b1a09-111">Êxito.</span><span class="sxs-lookup"><span data-stu-id="b1a09-111">Success.</span></span>  
  
 <span data-ttu-id="b1a09-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b1a09-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="b1a09-113">Não é possível alocar memória suficiente para `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="b1a09-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="b1a09-114">E_FAIL (ou outros códigos de retorno e _)</span><span class="sxs-lookup"><span data-stu-id="b1a09-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="b1a09-115">Outras falhas.</span><span class="sxs-lookup"><span data-stu-id="b1a09-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1a09-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1a09-116">Remarks</span></span>  
 <span data-ttu-id="b1a09-117">Para liberar a memória alocada por esse método, chame o [icoreclrdebugtarget:: freeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="b1a09-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1a09-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b1a09-118">Requirements</span></span>  
 <span data-ttu-id="b1a09-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1a09-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1a09-120">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="b1a09-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="b1a09-121">**Biblioteca:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="b1a09-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="b1a09-122">**Versões do .NET framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="b1a09-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1a09-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1a09-123">See also</span></span>
- [<span data-ttu-id="b1a09-124">Interface ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="b1a09-124">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
