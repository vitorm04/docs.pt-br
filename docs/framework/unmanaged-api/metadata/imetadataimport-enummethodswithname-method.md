---
title: "Método IMetaDataImport::EnumMethodsWithName"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMethodsWithName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: dadff8be283160ddc6049d0d2f8b78052e5c8ec5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="c610b-102">Método IMetaDataImport::EnumMethodsWithName</span><span class="sxs-lookup"><span data-stu-id="c610b-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="c610b-103">Enumera os métodos que têm o nome especificado e que são definidos pelo tipo referenciado pelo token de TypeDef especificado.</span><span class="sxs-lookup"><span data-stu-id="c610b-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c610b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c610b-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c610b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c610b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c610b-106">[out no] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="c610b-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c610b-107">Isso deve ser NULL para a primeira chamada do método.</span><span class="sxs-lookup"><span data-stu-id="c610b-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="c610b-108">[in] Um token de TypeDef que representa o tipo cujos métodos para enumerar.</span><span class="sxs-lookup"><span data-stu-id="c610b-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="c610b-109">[in] O nome que limita o escopo da enumeração.</span><span class="sxs-lookup"><span data-stu-id="c610b-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="c610b-110">[out] A matriz usada para armazenar os tokens de MethodDef.</span><span class="sxs-lookup"><span data-stu-id="c610b-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c610b-111">[in] O tamanho máximo da `rMethods` matriz.</span><span class="sxs-lookup"><span data-stu-id="c610b-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="c610b-112">[out] O número de tokens de MethodDef retornados em `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="c610b-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c610b-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="c610b-113">Remarks</span></span>  
 <span data-ttu-id="c610b-114">Esse método enumera campos e métodos, mas não propriedades ou eventos.</span><span class="sxs-lookup"><span data-stu-id="c610b-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="c610b-115">Ao contrário de [: Enummethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` descarta todos os tokens de método que não têm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="c610b-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c610b-116">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c610b-116">Return Value</span></span>  
  
|<span data-ttu-id="c610b-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c610b-117">HRESULT</span></span>|<span data-ttu-id="c610b-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="c610b-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c610b-119">`EnumMethodsWithName`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="c610b-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c610b-120">Não há nenhum tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="c610b-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="c610b-121">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="c610b-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c610b-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c610b-122">Requirements</span></span>  
 <span data-ttu-id="c610b-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c610b-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c610b-124">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c610b-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c610b-125">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="c610b-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c610b-126">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c610b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c610b-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c610b-127">See Also</span></span>  
 [<span data-ttu-id="c610b-128">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="c610b-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="c610b-129">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="c610b-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
