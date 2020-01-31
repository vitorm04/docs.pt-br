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
ms.openlocfilehash: 4b55ac1d895bfecbe74be447bd06f4aa22b9d04f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790787"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a><span data-ttu-id="155a0-102">Método ICoreClrDebugTarget::EnumRuntimes</span><span class="sxs-lookup"><span data-stu-id="155a0-102">ICoreClrDebugTarget::EnumRuntimes Method</span></span>
<span data-ttu-id="155a0-103">Enumera os Common Language runtimes (CLRs) no processo especificado que está sendo executado em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="155a0-103">Enumerates the common language runtimes (CLRs) in the specified process that is running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="155a0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="155a0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="155a0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="155a0-105">Parameters</span></span>  
 `dwInternalProcessID`  
 <span data-ttu-id="155a0-106">no A ID do processo interno do processo para o qual você deseja enumerar os tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="155a0-106">[in] The internal process ID of the process for which you want to enumerate runtimes.</span></span> <span data-ttu-id="155a0-107">Isso será `m_dwInternalID` do [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md)correspondente.</span><span class="sxs-lookup"><span data-stu-id="155a0-107">This will be `m_dwInternalID` from the corresponding [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md).</span></span>  
  
 `pcRuntimes`  
 <span data-ttu-id="155a0-108">fora O número de tempos de execução retornados em `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="155a0-108">[out] The number of runtimes returned in `ppRuntimes`.</span></span> <span data-ttu-id="155a0-109">Esse valor pode ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="155a0-109">This value can be 0 (zero).</span></span>  
  
 `ppRuntimes`  
 <span data-ttu-id="155a0-110">fora Uma matriz de estruturas [CoreClrDebugRuntimeInfo](coreclrdebugruntimeinfo-structure.md) que representam os tempos de execução carregados no processo de destino remoto.</span><span class="sxs-lookup"><span data-stu-id="155a0-110">[out] An array of [CoreClrDebugRuntimeInfo](coreclrdebugruntimeinfo-structure.md) structures that represent the runtimes loaded in the remote target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="155a0-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="155a0-111">Return Value</span></span>  
 <span data-ttu-id="155a0-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="155a0-112">S_OK</span></span>  
 <span data-ttu-id="155a0-113">Êxito.</span><span class="sxs-lookup"><span data-stu-id="155a0-113">Success.</span></span>  
  
 <span data-ttu-id="155a0-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="155a0-114">S_FALSE</span></span>  
 <span data-ttu-id="155a0-115">`dwInternalProcessID` não corresponde a nenhum processo em execução no computador, provavelmente porque o processo foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="155a0-115">`dwInternalProcessID` does not match any process that is running on the computer, probably because the process was terminated.</span></span> <span data-ttu-id="155a0-116">`pcRuntimes` e `ppRuntimes` serão nulas.</span><span class="sxs-lookup"><span data-stu-id="155a0-116">`pcRuntimes` and `ppRuntimes` will be null.</span></span>  
  
 <span data-ttu-id="155a0-117">{1&gt;E_OUTOFMEMORY&lt;1}</span><span class="sxs-lookup"><span data-stu-id="155a0-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="155a0-118">Não é possível alocar memória suficiente para `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="155a0-118">Unable to allocate enough memory for `ppRuntimes`.</span></span>  
  
 <span data-ttu-id="155a0-119">E_FAIL (ou outros códigos de retorno de E_)</span><span class="sxs-lookup"><span data-stu-id="155a0-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="155a0-120">Outras falhas.</span><span class="sxs-lookup"><span data-stu-id="155a0-120">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="155a0-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="155a0-121">Remarks</span></span>  
 <span data-ttu-id="155a0-122">Para liberar a memória que foi alocada por esse método, chame o método [ICoreClrDebugTarget:: freememory](icoreclrdebugtarget-freememory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="155a0-122">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="155a0-123">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="155a0-123">Requirements</span></span>  
 <span data-ttu-id="155a0-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="155a0-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="155a0-125">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="155a0-125">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="155a0-126">**Biblioteca:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="155a0-126">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="155a0-127">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="155a0-127">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="155a0-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="155a0-128">See also</span></span>

- [<span data-ttu-id="155a0-129">Interface ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="155a0-129">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
