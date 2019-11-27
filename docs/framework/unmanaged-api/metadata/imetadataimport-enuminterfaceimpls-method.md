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
ms.openlocfilehash: 4c819bff50e6644a733374e9863d670d3323ee68
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449530"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="d4525-102">Método IMetaDataImport::EnumInterfaceImpls</span><span class="sxs-lookup"><span data-stu-id="d4525-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="d4525-103">Enumera todas as interfaces implementadas pelo `TypeDef`especificado.</span><span class="sxs-lookup"><span data-stu-id="d4525-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="d4525-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d4525-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4525-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d4525-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d4525-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="d4525-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="d4525-107">no O token do TypeDef cujos tokens MethodDef que representam implementações de interface devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="d4525-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="d4525-108">fora A matriz usada para armazenar os tokens MethodDef.</span><span class="sxs-lookup"><span data-stu-id="d4525-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d4525-109">no O tamanho máximo da matriz de `rImpls`.</span><span class="sxs-lookup"><span data-stu-id="d4525-109">[in] The maximum size of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="d4525-110">fora O número real de tokens retornados em `rImpls`.</span><span class="sxs-lookup"><span data-stu-id="d4525-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4525-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d4525-111">Return Value</span></span>  
  
|<span data-ttu-id="d4525-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d4525-112">HRESULT</span></span>|<span data-ttu-id="d4525-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="d4525-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d4525-114">`EnumInterfaceImpls` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="d4525-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d4525-115">Não há tokens MethodDef para enumerar.</span><span class="sxs-lookup"><span data-stu-id="d4525-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="d4525-116">Nesse caso, `pcImpls` é definido como zero.</span><span class="sxs-lookup"><span data-stu-id="d4525-116">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="d4525-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="d4525-117">Remarks</span></span>

<span data-ttu-id="d4525-118">A enumeração retorna uma coleção de tokens de `mdInterfaceImpl` para cada interface implementada pelo `TypeDef`especificado.</span><span class="sxs-lookup"><span data-stu-id="d4525-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="d4525-119">Os tokens de interface são retornados na ordem em que as interfaces foram especificadas (por meio de `DefineTypeDef` ou `SetTypeDefProps`).</span><span class="sxs-lookup"><span data-stu-id="d4525-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="d4525-120">As propriedades dos tokens de `mdInterfaceImpl` retornados podem ser consultadas usando [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span><span class="sxs-lookup"><span data-stu-id="d4525-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="d4525-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d4525-121">Requirements</span></span>  
 <span data-ttu-id="d4525-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4525-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4525-123">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d4525-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d4525-124">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d4525-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d4525-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4525-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4525-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4525-126">See also</span></span>

- [<span data-ttu-id="d4525-127">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="d4525-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d4525-128">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="d4525-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
