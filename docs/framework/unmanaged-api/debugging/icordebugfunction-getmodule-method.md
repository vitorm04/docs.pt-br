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
ms.openlocfilehash: 41ad10fecca2ba1831d9e0d1120d3d1be0be92ad
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212952"
---
# <a name="icordebugfunctiongetmodule-method"></a><span data-ttu-id="3c478-102">Método ICorDebugFunction::GetModule</span><span class="sxs-lookup"><span data-stu-id="3c478-102">ICorDebugFunction::GetModule Method</span></span>
<span data-ttu-id="3c478-103">Obtém o módulo no qual essa função é definida.</span><span class="sxs-lookup"><span data-stu-id="3c478-103">Gets the module in which this function is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c478-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3c478-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c478-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3c478-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="3c478-106">fora Um ponteiro para o endereço de um objeto ICorDebugModule que representa o módulo no qual essa função é definida.</span><span class="sxs-lookup"><span data-stu-id="3c478-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this function is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c478-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3c478-107">Requirements</span></span>  
 <span data-ttu-id="3c478-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c478-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c478-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c478-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c478-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c478-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c478-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c478-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
