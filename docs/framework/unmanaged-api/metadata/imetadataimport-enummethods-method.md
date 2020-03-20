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
ms.openlocfilehash: 218b65b5899692774c434ae136a3976ecb97ea2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177307"
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="df47d-102">Método IMetaDataImport::EnumMethods</span><span class="sxs-lookup"><span data-stu-id="df47d-102">IMetaDataImport::EnumMethods Method</span></span>
<span data-ttu-id="df47d-103">Enumera os tokens MethodDef representando métodos do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="df47d-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df47d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df47d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,
   [in]  mdTypeDef      cl,
   [out] mdMethodDef    rMethods[],
   [in]  ULONG          cMax,
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df47d-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="df47d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="df47d-106">[dentro, fora] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="df47d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="df47d-107">Isto deve ser NULO para a primeira chamada deste método.</span><span class="sxs-lookup"><span data-stu-id="df47d-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="df47d-108">[em] Um token TypeDef representando o tipo com os métodos a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="df47d-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="df47d-109">[fora] A matriz para armazenar os tokens MethodDef.</span><span class="sxs-lookup"><span data-stu-id="df47d-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="df47d-110">[em] O tamanho máximo da `rMethods` matriz MethodDef.</span><span class="sxs-lookup"><span data-stu-id="df47d-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="df47d-111">[fora] O número de tokens MethodDef retornado em `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="df47d-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df47d-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="df47d-112">Return Value</span></span>  
  
|<span data-ttu-id="df47d-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="df47d-113">HRESULT</span></span>|<span data-ttu-id="df47d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="df47d-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="df47d-115">`EnumMethods`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="df47d-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="df47d-116">Não há tokens MethodDef para enumerar.</span><span class="sxs-lookup"><span data-stu-id="df47d-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="df47d-117">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="df47d-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="df47d-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="df47d-118">Requirements</span></span>  
 <span data-ttu-id="df47d-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df47d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df47d-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="df47d-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="df47d-121">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="df47d-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="df47d-122">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df47d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df47d-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="df47d-123">See also</span></span>

- [<span data-ttu-id="df47d-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="df47d-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="df47d-125">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="df47d-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
