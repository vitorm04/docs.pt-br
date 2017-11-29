---
title: "Método ICorDebugProcess5::GetTypeLayout"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetTypeLayout
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetTypeLayout
helpviewer_keywords:
- ICorDebugProcess5::GetTypeLayout method [.NET Framework debugging]
- GetTypeLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: bd62f5d1-e874-41f1-81e5-a29a7572c15d
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2f36b78558f8a8005735166436ad3dead28992e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5gettypelayout-method"></a><span data-ttu-id="e7336-102">Método ICorDebugProcess5::GetTypeLayout</span><span class="sxs-lookup"><span data-stu-id="e7336-102">ICorDebugProcess5::GetTypeLayout Method</span></span>
<span data-ttu-id="e7336-103">Obtém informações sobre o layout de um objeto na memória com base em seu identificador de tipo.</span><span class="sxs-lookup"><span data-stu-id="e7336-103">Gets information about the layout of an object in memory based on its type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7336-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e7336-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7336-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e7336-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="e7336-106">[in] Um [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token que especifica o tipo cujo layout é desejado.</span><span class="sxs-lookup"><span data-stu-id="e7336-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the type whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="e7336-107">[out] Um ponteiro para um [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) estrutura que contém informações sobre o layout do objeto na memória.</span><span class="sxs-lookup"><span data-stu-id="e7336-107">[out] A pointer to a [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure that contains information about the layout of the object in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7336-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="e7336-108">Remarks</span></span>  
 <span data-ttu-id="e7336-109">O `ICorDebugProcess5::GetTypeLayout` método fornece informações sobre um objeto com base em seu [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), que é retornado por um número de outros [ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) métodos.</span><span class="sxs-lookup"><span data-stu-id="e7336-109">The `ICorDebugProcess5::GetTypeLayout` method provides information about an object based on its [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which is returned by a number of other [ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) methods.</span></span> <span data-ttu-id="e7336-110">As informações são fornecidas por um [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) estrutura que é preenchida pelo método.</span><span class="sxs-lookup"><span data-stu-id="e7336-110">The information is provided by a [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure that is populated by the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7336-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e7336-111">Requirements</span></span>  
 <span data-ttu-id="e7336-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7336-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7336-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7336-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7336-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7336-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7336-115">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7336-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7336-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7336-116">See Also</span></span>  
 [<span data-ttu-id="e7336-117">Estrutura COR_TYPE_LAYOUT</span><span class="sxs-lookup"><span data-stu-id="e7336-117">COR_TYPE_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 [<span data-ttu-id="e7336-118">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="e7336-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="e7336-119">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="e7336-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
