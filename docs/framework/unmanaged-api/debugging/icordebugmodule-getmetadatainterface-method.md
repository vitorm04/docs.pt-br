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
ms.openlocfilehash: f5d0dd7a99087b21a5f827e4dce0f6342ae7b25a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501762"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="1354a-102">Método ICorDebugModule::GetMetaDataInterface</span><span class="sxs-lookup"><span data-stu-id="1354a-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="1354a-103">Obtém um objeto de interface de metadados que pode ser usado para examinar os metadados do módulo.</span><span class="sxs-lookup"><span data-stu-id="1354a-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1354a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1354a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1354a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1354a-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="1354a-106">no A ID de referência que especifica a interface de metadados.</span><span class="sxs-lookup"><span data-stu-id="1354a-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="1354a-107">fora Um ponteiro para o endereço de um `T:IUnknown` objeto que é uma das [interfaces de metadados](../metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="1354a-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1354a-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="1354a-108">Remarks</span></span>  
 <span data-ttu-id="1354a-109">O depurador pode usar o `GetMetaDataInterface` método para fazer uma cópia dos metadados originais de um módulo, o que deve ser feito para editar esse módulo.</span><span class="sxs-lookup"><span data-stu-id="1354a-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="1354a-110">O depurador chama `GetMetaDataInterface` para obter um objeto de interface [IMetaDataEmit](../metadata/imetadataemit-interface.md) para o módulo e, em seguida, chama [IMetaDataEmit:: SaveToMemory](../metadata/imetadataemit-savetomemory-method.md) para salvar uma cópia dos metadados do módulo na memória.</span><span class="sxs-lookup"><span data-stu-id="1354a-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1354a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1354a-111">Requirements</span></span>  
 <span data-ttu-id="1354a-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1354a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1354a-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1354a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1354a-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1354a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1354a-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1354a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1354a-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="1354a-116">See also</span></span>

- [<span data-ttu-id="1354a-117">Metadados</span><span class="sxs-lookup"><span data-stu-id="1354a-117">Metadata</span></span>](../metadata/index.md)
