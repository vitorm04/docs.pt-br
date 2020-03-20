---
title: Método IMetaDataImport::EnumInterfaceImpls
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
ms.openlocfilehash: b535fdd5027a26cc4dd0eafec9883f0186773dd1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175493"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="f8698-102">Método IMetaDataImport::EnumInterfaceImpls</span><span class="sxs-lookup"><span data-stu-id="f8698-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="f8698-103">Enumera todas as interfaces implementadas `TypeDef`pelo especificado .</span><span class="sxs-lookup"><span data-stu-id="f8698-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="f8698-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f8698-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8698-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8698-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f8698-106">[dentro, fora] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="f8698-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="f8698-107">[em] O token do TypeDef cujos tokens MethodDef representando implementações de interface devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="f8698-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="f8698-108">[fora] A matriz usada para armazenar os tokens MethodDef.</span><span class="sxs-lookup"><span data-stu-id="f8698-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f8698-109">[em] O comprimento máximo `rImpls` da matriz.</span><span class="sxs-lookup"><span data-stu-id="f8698-109">[in] The maximum length of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="f8698-110">[fora] O número real de tokens retornou em `rImpls`.</span><span class="sxs-lookup"><span data-stu-id="f8698-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8698-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f8698-111">Return Value</span></span>  
  
|<span data-ttu-id="f8698-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f8698-112">HRESULT</span></span>|<span data-ttu-id="f8698-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8698-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f8698-114">`EnumInterfaceImpls`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="f8698-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f8698-115">Não há tokens MethodDef para enumerar.</span><span class="sxs-lookup"><span data-stu-id="f8698-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="f8698-116">Nesse caso, `pcImpls` está definido como zero.</span><span class="sxs-lookup"><span data-stu-id="f8698-116">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="f8698-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="f8698-117">Remarks</span></span>

<span data-ttu-id="f8698-118">A enumeração retorna `mdInterfaceImpl` uma coleção de tokens para `TypeDef`cada interface implementada pelo especificado .</span><span class="sxs-lookup"><span data-stu-id="f8698-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="f8698-119">Os tokens de interface são devolvidos na ordem `DefineTypeDef` `SetTypeDefProps`em que as interfaces foram especificadas (através ou ).</span><span class="sxs-lookup"><span data-stu-id="f8698-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="f8698-120">As propriedades dos `mdInterfaceImpl` tokens retornados podem ser consultadas usando [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span><span class="sxs-lookup"><span data-stu-id="f8698-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="f8698-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f8698-121">Requirements</span></span>  
 <span data-ttu-id="f8698-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8698-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8698-123">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f8698-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f8698-124">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f8698-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f8698-125">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8698-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8698-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="f8698-126">See also</span></span>

- [<span data-ttu-id="f8698-127">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="f8698-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f8698-128">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="f8698-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
