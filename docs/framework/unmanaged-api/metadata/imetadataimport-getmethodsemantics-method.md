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
ms.openlocfilehash: 57ddbd8c6935f2c0275c132e30ea175c6f198fac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200084"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="22907-102">Método IMetaDataImport::GetMethodSemantics</span><span class="sxs-lookup"><span data-stu-id="22907-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="22907-103">Obtém o token de sinalizadores que indica a relação entre o método referenciado pelo token MethodDef especificado e a propriedade emparelhada e o evento referenciado pelo EventProp especificado.</span><span class="sxs-lookup"><span data-stu-id="22907-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22907-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22907-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22907-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="22907-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="22907-106">[in] Um token MethodDef que representa o método para obter as informações de função semântica para.</span><span class="sxs-lookup"><span data-stu-id="22907-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="22907-107">[in] Um token que representa a propriedade emparelhada e o evento para o qual obter a função do método.</span><span class="sxs-lookup"><span data-stu-id="22907-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="22907-108">[out] Um ponteiro para os sinalizadores de semântica associada.</span><span class="sxs-lookup"><span data-stu-id="22907-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="22907-109">Esse valor é um bitmask do [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="22907-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22907-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="22907-110">Remarks</span></span>  
 <span data-ttu-id="22907-111">O [imetadataemit:: Defineproperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) método define sinalizadores de semântica do método.</span><span class="sxs-lookup"><span data-stu-id="22907-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22907-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="22907-112">Requirements</span></span>  
 <span data-ttu-id="22907-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22907-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22907-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="22907-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="22907-115">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="22907-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="22907-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="22907-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="22907-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22907-117">See also</span></span>

- [<span data-ttu-id="22907-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="22907-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="22907-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="22907-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
