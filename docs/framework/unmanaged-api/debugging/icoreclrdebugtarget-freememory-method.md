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
ms.openlocfilehash: 061a2b9990d4b4d6398d0a31b97bc403a5f10de4
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397166"
---
# <a name="icoreclrdebugtargetfreememory-method"></a><span data-ttu-id="c25a8-102">Método ICoreClrDebugTarget::FreeMemory</span><span class="sxs-lookup"><span data-stu-id="c25a8-102">ICoreClrDebugTarget::FreeMemory Method</span></span>
<span data-ttu-id="c25a8-103">Libera a memória alocada pelos métodos [ICoreClrDebugTarget:: EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) e [ICoreClrDebugTarget:: EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c25a8-103">Frees the memory allocated by the [ICoreClrDebugTarget::EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) and [ICoreClrDebugTarget::EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c25a8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c25a8-104">Syntax</span></span>  
  
```cpp  
void FreeMemory (  
     [in] void*pMemory);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c25a8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c25a8-105">Parameters</span></span>  
 `pMemory`  
 <span data-ttu-id="c25a8-106">no Um ponteiro para a matriz que é retornado pelo método [ICoreClrDebugTarget:: EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) ou [ICoreClrDebugTarget:: EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c25a8-106">[in] A pointer to the array that is returned by either the [ICoreClrDebugTarget::EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) or the [ICoreClrDebugTarget::EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c25a8-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c25a8-107">Requirements</span></span>  
 <span data-ttu-id="c25a8-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c25a8-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c25a8-109">**Cabeçalho:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="c25a8-109">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="c25a8-110">**Biblioteca:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="c25a8-110">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="c25a8-111">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="c25a8-111">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c25a8-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="c25a8-112">See also</span></span>

- [<span data-ttu-id="c25a8-113">Interface ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="c25a8-113">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
