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
ms.openlocfilehash: c4f33bb15a351be5fe8318dcc3339d429dec039e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183697"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="312e0-102">Método ICorDebugClass::GetToken</span><span class="sxs-lookup"><span data-stu-id="312e0-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="312e0-103">Obtém o `TypeDef` token de metadados que faz referência a definição dessa classe.</span><span class="sxs-lookup"><span data-stu-id="312e0-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="312e0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="312e0-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="312e0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="312e0-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="312e0-106">[out] Um ponteiro para um `mdTypeDef` token que faz referência a definição dessa classe.</span><span class="sxs-lookup"><span data-stu-id="312e0-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="312e0-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="312e0-107">Requirements</span></span>  
 <span data-ttu-id="312e0-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="312e0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="312e0-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="312e0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="312e0-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="312e0-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="312e0-111">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="312e0-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="312e0-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="312e0-112">See also</span></span>

- [<span data-ttu-id="312e0-113">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="312e0-113">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
