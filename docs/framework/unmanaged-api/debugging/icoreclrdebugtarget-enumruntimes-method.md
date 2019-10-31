---
title: Método ICoreClrDebugTarget::EnumRuntimes
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumRuntimes
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumRuntimes
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget::EnumRuntimes method [Silverlight debugging]
- EnumRuntimes method, ICoreClrDebugTarget interface [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 316df866-442d-40cc-b049-45e8adcb65d1
topic_type:
- apiref
ms.openlocfilehash: 2579bed9ae432a2b9460c421c6ee5bdc40d1e149
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121831"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a><span data-ttu-id="42c1c-102">Método ICoreClrDebugTarget::EnumRuntimes</span><span class="sxs-lookup"><span data-stu-id="42c1c-102">ICoreClrDebugTarget::EnumRuntimes Method</span></span>
<span data-ttu-id="42c1c-103">Enumera os Common Language runtimes (CLRs) no processo especificado que está sendo executado em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="42c1c-103">Enumerates the common language runtimes (CLRs) in the specified process that is running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42c1c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42c1c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="42c1c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="42c1c-105">Parameters</span></span>  
 `dwInternalProcessID`  
 <span data-ttu-id="42c1c-106">no A ID do processo interno do processo para o qual você deseja enumerar os tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="42c1c-106">[in] The internal process ID of the process for which you want to enumerate runtimes.</span></span> <span data-ttu-id="42c1c-107">Isso será `m_dwInternalID` do [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)correspondente.</span><span class="sxs-lookup"><span data-stu-id="42c1c-107">This will be `m_dwInternalID` from the corresponding [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).</span></span>  
  
 `pcRuntimes`  
 <span data-ttu-id="42c1c-108">fora O número de tempos de execução retornados em `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="42c1c-108">[out] The number of runtimes returned in `ppRuntimes`.</span></span> <span data-ttu-id="42c1c-109">Esse valor pode ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="42c1c-109">This value can be 0 (zero).</span></span>  
  
 `ppRuntimes`  
 <span data-ttu-id="42c1c-110">fora Uma matriz de estruturas [CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) que representam os tempos de execução carregados no processo de destino remoto.</span><span class="sxs-lookup"><span data-stu-id="42c1c-110">[out] An array of [CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) structures that represent the runtimes loaded in the remote target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42c1c-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="42c1c-111">Return Value</span></span>  
 <span data-ttu-id="42c1c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="42c1c-112">S_OK</span></span>  
 <span data-ttu-id="42c1c-113">Êxito.</span><span class="sxs-lookup"><span data-stu-id="42c1c-113">Success.</span></span>  
  
 <span data-ttu-id="42c1c-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="42c1c-114">S_FALSE</span></span>  
 <span data-ttu-id="42c1c-115">`dwInternalProcessID` não corresponde a nenhum processo em execução no computador, provavelmente porque o processo foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="42c1c-115">`dwInternalProcessID` does not match any process that is running on the computer, probably because the process was terminated.</span></span> <span data-ttu-id="42c1c-116">`pcRuntimes` e `ppRuntimes` serão nulas.</span><span class="sxs-lookup"><span data-stu-id="42c1c-116">`pcRuntimes` and `ppRuntimes` will be null.</span></span>  
  
 <span data-ttu-id="42c1c-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="42c1c-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="42c1c-118">Não é possível alocar memória suficiente para `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="42c1c-118">Unable to allocate enough memory for `ppRuntimes`.</span></span>  
  
 <span data-ttu-id="42c1c-119">E_FAIL (ou outros códigos de retorno de E_)</span><span class="sxs-lookup"><span data-stu-id="42c1c-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="42c1c-120">Outras falhas.</span><span class="sxs-lookup"><span data-stu-id="42c1c-120">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42c1c-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="42c1c-121">Remarks</span></span>  
 <span data-ttu-id="42c1c-122">Para liberar a memória que foi alocada por esse método, chame o método [ICoreClrDebugTarget:: freememory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="42c1c-122">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42c1c-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="42c1c-123">Requirements</span></span>  
 <span data-ttu-id="42c1c-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42c1c-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42c1c-125">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="42c1c-125">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="42c1c-126">**Biblioteca:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="42c1c-126">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="42c1c-127">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="42c1c-127">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42c1c-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42c1c-128">See also</span></span>

- [<span data-ttu-id="42c1c-129">Interface ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="42c1c-129">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
