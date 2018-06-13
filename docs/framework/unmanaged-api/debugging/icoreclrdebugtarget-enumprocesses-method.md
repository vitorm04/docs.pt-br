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
ms.openlocfilehash: c09b70b5afb0561d32e55dd89df6cac083abc068
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422010"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="45477-102">Método ICoreClrDebugTarget::EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="45477-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="45477-103">Enumera os processos em execução em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="45477-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45477-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45477-104">Syntax</span></span>  
  
```  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45477-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="45477-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="45477-106">[out] O número de processos retornados em `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="45477-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="45477-107">Esse valor pode ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="45477-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="45477-108">[out] Uma matriz de [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) estruturas que representam os processos em execução no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="45477-108">[out] An array of [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45477-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="45477-109">Return Value</span></span>  
 <span data-ttu-id="45477-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="45477-110">S_OK</span></span>  
 <span data-ttu-id="45477-111">Êxito.</span><span class="sxs-lookup"><span data-stu-id="45477-111">Success.</span></span>  
  
 <span data-ttu-id="45477-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="45477-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="45477-113">Não é possível alocar memória suficiente para `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="45477-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="45477-114">E_FAIL (ou outros códigos de retorno E_)</span><span class="sxs-lookup"><span data-stu-id="45477-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="45477-115">Outras falhas.</span><span class="sxs-lookup"><span data-stu-id="45477-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45477-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="45477-116">Remarks</span></span>  
 <span data-ttu-id="45477-117">Para liberar a memória que foi alocada por esse método, chame o [Icoreclrdebugtarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="45477-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45477-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="45477-118">Requirements</span></span>  
 <span data-ttu-id="45477-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45477-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45477-120">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="45477-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="45477-121">**Biblioteca:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="45477-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="45477-122">**Versões do .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="45477-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45477-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45477-123">See Also</span></span>  
 [<span data-ttu-id="45477-124">Interface ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="45477-124">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
