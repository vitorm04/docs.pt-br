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
ms.openlocfilehash: fb96949e22b4edfc0e64780a54bb38da44eb8369
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129546"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="88841-102">Método ICorDebugModule::GetMetaDataInterface</span><span class="sxs-lookup"><span data-stu-id="88841-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="88841-103">Obtém um objeto de interface de metadados que pode ser usado para examinar os metadados do módulo.</span><span class="sxs-lookup"><span data-stu-id="88841-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88841-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88841-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88841-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="88841-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="88841-106">no A ID de referência que especifica a interface de metadados.</span><span class="sxs-lookup"><span data-stu-id="88841-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="88841-107">fora Um ponteiro para o endereço de um objeto de `T:IUnknown` que é uma das [interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="88841-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88841-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="88841-108">Remarks</span></span>  
 <span data-ttu-id="88841-109">O depurador pode usar o método `GetMetaDataInterface` para fazer uma cópia dos metadados originais de um módulo, o que deve ser feito para editar esse módulo.</span><span class="sxs-lookup"><span data-stu-id="88841-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="88841-110">O depurador chama `GetMetaDataInterface` para obter um objeto de interface [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) para o módulo e, em seguida, chama [IMetaDataEmit:: SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) para salvar uma cópia dos metadados do módulo na memória.</span><span class="sxs-lookup"><span data-stu-id="88841-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88841-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="88841-111">Requirements</span></span>  
 <span data-ttu-id="88841-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88841-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88841-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88841-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88841-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88841-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88841-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88841-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88841-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88841-116">See also</span></span>

- [<span data-ttu-id="88841-117">Metadados</span><span class="sxs-lookup"><span data-stu-id="88841-117">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
