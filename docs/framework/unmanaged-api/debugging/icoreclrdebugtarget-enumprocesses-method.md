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
ms.openlocfilehash: 0c1b18f24fd30b5f6d5e85633fc0c25839aba6df
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396416"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="776e3-102">Método ICoreClrDebugTarget::EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="776e3-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="776e3-103">Enumera os processos que estão sendo executados em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="776e3-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="776e3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="776e3-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="776e3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="776e3-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="776e3-106">fora O número de processos retornados em `ppProcs` .</span><span class="sxs-lookup"><span data-stu-id="776e3-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="776e3-107">Esse valor pode ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="776e3-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="776e3-108">fora Uma matriz de estruturas [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) que representam os processos em execução no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="776e3-108">[out] An array of [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="776e3-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="776e3-109">Return Value</span></span>  
 <span data-ttu-id="776e3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="776e3-110">S_OK</span></span>  
 <span data-ttu-id="776e3-111">Êxito.</span><span class="sxs-lookup"><span data-stu-id="776e3-111">Success.</span></span>  
  
 <span data-ttu-id="776e3-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="776e3-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="776e3-113">Não é possível alocar memória suficiente para `ppProcs` .</span><span class="sxs-lookup"><span data-stu-id="776e3-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="776e3-114">E_FAIL (ou outros códigos de retorno de E_)</span><span class="sxs-lookup"><span data-stu-id="776e3-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="776e3-115">Outras falhas.</span><span class="sxs-lookup"><span data-stu-id="776e3-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="776e3-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="776e3-116">Remarks</span></span>  
 <span data-ttu-id="776e3-117">Para liberar a memória que foi alocada por esse método, chame o método [ICoreClrDebugTarget:: freememory](icoreclrdebugtarget-freememory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="776e3-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="776e3-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="776e3-118">Requirements</span></span>  
 <span data-ttu-id="776e3-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="776e3-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="776e3-120">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="776e3-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="776e3-121">**Biblioteca:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="776e3-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="776e3-122">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="776e3-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="776e3-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="776e3-123">See also</span></span>

- [<span data-ttu-id="776e3-124">Interface ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="776e3-124">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
