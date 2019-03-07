---
title: Método ICorDebugClass::GetToken
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetToken
helpviewer_keywords:
- GetToken method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetToken method [.NET Framework debugging]
ms.assetid: ee5c848a-eac4-4462-b07a-07ccd76a75df
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7532c34dca070b07bd3124002eaf72a2f939238
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493057"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="05654-102">Método ICorDebugClass::GetToken</span><span class="sxs-lookup"><span data-stu-id="05654-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="05654-103">Obtém o `TypeDef` token de metadados que faz referência a definição dessa classe.</span><span class="sxs-lookup"><span data-stu-id="05654-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05654-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="05654-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05654-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="05654-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="05654-106">[out] Um ponteiro para um `mdTypeDef` token que faz referência a definição dessa classe.</span><span class="sxs-lookup"><span data-stu-id="05654-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05654-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="05654-107">Requirements</span></span>  
 <span data-ttu-id="05654-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05654-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05654-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05654-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05654-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05654-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05654-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05654-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05654-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05654-112">See also</span></span>
- [<span data-ttu-id="05654-113">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="05654-113">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
