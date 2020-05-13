---
title: Método ICorDebugModule::IsDynamic
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsDynamic
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type:
- apiref
ms.openlocfilehash: 4517f266bbb500223214a6a8fe5881e8b29566c3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206890"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="7b7ef-102">Método ICorDebugModule::IsDynamic</span><span class="sxs-lookup"><span data-stu-id="7b7ef-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="7b7ef-103">Obtém um valor que indica se este módulo é dinâmico.</span><span class="sxs-lookup"><span data-stu-id="7b7ef-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b7ef-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b7ef-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b7ef-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7b7ef-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="7b7ef-106">[fora] `true` Se esse módulo for dinâmico; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="7b7ef-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b7ef-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="7b7ef-107">Remarks</span></span>  
 <span data-ttu-id="7b7ef-108">Um módulo dinâmico pode adicionar novas classes e excluir classes existentes mesmo depois que o módulo tiver sido carregado.</span><span class="sxs-lookup"><span data-stu-id="7b7ef-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="7b7ef-109">Os retornos de chamada [ICorDebugManagedCallback:: LoadClass](icordebugmanagedcallback-loadclass-method.md) e [ICorDebugManagedCallback:: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) informam ao depurador quando uma classe foi adicionada ou excluída.</span><span class="sxs-lookup"><span data-stu-id="7b7ef-109">The [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b7ef-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7b7ef-110">Requirements</span></span>  
 <span data-ttu-id="7b7ef-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b7ef-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b7ef-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b7ef-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b7ef-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b7ef-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b7ef-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b7ef-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
