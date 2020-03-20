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
ms.openlocfilehash: 6484832e8e737b9a0d0b3eaf3ede4078729f7a4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178432"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="8c58b-102">Método ICoreClrDebugTarget::EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="8c58b-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="8c58b-103">Enumera os processos que estão sendo executados em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="8c58b-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c58b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c58b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c58b-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="8c58b-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="8c58b-106">[fora] O número de processos `ppProcs`retornados em .</span><span class="sxs-lookup"><span data-stu-id="8c58b-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="8c58b-107">Este valor pode ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="8c58b-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="8c58b-108">[fora] Um conjunto de estruturas [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) que representam os processos em execução no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="8c58b-108">[out] An array of [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c58b-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="8c58b-109">Return Value</span></span>  
 <span data-ttu-id="8c58b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c58b-110">S_OK</span></span>  
 <span data-ttu-id="8c58b-111">Sucesso.</span><span class="sxs-lookup"><span data-stu-id="8c58b-111">Success.</span></span>  
  
 <span data-ttu-id="8c58b-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8c58b-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="8c58b-113">Não é possível `ppProcs`alocar memória suficiente para .</span><span class="sxs-lookup"><span data-stu-id="8c58b-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="8c58b-114">E_FAIL (ou outros códigos de retorno E_)</span><span class="sxs-lookup"><span data-stu-id="8c58b-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="8c58b-115">Outras falhas.</span><span class="sxs-lookup"><span data-stu-id="8c58b-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c58b-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c58b-116">Remarks</span></span>  
 <span data-ttu-id="8c58b-117">Para liberar a memória alocada por este método, ligue para o [método ICoreClrDebugTarget:::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="8c58b-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c58b-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8c58b-118">Requirements</span></span>  
 <span data-ttu-id="8c58b-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c58b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c58b-120">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="8c58b-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="8c58b-121">**Biblioteca:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="8c58b-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="8c58b-122">**.NET Framework Versões:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="8c58b-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c58b-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="8c58b-123">See also</span></span>

- [<span data-ttu-id="8c58b-124">Interface ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="8c58b-124">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
