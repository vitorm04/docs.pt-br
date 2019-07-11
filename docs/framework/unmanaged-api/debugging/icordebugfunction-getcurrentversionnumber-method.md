---
title: Método ICorDebugFunction::GetCurrentVersionNumber
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetCurrentVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be66e0e2c9aff788d1003878891b8d64d6353500
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754704"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="38880-102">Método ICorDebugFunction::GetCurrentVersionNumber</span><span class="sxs-lookup"><span data-stu-id="38880-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>
<span data-ttu-id="38880-103">Obtém o número de versão da edição mais recente feita na função representada por esse objeto ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="38880-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38880-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38880-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38880-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="38880-105">Parameters</span></span>  
 `pnCurrentVersion`  
 <span data-ttu-id="38880-106">[out] Um ponteiro para um valor inteiro que é o número de versão da edição mais recente feita para essa função.</span><span class="sxs-lookup"><span data-stu-id="38880-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38880-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="38880-107">Remarks</span></span>  
 <span data-ttu-id="38880-108">O número de versão da edição mais recente feita para essa função pode ser maior que o número de versão da função em si.</span><span class="sxs-lookup"><span data-stu-id="38880-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="38880-109">Use o [ICorDebugFunction2::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) método ou o [icordebugcode:: Getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) método para recuperar o número de versão da função.</span><span class="sxs-lookup"><span data-stu-id="38880-109">Use either the [ICorDebugFunction2::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38880-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38880-110">Requirements</span></span>  
 <span data-ttu-id="38880-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38880-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38880-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38880-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38880-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38880-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38880-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38880-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
