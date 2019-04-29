---
title: Método ICorDebugCode::GetVersionNumber
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetVersionNumber
helpviewer_keywords:
- GetVersionNumber method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetVersionNumber method [.NET Framework debugging]
ms.assetid: c8e02518-679f-4e9f-8a28-ba4a89a3876f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 003b29501e8f22ed9010a9f16a4f7ee67bce03a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750131"
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="b1df6-102">Método ICorDebugCode::GetVersionNumber</span><span class="sxs-lookup"><span data-stu-id="b1df6-102">ICorDebugCode::GetVersionNumber Method</span></span>
<span data-ttu-id="b1df6-103">Obtém o baseado em um número que identifica a versão do código que representa essa "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="b1df6-103">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1df6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1df6-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32    *nVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1df6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b1df6-105">Parameters</span></span>  
 `nVersion`  
 <span data-ttu-id="b1df6-106">[out] Um ponteiro para o número de versão do código.</span><span class="sxs-lookup"><span data-stu-id="b1df6-106">[out] A pointer to the version number of the code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1df6-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1df6-107">Remarks</span></span>  
 <span data-ttu-id="b1df6-108">O número de versão é incrementado toda vez que uma operação de editar e continuar de (EnC) é executada no código.</span><span class="sxs-lookup"><span data-stu-id="b1df6-108">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1df6-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b1df6-109">Requirements</span></span>  
 <span data-ttu-id="b1df6-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1df6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1df6-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1df6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1df6-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1df6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1df6-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1df6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1df6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1df6-114">See also</span></span>
