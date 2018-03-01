---
title: "Método ICorDebugModule::GetBaseAddress"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugModule.GetBaseAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetBaseAddress
helpviewer_keywords:
- GetBaseAddress method [.NET Framework debugging]
- ICorDebugModule::GetBaseAddress method [.NET Framework debugging]
ms.assetid: 26a82815-1982-4eb7-92d1-5c3d318d5be4
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aca93086e5425d7579b1394f72b039938f519ca9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="f47a1-102">Método ICorDebugModule::GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="f47a1-102">ICorDebugModule::GetBaseAddress Method</span></span>
<span data-ttu-id="f47a1-103">Obtém o endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="f47a1-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f47a1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f47a1-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f47a1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f47a1-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="f47a1-106">[out] Um `CORDB_ADDRESS` que especifica o endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="f47a1-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f47a1-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f47a1-107">Remarks</span></span>  
 <span data-ttu-id="f47a1-108">Se o módulo for uma nativa da imagem (ou seja, se o módulo foi produzido pelo gerador de imagem nativa, NGen.exe), seu endereço base será zero.</span><span class="sxs-lookup"><span data-stu-id="f47a1-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f47a1-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f47a1-109">Requirements</span></span>  
 <span data-ttu-id="f47a1-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f47a1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f47a1-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f47a1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f47a1-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f47a1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f47a1-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f47a1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f47a1-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f47a1-114">See Also</span></span>  
    
 
