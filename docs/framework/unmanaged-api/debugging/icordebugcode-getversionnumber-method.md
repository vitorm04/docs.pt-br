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
ms.openlocfilehash: a3d4609d79bb424cabc011122480f952f0f877f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411228"
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="03004-102">Método ICorDebugCode::GetVersionNumber</span><span class="sxs-lookup"><span data-stu-id="03004-102">ICorDebugCode::GetVersionNumber Method</span></span>
<span data-ttu-id="03004-103">Obtém o baseado em um número que identifica a versão do código que representa essa "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="03004-103">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03004-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03004-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32    *nVersion  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03004-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="03004-105">Parameters</span></span>  
 `nVersion`  
 <span data-ttu-id="03004-106">[out] Um ponteiro para o número de versão do código.</span><span class="sxs-lookup"><span data-stu-id="03004-106">[out] A pointer to the version number of the code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03004-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="03004-107">Remarks</span></span>  
 <span data-ttu-id="03004-108">O número de versão é incrementado toda vez que uma operação de (EnC) edit-and-continue é executada no código.</span><span class="sxs-lookup"><span data-stu-id="03004-108">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03004-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="03004-109">Requirements</span></span>  
 <span data-ttu-id="03004-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03004-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03004-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="03004-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03004-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03004-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03004-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03004-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03004-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03004-114">See Also</span></span>  
 
