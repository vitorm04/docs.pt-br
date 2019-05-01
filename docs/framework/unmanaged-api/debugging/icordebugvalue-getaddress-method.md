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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac550ee7b1d66612557b30d15c275c90cf09b8af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986850"
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="10de1-102">Método ICorDebugValue::GetAddress</span><span class="sxs-lookup"><span data-stu-id="10de1-102">ICorDebugValue::GetAddress Method</span></span>
<span data-ttu-id="10de1-103">Obtém o endereço do objeto "ICorDebugValue", que está no processo que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="10de1-103">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10de1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10de1-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10de1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="10de1-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="10de1-106">[out] Ponteiro para um `CORDB_ADDRESS` objeto que especifica o endereço desse objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="10de1-106">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10de1-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="10de1-107">Remarks</span></span>  
 <span data-ttu-id="10de1-108">Se o valor não estiver disponível, 0 (zero) será retornado.</span><span class="sxs-lookup"><span data-stu-id="10de1-108">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="10de1-109">Isso pode ocorrer se o valor for pelo menos parcialmente em registros ou armazenados em um identificador do coletor de lixo (`GCHandle`).</span><span class="sxs-lookup"><span data-stu-id="10de1-109">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10de1-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="10de1-110">Requirements</span></span>  
 <span data-ttu-id="10de1-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10de1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10de1-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10de1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10de1-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10de1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10de1-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10de1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10de1-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10de1-115">See also</span></span>
