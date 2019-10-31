---
title: Método ICorDebugEnum::Clone
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Clone
helpviewer_keywords:
- Clone method, ICorDebugEnum interface [.NET Framework debugging]
- ICorDebugEnum::Clone method [.NET Framework debugging]
ms.assetid: 57eefaf3-75cf-4496-bc94-88c0706861b7
topic_type:
- apiref
ms.openlocfilehash: 2ec769c343ad055132c6d84e64600fc459357a85
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124706"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="e477d-102">Método ICorDebugEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="e477d-102">ICorDebugEnum::Clone Method</span></span>
<span data-ttu-id="e477d-103">Cria uma cópia deste objeto ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="e477d-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e477d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e477d-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e477d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e477d-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="e477d-106">fora Um ponteiro para o endereço de um objeto de `ICorDebugEnum` que é uma cópia desse objeto `ICorDebugEnum`.</span><span class="sxs-lookup"><span data-stu-id="e477d-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e477d-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e477d-107">Requirements</span></span>  
 <span data-ttu-id="e477d-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e477d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e477d-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e477d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e477d-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e477d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e477d-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e477d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
