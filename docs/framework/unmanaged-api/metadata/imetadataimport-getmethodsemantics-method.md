---
title: "Método IMetaDataImport::GetMethodSemantics"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetMethodSemantics
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetMethodSemantics
helpviewer_keywords:
- GetMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::GetMethodSemantics method [.NET Framework metadata]
ms.assetid: 5e018eaa-d60e-4a0b-a2c5-8c36bd09d905
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f15aedb74fd7322031d213c5229f65d70f7cb771
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="d511a-102">Método IMetaDataImport::GetMethodSemantics</span><span class="sxs-lookup"><span data-stu-id="d511a-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="d511a-103">Obtém sinalizadores indicando a relação entre o método referenciado por token MethodDef especificado e a propriedade emparelhada e o evento referenciado pelo EventProp especificado token.</span><span class="sxs-lookup"><span data-stu-id="d511a-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d511a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d511a-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d511a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d511a-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="d511a-106">[in] Um token MethodDef que representa o método para obter as informações de função semântica.</span><span class="sxs-lookup"><span data-stu-id="d511a-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="d511a-107">[in] Um token que representa a propriedade emparelhada e eventos para o qual obter a função do método.</span><span class="sxs-lookup"><span data-stu-id="d511a-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="d511a-108">[out] Um ponteiro para os sinalizadores de semântica associada.</span><span class="sxs-lookup"><span data-stu-id="d511a-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="d511a-109">Esse valor é um bitmask do [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="d511a-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d511a-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="d511a-110">Remarks</span></span>  
 <span data-ttu-id="d511a-111">O [: Defineproperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) método define sinalizadores de semântica do método.</span><span class="sxs-lookup"><span data-stu-id="d511a-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d511a-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d511a-112">Requirements</span></span>  
 <span data-ttu-id="d511a-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d511a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d511a-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d511a-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d511a-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d511a-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d511a-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d511a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d511a-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d511a-117">See Also</span></span>  
 [<span data-ttu-id="d511a-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="d511a-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="d511a-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="d511a-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
