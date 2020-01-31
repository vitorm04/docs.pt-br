---
title: Método ICoreClrDebugTarget::FreeMemory
ms.date: 03/30/2017
api_name:
- ICoreDebugTarget.FreeMemory
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::FreeMemory
helpviewer_keywords:
- remote debugging API [Silverlight]
- FreeMemory method, ICoreClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::FreeMemory method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 98f2a0db-a6ec-4f9b-861d-f82485237d08
topic_type:
- apiref
ms.openlocfilehash: cfa313d286d0decad82f51bcedc582470549c8e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790780"
---
# <a name="icoreclrdebugtargetfreememory-method"></a><span data-ttu-id="d6048-102">Método ICoreClrDebugTarget::FreeMemory</span><span class="sxs-lookup"><span data-stu-id="d6048-102">ICoreClrDebugTarget::FreeMemory Method</span></span>
<span data-ttu-id="d6048-103">Libera a memória alocada pelos métodos [ICoreClrDebugTarget:: EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) e [ICoreClrDebugTarget:: EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d6048-103">Frees the memory allocated by the [ICoreClrDebugTarget::EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) and [ICoreClrDebugTarget::EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6048-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6048-104">Syntax</span></span>  
  
```cpp  
void FreeMemory (  
     [in] void*pMemory);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6048-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d6048-105">Parameters</span></span>  
 `pMemory`  
 <span data-ttu-id="d6048-106">no Um ponteiro para a matriz que é retornado pelo método [ICoreClrDebugTarget:: EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) ou [ICoreClrDebugTarget:: EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d6048-106">[in] A pointer to the array that is returned by either the [ICoreClrDebugTarget::EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) or the [ICoreClrDebugTarget::EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6048-107">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="d6048-107">Requirements</span></span>  
 <span data-ttu-id="d6048-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6048-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6048-109">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="d6048-109">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="d6048-110">**Biblioteca:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="d6048-110">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="d6048-111">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="d6048-111">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6048-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="d6048-112">See also</span></span>

- [<span data-ttu-id="d6048-113">Interface ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="d6048-113">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
