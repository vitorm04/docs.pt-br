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
ms.openlocfilehash: aef12634da477e72757e98e520b600ec1ee0f1b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412159"
---
# <a name="icordebugfunctiongetmodule-method"></a><span data-ttu-id="c8e6c-102">Método ICorDebugFunction::GetModule</span><span class="sxs-lookup"><span data-stu-id="c8e6c-102">ICorDebugFunction::GetModule Method</span></span>
<span data-ttu-id="c8e6c-103">Obtém o módulo no qual a função é definida.</span><span class="sxs-lookup"><span data-stu-id="c8e6c-103">Gets the module in which this function is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8e6c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8e6c-104">Syntax</span></span>  
  
```  
HRESULT GetModule (  
    [out] ICorDebugModule **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8e6c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c8e6c-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="c8e6c-106">[out] Um ponteiro para o endereço de um objeto ICorDebugModule que representa o módulo no qual a função é definida.</span><span class="sxs-lookup"><span data-stu-id="c8e6c-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this function is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8e6c-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c8e6c-107">Requirements</span></span>  
 <span data-ttu-id="c8e6c-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8e6c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8e6c-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8e6c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8e6c-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8e6c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8e6c-111">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8e6c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
