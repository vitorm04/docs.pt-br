---
title: Método ICorDebugModule::GetBaseAddress
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ad6c8bd59f62bc7b0a96e1ef5e545fe15610c91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516974"
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="9217d-102">Método ICorDebugModule::GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="9217d-102">ICorDebugModule::GetBaseAddress Method</span></span>
<span data-ttu-id="9217d-103">Obtém o endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="9217d-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9217d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9217d-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9217d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9217d-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="9217d-106">[out] Um `CORDB_ADDRESS` que especifica o endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="9217d-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9217d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="9217d-107">Remarks</span></span>  
 <span data-ttu-id="9217d-108">Se o módulo for uma nativa da imagem (ou seja, se o módulo foi produzido pelo gerador de imagem nativa, NGen.exe), seu endereço base será zero.</span><span class="sxs-lookup"><span data-stu-id="9217d-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9217d-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9217d-109">Requirements</span></span>  
 <span data-ttu-id="9217d-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9217d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9217d-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9217d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9217d-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9217d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9217d-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9217d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9217d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9217d-114">See also</span></span>


