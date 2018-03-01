---
title: "Método ICorDebugModule::GetMetaDataInterface"
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
- ICorDebugModule.GetMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d374b83155ccc8511c6e3217a8a49819d81a7d48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="60553-102">Método ICorDebugModule::GetMetaDataInterface</span><span class="sxs-lookup"><span data-stu-id="60553-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="60553-103">Obtém um objeto de interface de metadados que pode ser usado para examinar os metadados para o módulo.</span><span class="sxs-lookup"><span data-stu-id="60553-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60553-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60553-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60553-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="60553-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="60553-106">[in] A ID de referência que especifica a interface de metadados.</span><span class="sxs-lookup"><span data-stu-id="60553-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="60553-107">[out] Um ponteiro para o endereço de um `T:IUnknown` objeto que é uma da [interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="60553-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60553-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="60553-108">Remarks</span></span>  
 <span data-ttu-id="60553-109">O depurador pode usar o `GetMetaDataInterface` método para fazer uma cópia dos metadados de um módulo, que deve ser feito para editar esse módulo original.</span><span class="sxs-lookup"><span data-stu-id="60553-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="60553-110">As chamadas do depurador `GetMetaDataInterface` para obter um [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) objeto de interface do módulo, em seguida, chama [: Savetomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) para salvar uma cópia dos metadados do módulo de memória.</span><span class="sxs-lookup"><span data-stu-id="60553-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60553-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="60553-111">Requirements</span></span>  
 <span data-ttu-id="60553-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60553-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60553-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60553-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60553-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60553-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60553-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60553-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60553-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60553-116">See Also</span></span>  
 [<span data-ttu-id="60553-117">Metadados</span><span class="sxs-lookup"><span data-stu-id="60553-117">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
