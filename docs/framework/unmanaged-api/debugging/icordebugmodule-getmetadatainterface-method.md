---
title: "Método ICorDebugModule::GetMetaDataInterface"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetMetaDataInterface
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f4b1944c68db0cbdd8eb49e10433defc953e4494
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="d8abc-102">Método ICorDebugModule::GetMetaDataInterface</span><span class="sxs-lookup"><span data-stu-id="d8abc-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="d8abc-103">Obtém um objeto de interface de metadados que pode ser usado para examinar os metadados para o módulo.</span><span class="sxs-lookup"><span data-stu-id="d8abc-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8abc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8abc-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8abc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d8abc-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="d8abc-106">[in] A ID de referência que especifica a interface de metadados.</span><span class="sxs-lookup"><span data-stu-id="d8abc-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="d8abc-107">[out] Um ponteiro para o endereço de um `T:IUnknown` objeto que é uma da [interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="d8abc-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8abc-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="d8abc-108">Remarks</span></span>  
 <span data-ttu-id="d8abc-109">O depurador pode usar o `GetMetaDataInterface` método para fazer uma cópia dos metadados de um módulo, que deve ser feito para editar esse módulo original.</span><span class="sxs-lookup"><span data-stu-id="d8abc-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="d8abc-110">As chamadas do depurador `GetMetaDataInterface` para obter um [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) objeto de interface do módulo, em seguida, chama [: Savetomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) para salvar uma cópia dos metadados do módulo de memória.</span><span class="sxs-lookup"><span data-stu-id="d8abc-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8abc-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d8abc-111">Requirements</span></span>  
 <span data-ttu-id="d8abc-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8abc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8abc-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8abc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8abc-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8abc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8abc-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8abc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8abc-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8abc-116">See Also</span></span>  
 [<span data-ttu-id="d8abc-117">Metadados</span><span class="sxs-lookup"><span data-stu-id="d8abc-117">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
