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
ms.openlocfilehash: 9f0fda803ba3a1ce35017d85e84b3bf6f567eda0
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976363"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="3b3f2-102">Método ICorDebugEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="3b3f2-102">ICorDebugEnum::Clone Method</span></span>
<span data-ttu-id="3b3f2-103">Cria uma cópia deste objeto ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="3b3f2-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b3f2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3b3f2-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b3f2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3b3f2-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="3b3f2-106">fora Um ponteiro para o endereço de um `ICorDebugEnum` objeto que é uma cópia desse `ICorDebugEnum` objeto.</span><span class="sxs-lookup"><span data-stu-id="3b3f2-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b3f2-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3b3f2-107">Requirements</span></span>  
 <span data-ttu-id="3b3f2-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b3f2-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b3f2-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b3f2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b3f2-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b3f2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b3f2-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b3f2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
