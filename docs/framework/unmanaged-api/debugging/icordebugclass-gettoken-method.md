---
title: "Método ICorDebugClass::GetToken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass.GetToken
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass::GetToken
helpviewer_keywords:
- GetToken method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetToken method [.NET Framework debugging]
ms.assetid: ee5c848a-eac4-4462-b07a-07ccd76a75df
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 805ecd7111fd06dfe0d13f60e6dd1e64ec3c37b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="b996b-102">Método ICorDebugClass::GetToken</span><span class="sxs-lookup"><span data-stu-id="b996b-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="b996b-103">Obtém o `TypeDef` token de metadados que faz referência a definição dessa classe.</span><span class="sxs-lookup"><span data-stu-id="b996b-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b996b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b996b-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b996b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b996b-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="b996b-106">[out] Um ponteiro para um `mdTypeDef` token que faz referência a definição dessa classe.</span><span class="sxs-lookup"><span data-stu-id="b996b-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b996b-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b996b-107">Requirements</span></span>  
 <span data-ttu-id="b996b-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b996b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b996b-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b996b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b996b-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b996b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b996b-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b996b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b996b-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b996b-112">See Also</span></span>  
 [<span data-ttu-id="b996b-113">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="b996b-113">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
