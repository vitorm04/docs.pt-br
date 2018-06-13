---
title: Método IMetaDataImport::EnumParams
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumParams
helpviewer_keywords:
- IMetaDataImport::EnumParams method [.NET Framework metadata]
- EnumParams method [.NET Framework metadata]
ms.assetid: 52118dc9-fe6e-4b39-aa48-c3cc3ea4214d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b848c30e824d45f6f619cfdb3d00a2d3cdc4573e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448707"
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="f9370-102">Método IMetaDataImport::EnumParams</span><span class="sxs-lookup"><span data-stu-id="f9370-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="f9370-103">Enumera ParamDef tokens que representam os parâmetros do método referenciada pelo token MethodDef especificado.</span><span class="sxs-lookup"><span data-stu-id="f9370-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9370-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9370-104">Syntax</span></span>  
  
```  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9370-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f9370-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f9370-106">[out no] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="f9370-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="f9370-107">Isso deve ser NULL para a primeira chamada do método.</span><span class="sxs-lookup"><span data-stu-id="f9370-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="f9370-108">[in] Um token MethodDef que representa o método com parâmetros para enumerar.</span><span class="sxs-lookup"><span data-stu-id="f9370-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="f9370-109">[out] A matriz usada para armazenar os tokens de ParamDef.</span><span class="sxs-lookup"><span data-stu-id="f9370-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f9370-110">[in] O tamanho máximo da `rParams` matriz.</span><span class="sxs-lookup"><span data-stu-id="f9370-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="f9370-111">[out] O número de tokens ParamDef retornado em `rParams`.</span><span class="sxs-lookup"><span data-stu-id="f9370-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9370-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f9370-112">Return Value</span></span>  
  
|<span data-ttu-id="f9370-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f9370-113">HRESULT</span></span>|<span data-ttu-id="f9370-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9370-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f9370-115">`EnumParams` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="f9370-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f9370-116">Não há nenhum tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="f9370-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="f9370-117">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="f9370-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f9370-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f9370-118">Requirements</span></span>  
 <span data-ttu-id="f9370-119">**Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9370-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9370-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f9370-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f9370-121">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="f9370-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f9370-122">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9370-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9370-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9370-123">See Also</span></span>  
 [<span data-ttu-id="f9370-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="f9370-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="f9370-125">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="f9370-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
