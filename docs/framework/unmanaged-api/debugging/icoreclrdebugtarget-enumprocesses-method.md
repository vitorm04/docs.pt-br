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
ms.openlocfilehash: 11b1072b3467f7d0a3f223fbc2151ec9ccf461ad
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790799"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="fc881-102">Método ICoreClrDebugTarget::EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="fc881-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="fc881-103">Enumera os processos que estão sendo executados em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="fc881-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc881-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc881-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc881-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fc881-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="fc881-106">fora O número de processos retornados em `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="fc881-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="fc881-107">Esse valor pode ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="fc881-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="fc881-108">fora Uma matriz de estruturas [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) que representam os processos em execução no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="fc881-108">[out] An array of [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc881-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="fc881-109">Return Value</span></span>  
 <span data-ttu-id="fc881-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc881-110">S_OK</span></span>  
 <span data-ttu-id="fc881-111">Êxito.</span><span class="sxs-lookup"><span data-stu-id="fc881-111">Success.</span></span>  
  
 <span data-ttu-id="fc881-112">{1&gt;E_OUTOFMEMORY&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fc881-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="fc881-113">Não é possível alocar memória suficiente para `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="fc881-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="fc881-114">E_FAIL (ou outros códigos de retorno de E_)</span><span class="sxs-lookup"><span data-stu-id="fc881-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="fc881-115">Outras falhas.</span><span class="sxs-lookup"><span data-stu-id="fc881-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc881-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="fc881-116">Remarks</span></span>  
 <span data-ttu-id="fc881-117">Para liberar a memória que foi alocada por esse método, chame o método [ICoreClrDebugTarget:: freememory](icoreclrdebugtarget-freememory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fc881-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc881-118">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="fc881-118">Requirements</span></span>  
 <span data-ttu-id="fc881-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc881-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc881-120">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="fc881-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="fc881-121">**Biblioteca:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="fc881-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="fc881-122">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="fc881-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc881-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="fc881-123">See also</span></span>

- [<span data-ttu-id="fc881-124">Interface ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="fc881-124">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
