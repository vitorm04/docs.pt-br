---
title: Método ICorDebugFunction::GetModule
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetModule
helpviewer_keywords:
- ICorDebugFunction::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 5031a5d3-2564-412a-9007-e36d4631308a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6bfde8a934da857e580c603bd1c0115a04a4070
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754637"
---
# <a name="icordebugfunctiongetmodule-method"></a><span data-ttu-id="ab7b6-102">Método ICorDebugFunction::GetModule</span><span class="sxs-lookup"><span data-stu-id="ab7b6-102">ICorDebugFunction::GetModule Method</span></span>
<span data-ttu-id="ab7b6-103">Obtém o módulo no qual essa função é definida.</span><span class="sxs-lookup"><span data-stu-id="ab7b6-103">Gets the module in which this function is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab7b6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ab7b6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab7b6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ab7b6-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="ab7b6-106">[out] Um ponteiro para o endereço de um objeto ICorDebugModule que representa o módulo no qual essa função é definida.</span><span class="sxs-lookup"><span data-stu-id="ab7b6-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this function is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab7b6-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ab7b6-107">Requirements</span></span>  
 <span data-ttu-id="ab7b6-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab7b6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab7b6-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab7b6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab7b6-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab7b6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab7b6-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab7b6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
