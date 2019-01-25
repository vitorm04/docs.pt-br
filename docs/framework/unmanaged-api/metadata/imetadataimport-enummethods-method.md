---
title: Método IMetaDataImport::EnumMethods
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethods
helpviewer_keywords:
- IMetaDataImport::EnumMethods method [.NET Framework metadata]
- EnumMethods method [.NET Framework metadata]
ms.assetid: 8cc3b0c3-d97d-4f71-9e7d-ef2a92b4959a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 668c7298a9543cce93cce324672334c9ec1e8cd2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732811"
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="b27ae-102">Método IMetaDataImport::EnumMethods</span><span class="sxs-lookup"><span data-stu-id="b27ae-102">IMetaDataImport::EnumMethods Method</span></span>
<span data-ttu-id="b27ae-103">Enumera os tokens MethodDef que representam os métodos do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="b27ae-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b27ae-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b27ae-104">Syntax</span></span>  
  
```  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,   
   [in]  mdTypeDef      cl,   
   [out] mdMethodDef    rMethods[],   
   [in]  ULONG          cMax,   
   [out] ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b27ae-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b27ae-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b27ae-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="b27ae-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b27ae-107">Isso deve ser NULL para a primeira chamada desse método.</span><span class="sxs-lookup"><span data-stu-id="b27ae-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="b27ae-108">[in] Um token de TypeDef que representa o tipo com os métodos para enumerar.</span><span class="sxs-lookup"><span data-stu-id="b27ae-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="b27ae-109">[out] A matriz para armazenar os tokens MethodDef.</span><span class="sxs-lookup"><span data-stu-id="b27ae-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b27ae-110">[in] O tamanho máximo do MethodDef `rMethods` matriz.</span><span class="sxs-lookup"><span data-stu-id="b27ae-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="b27ae-111">[out] O número de tokens MethodDef retornado no `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="b27ae-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b27ae-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b27ae-112">Return Value</span></span>  
  
|<span data-ttu-id="b27ae-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b27ae-113">HRESULT</span></span>|<span data-ttu-id="b27ae-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b27ae-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b27ae-115">`EnumMethods` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b27ae-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b27ae-116">Não há nenhum token MethodDef para enumerar.</span><span class="sxs-lookup"><span data-stu-id="b27ae-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="b27ae-117">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="b27ae-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b27ae-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b27ae-118">Requirements</span></span>  
 <span data-ttu-id="b27ae-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b27ae-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b27ae-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b27ae-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b27ae-121">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b27ae-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b27ae-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b27ae-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b27ae-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b27ae-123">See also</span></span>
- [<span data-ttu-id="b27ae-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="b27ae-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b27ae-125">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="b27ae-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
