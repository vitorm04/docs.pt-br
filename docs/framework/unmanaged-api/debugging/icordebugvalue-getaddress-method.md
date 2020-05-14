---
title: Método ICorDebugValue::GetAddress
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
ms.openlocfilehash: 467ba53f90081f0c3499fb22acab96b5e380a3f4
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395839"
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="30bb2-102">Método ICorDebugValue::GetAddress</span><span class="sxs-lookup"><span data-stu-id="30bb2-102">ICorDebugValue::GetAddress Method</span></span>
<span data-ttu-id="30bb2-103">Obtém o endereço desse objeto "ICorDebugValue", que está no processo de ser depurado.</span><span class="sxs-lookup"><span data-stu-id="30bb2-103">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30bb2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30bb2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30bb2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="30bb2-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="30bb2-106">fora Ponteiro para um `CORDB_ADDRESS` objeto que especifica o endereço desse objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="30bb2-106">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30bb2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="30bb2-107">Remarks</span></span>  
 <span data-ttu-id="30bb2-108">Se o valor não estiver disponível, será retornado 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="30bb2-108">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="30bb2-109">Isso pode acontecer se o valor for pelo menos parcialmente em registros ou armazenado em um identificador de coletor de lixo ( `GCHandle` ).</span><span class="sxs-lookup"><span data-stu-id="30bb2-109">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30bb2-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30bb2-110">Requirements</span></span>  
 <span data-ttu-id="30bb2-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30bb2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30bb2-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30bb2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30bb2-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30bb2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30bb2-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30bb2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30bb2-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="30bb2-115">See also</span></span>
