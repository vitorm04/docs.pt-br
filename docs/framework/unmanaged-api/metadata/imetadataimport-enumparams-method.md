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
ms.openlocfilehash: f9a58a70b5264d7f1eb33fb0e09c702c94a13e85
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491744"
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="74c21-102">Método IMetaDataImport::EnumParams</span><span class="sxs-lookup"><span data-stu-id="74c21-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="74c21-103">Enumera os tokens ParamDef que representam os parâmetros do método referenciado pelo token MethodDef especificado.</span><span class="sxs-lookup"><span data-stu-id="74c21-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74c21-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="74c21-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74c21-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="74c21-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="74c21-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="74c21-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="74c21-107">Isso deve ser nulo para a primeira chamada deste método.</span><span class="sxs-lookup"><span data-stu-id="74c21-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="74c21-108">no Um token MethodDef que representa o método com os parâmetros a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="74c21-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="74c21-109">fora A matriz usada para armazenar os tokens ParamDef.</span><span class="sxs-lookup"><span data-stu-id="74c21-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="74c21-110">no O tamanho máximo da `rParams` matriz.</span><span class="sxs-lookup"><span data-stu-id="74c21-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="74c21-111">fora O número de tokens ParamDef retornados em `rParams` .</span><span class="sxs-lookup"><span data-stu-id="74c21-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74c21-112">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="74c21-112">Return Value</span></span>  
  
|<span data-ttu-id="74c21-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="74c21-113">HRESULT</span></span>|<span data-ttu-id="74c21-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="74c21-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="74c21-115">`EnumParams`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="74c21-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="74c21-116">Não há tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="74c21-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="74c21-117">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="74c21-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="74c21-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="74c21-118">Requirements</span></span>  
 <span data-ttu-id="74c21-119">**Plataforma:** Consulte [requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74c21-119">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74c21-120">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="74c21-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="74c21-121">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="74c21-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="74c21-122">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74c21-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74c21-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="74c21-123">See also</span></span>

- [<span data-ttu-id="74c21-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="74c21-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="74c21-125">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="74c21-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
