---
title: Método ICorDebugAssembly::EnumerateModules
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.EnumerateModules
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::EnumerateModules
helpviewer_keywords:
- ICorDebugAssembly::EnumerateModules method [.NET Framework debugging]
- EnumerateModules method [.NET Framework debugging]
ms.assetid: c7ba51a1-0dd5-4452-b471-232febe0f897
topic_type:
- apiref
ms.openlocfilehash: 12dc5466d5be73b327f171c389c41c55901f2915
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894949"
---
# <a name="icordebugassemblyenumeratemodules-method"></a><span data-ttu-id="8eee7-102">Método ICorDebugAssembly::EnumerateModules</span><span class="sxs-lookup"><span data-stu-id="8eee7-102">ICorDebugAssembly::EnumerateModules Method</span></span>
<span data-ttu-id="8eee7-103">Obtém um enumerador para os módulos contidos no `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="8eee7-103">Gets an enumerator for the modules contained in the `ICorDebugAssembly`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eee7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8eee7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateModules (  
    [out] ICorDebugModuleEnum **ppModules  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8eee7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8eee7-105">Parameters</span></span>  
 `ppModules`  
 <span data-ttu-id="8eee7-106">fora Um ponteiro para o endereço da interface ICorDebugModuleEnum que é o enumerador.</span><span class="sxs-lookup"><span data-stu-id="8eee7-106">[out] A pointer to the address of the ICorDebugModuleEnum interface that is the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8eee7-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8eee7-107">Requirements</span></span>  
 <span data-ttu-id="8eee7-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8eee7-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8eee7-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8eee7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8eee7-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8eee7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8eee7-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8eee7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
