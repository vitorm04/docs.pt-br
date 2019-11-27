---
title: Método IMetaDataImport::EnumMethodsWithName
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
ms.openlocfilehash: b0817288040550b5f4c3c4ec063f6a7fdb004137
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450065"
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="dd0bc-102">Método IMetaDataImport::EnumMethodsWithName</span><span class="sxs-lookup"><span data-stu-id="dd0bc-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="dd0bc-103">Enumera os métodos que têm o nome especificado e que são definidos pelo tipo referenciado pelo token de TypeDef especificado.</span><span class="sxs-lookup"><span data-stu-id="dd0bc-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd0bc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd0bc-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd0bc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dd0bc-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="dd0bc-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="dd0bc-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="dd0bc-107">Isso deve ser nulo para a primeira chamada deste método.</span><span class="sxs-lookup"><span data-stu-id="dd0bc-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="dd0bc-108">no Um token de TypeDef que representa o tipo cujos métodos são enumerados.</span><span class="sxs-lookup"><span data-stu-id="dd0bc-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="dd0bc-109">no O nome que limita o escopo da enumeração.</span><span class="sxs-lookup"><span data-stu-id="dd0bc-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="dd0bc-110">fora A matriz usada para armazenar os tokens MethodDef.</span><span class="sxs-lookup"><span data-stu-id="dd0bc-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="dd0bc-111">no O tamanho máximo da matriz de `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="dd0bc-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="dd0bc-112">fora O número de tokens MethodDef retornados em `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="dd0bc-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd0bc-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="dd0bc-113">Remarks</span></span>  
 <span data-ttu-id="dd0bc-114">Esse método enumera campos e métodos, mas não propriedades ou eventos.</span><span class="sxs-lookup"><span data-stu-id="dd0bc-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="dd0bc-115">Ao contrário de [IMetaDataImport:: EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` descarta todos os tokens de método que não têm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="dd0bc-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd0bc-116">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="dd0bc-116">Return Value</span></span>  
  
|<span data-ttu-id="dd0bc-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dd0bc-117">HRESULT</span></span>|<span data-ttu-id="dd0bc-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd0bc-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="dd0bc-119">`EnumMethodsWithName` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="dd0bc-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="dd0bc-120">Não há tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="dd0bc-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="dd0bc-121">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="dd0bc-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dd0bc-122">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="dd0bc-122">Requirements</span></span>  
 <span data-ttu-id="dd0bc-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd0bc-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd0bc-124">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="dd0bc-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd0bc-125">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dd0bc-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dd0bc-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd0bc-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd0bc-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd0bc-127">See also</span></span>

- [<span data-ttu-id="dd0bc-128">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="dd0bc-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="dd0bc-129">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="dd0bc-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
