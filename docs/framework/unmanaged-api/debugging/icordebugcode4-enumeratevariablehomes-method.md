---
title: "Método ICorDebugCode4::EnumerateVariableHomes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugCode4.EnumerateVariableHomes
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4623f4bb1af21d19446b4e0f65dd5d826c412ccd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="2ec0d-102">Método ICorDebugCode4::EnumerateVariableHomes</span><span class="sxs-lookup"><span data-stu-id="2ec0d-102">ICorDebugCode4::EnumerateVariableHomes Method</span></span>
<span data-ttu-id="2ec0d-103">Obtém um enumerador para os argumentos e variáveis locais em uma função.</span><span class="sxs-lookup"><span data-stu-id="2ec0d-103">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ec0d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2ec0d-104">Syntax</span></span>  
  
```  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ec0d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2ec0d-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="2ec0d-106">Um ponteiro para o endereço de um [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) objeto de interface que é um enumerador para a variáveis locais e os argumentos em uma função.</span><span class="sxs-lookup"><span data-stu-id="2ec0d-106">A pointer to the address of an [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ec0d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="2ec0d-107">Remarks</span></span>  
 <span data-ttu-id="2ec0d-108">O [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) objeto de interface é um enumerador padrão derivado da interface "ICorDebugEnum" que permite que você enumere [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objetos.</span><span class="sxs-lookup"><span data-stu-id="2ec0d-108">The [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="2ec0d-109">A coleção pode incluir vários [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objetos para o índice de slot ou argumento mesmo se eles tiverem diferentes residências em pontos diferentes na função.</span><span class="sxs-lookup"><span data-stu-id="2ec0d-109">The collection may include multiple [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ec0d-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2ec0d-110">Requirements</span></span>  
 <span data-ttu-id="2ec0d-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ec0d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ec0d-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ec0d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ec0d-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ec0d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ec0d-114">**Versões do .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ec0d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ec0d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ec0d-115">See Also</span></span>  
 [<span data-ttu-id="2ec0d-116">Interface ICorDebugCode4</span><span class="sxs-lookup"><span data-stu-id="2ec0d-116">ICorDebugCode4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 [<span data-ttu-id="2ec0d-117">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="2ec0d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
