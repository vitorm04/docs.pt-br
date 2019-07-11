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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d0f94949cdc82cdecd52f003f3400c43014fabf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780455"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="4ab5b-102">Método IMetaDataImport::EnumInterfaceImpls</span><span class="sxs-lookup"><span data-stu-id="4ab5b-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="4ab5b-103">Enumera todas as interfaces implementadas por especificado `TypeDef`.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="4ab5b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4ab5b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ab5b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4ab5b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="4ab5b-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="4ab5b-107">[in] O token do TypeDef cujos tokens MethodDef representando as implementações de interface são a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="4ab5b-108">[out] A matriz usada para armazenar os tokens MethodDef.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4ab5b-109">[in] O tamanho máximo da `rImpls` matriz.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-109">[in] The maximum size of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="4ab5b-110">[out] O número real de tokens retornado no `rImpls`.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ab5b-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4ab5b-111">Return Value</span></span>  
  
|<span data-ttu-id="4ab5b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4ab5b-112">HRESULT</span></span>|<span data-ttu-id="4ab5b-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="4ab5b-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4ab5b-114">`EnumInterfaceImpls` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4ab5b-115">Não há nenhum token MethodDef para enumerar.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="4ab5b-116">Nesse caso, `pcImpls` é definido como zero.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-116">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="4ab5b-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="4ab5b-117">Remarks</span></span>

<span data-ttu-id="4ab5b-118">A enumeração retorna uma coleção de `mdInterfaceImpl` tokens para cada interface implementada por especificado `TypeDef`.</span><span class="sxs-lookup"><span data-stu-id="4ab5b-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="4ab5b-119">Interface tokens são retornados na ordem em que as interfaces foram especificadas (por meio `DefineTypeDef` ou `SetTypeDefProps`).</span><span class="sxs-lookup"><span data-stu-id="4ab5b-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="4ab5b-120">Propriedades de retornado `mdInterfaceImpl` tokens podem ser consultados usando [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span><span class="sxs-lookup"><span data-stu-id="4ab5b-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="4ab5b-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4ab5b-121">Requirements</span></span>  
 <span data-ttu-id="4ab5b-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ab5b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ab5b-123">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4ab5b-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4ab5b-124">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="4ab5b-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4ab5b-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ab5b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ab5b-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ab5b-126">See also</span></span>

- [<span data-ttu-id="4ab5b-127">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="4ab5b-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4ab5b-128">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="4ab5b-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
