---
title: Método ICorDebugModule::GetMetaDataInterface
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37710fbb7acc50b80d7acebe4194b019c0b64660
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102590"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="6258f-102">Método ICorDebugModule::GetMetaDataInterface</span><span class="sxs-lookup"><span data-stu-id="6258f-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="6258f-103">Obtém um objeto de interface de metadados que pode ser usado para examinar os metadados para o módulo.</span><span class="sxs-lookup"><span data-stu-id="6258f-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6258f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6258f-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6258f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6258f-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="6258f-106">[in] A ID de referência que especifica a interface de metadados.</span><span class="sxs-lookup"><span data-stu-id="6258f-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="6258f-107">[out] Um ponteiro para o endereço de um `T:IUnknown` objeto que é um dos [interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="6258f-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6258f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="6258f-108">Remarks</span></span>  
 <span data-ttu-id="6258f-109">O depurador pode usar o `GetMetaDataInterface` método para fazer uma cópia dos metadados para um módulo, que deve ser feito para editar esse módulo original.</span><span class="sxs-lookup"><span data-stu-id="6258f-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="6258f-110">As chamadas do depurador `GetMetaDataInterface` para obter uma [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) objeto de interface do módulo, em seguida, chama [imetadataemit:: Savetomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) para salvar uma cópia dos metadados do módulo para a memória.</span><span class="sxs-lookup"><span data-stu-id="6258f-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6258f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6258f-111">Requirements</span></span>  
 <span data-ttu-id="6258f-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6258f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6258f-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6258f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6258f-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6258f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6258f-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6258f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6258f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6258f-116">See also</span></span>

- [<span data-ttu-id="6258f-117">Metadados</span><span class="sxs-lookup"><span data-stu-id="6258f-117">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
