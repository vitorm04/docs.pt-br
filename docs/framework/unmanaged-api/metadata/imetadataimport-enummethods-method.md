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
ms.openlocfilehash: 91ae326a89e463d26b39c1659d872130042557bf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492001"
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="5bdab-102">Método IMetaDataImport::EnumMethods</span><span class="sxs-lookup"><span data-stu-id="5bdab-102">IMetaDataImport::EnumMethods Method</span></span>
<span data-ttu-id="5bdab-103">Enumera tokens MethodDef que representam métodos do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="5bdab-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bdab-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5bdab-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,
   [in]  mdTypeDef      cl,
   [out] mdMethodDef    rMethods[],
   [in]  ULONG          cMax,
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bdab-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5bdab-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="5bdab-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="5bdab-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="5bdab-107">Isso deve ser nulo para a primeira chamada deste método.</span><span class="sxs-lookup"><span data-stu-id="5bdab-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="5bdab-108">no Um token de TypeDef que representa o tipo com os métodos a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="5bdab-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="5bdab-109">fora A matriz para armazenar os tokens MethodDef.</span><span class="sxs-lookup"><span data-stu-id="5bdab-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5bdab-110">no O tamanho máximo da matriz MethodDef `rMethods` .</span><span class="sxs-lookup"><span data-stu-id="5bdab-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="5bdab-111">fora O número de tokens MethodDef retornados em `rMethods` .</span><span class="sxs-lookup"><span data-stu-id="5bdab-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5bdab-112">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="5bdab-112">Return Value</span></span>  
  
|<span data-ttu-id="5bdab-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5bdab-113">HRESULT</span></span>|<span data-ttu-id="5bdab-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5bdab-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5bdab-115">`EnumMethods`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="5bdab-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5bdab-116">Não há tokens MethodDef para enumerar.</span><span class="sxs-lookup"><span data-stu-id="5bdab-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="5bdab-117">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="5bdab-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5bdab-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5bdab-118">Requirements</span></span>  
 <span data-ttu-id="5bdab-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bdab-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bdab-120">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5bdab-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5bdab-121">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5bdab-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5bdab-122">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bdab-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bdab-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="5bdab-123">See also</span></span>

- [<span data-ttu-id="5bdab-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="5bdab-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="5bdab-125">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="5bdab-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
