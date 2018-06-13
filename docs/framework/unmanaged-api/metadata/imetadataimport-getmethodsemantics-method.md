---
title: Método IMetaDataImport::GetMethodSemantics
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodSemantics
helpviewer_keywords:
- GetMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::GetMethodSemantics method [.NET Framework metadata]
ms.assetid: 5e018eaa-d60e-4a0b-a2c5-8c36bd09d905
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4f4908f5d03687fb415c91325941aaab148832dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447730"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="cd471-102">Método IMetaDataImport::GetMethodSemantics</span><span class="sxs-lookup"><span data-stu-id="cd471-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="cd471-103">Obtém sinalizadores indicando a relação entre o método referenciado por token MethodDef especificado e a propriedade emparelhada e o evento referenciado pelo EventProp especificado token.</span><span class="sxs-lookup"><span data-stu-id="cd471-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd471-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd471-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd471-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cd471-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="cd471-106">[in] Um token MethodDef que representa o método para obter as informações de função semântica.</span><span class="sxs-lookup"><span data-stu-id="cd471-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="cd471-107">[in] Um token que representa a propriedade emparelhada e eventos para o qual obter a função do método.</span><span class="sxs-lookup"><span data-stu-id="cd471-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="cd471-108">[out] Um ponteiro para os sinalizadores de semântica associada.</span><span class="sxs-lookup"><span data-stu-id="cd471-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="cd471-109">Esse valor é um bitmask do [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="cd471-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd471-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="cd471-110">Remarks</span></span>  
 <span data-ttu-id="cd471-111">O [: Defineproperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) método define sinalizadores de semântica do método.</span><span class="sxs-lookup"><span data-stu-id="cd471-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd471-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cd471-112">Requirements</span></span>  
 <span data-ttu-id="cd471-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd471-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd471-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cd471-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cd471-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="cd471-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cd471-116">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd471-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd471-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd471-117">See Also</span></span>  
 [<span data-ttu-id="cd471-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="cd471-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="cd471-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="cd471-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
