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
ms.openlocfilehash: 4ed5ddd74e61e63426871f659aa1c962d38fd534
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221395"
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="e84cb-102">Método IMetaDataImport::EnumParams</span><span class="sxs-lookup"><span data-stu-id="e84cb-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="e84cb-103">Enumera os tokens de ParamDef que representam os parâmetros do método referenciada pelo token de MethodDef especificado.</span><span class="sxs-lookup"><span data-stu-id="e84cb-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e84cb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e84cb-104">Syntax</span></span>  
  
```  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e84cb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e84cb-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e84cb-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="e84cb-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e84cb-107">Isso deve ser NULL para a primeira chamada desse método.</span><span class="sxs-lookup"><span data-stu-id="e84cb-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="e84cb-108">[in] Um token MethodDef que representa o método com os parâmetros para enumerar.</span><span class="sxs-lookup"><span data-stu-id="e84cb-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="e84cb-109">[out] A matriz usada para armazenar os tokens de ParamDef.</span><span class="sxs-lookup"><span data-stu-id="e84cb-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e84cb-110">[in] O tamanho máximo da `rParams` matriz.</span><span class="sxs-lookup"><span data-stu-id="e84cb-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e84cb-111">[out] O número de tokens ParamDef retornado no `rParams`.</span><span class="sxs-lookup"><span data-stu-id="e84cb-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e84cb-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e84cb-112">Return Value</span></span>  
  
|<span data-ttu-id="e84cb-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e84cb-113">HRESULT</span></span>|<span data-ttu-id="e84cb-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e84cb-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumParams` <span data-ttu-id="e84cb-115">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="e84cb-115">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e84cb-116">Não há nenhum token para enumerar.</span><span class="sxs-lookup"><span data-stu-id="e84cb-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="e84cb-117">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="e84cb-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e84cb-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e84cb-118">Requirements</span></span>  
 <span data-ttu-id="e84cb-119">**Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e84cb-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e84cb-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e84cb-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e84cb-121">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e84cb-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="e84cb-122">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="e84cb-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e84cb-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e84cb-123">See also</span></span>

- [<span data-ttu-id="e84cb-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="e84cb-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e84cb-125">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="e84cb-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
