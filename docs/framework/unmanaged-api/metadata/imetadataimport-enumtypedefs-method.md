---
title: Método IMetaDataImport::EnumTypeDefs
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
ms.openlocfilehash: 3854cb4aa3d229c87466c0a35a72447ceb235624
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449998"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="2b666-102">Método IMetaDataImport::EnumTypeDefs</span><span class="sxs-lookup"><span data-stu-id="2b666-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="2b666-103">Enumera os tokens de TypeDef que representam todos os tipos no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="2b666-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b666-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b666-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b666-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2b666-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="2b666-106">fora Um ponteiro para o novo enumerador.</span><span class="sxs-lookup"><span data-stu-id="2b666-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="2b666-107">Isso deve ser nulo para a primeira chamada deste método.</span><span class="sxs-lookup"><span data-stu-id="2b666-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="2b666-108">no A matriz usada para armazenar os tokens de TypeDef.</span><span class="sxs-lookup"><span data-stu-id="2b666-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2b666-109">no O tamanho máximo da matriz de `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="2b666-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="2b666-110">fora O número de tokens de TypeDef retornados em `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="2b666-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b666-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2b666-111">Return Value</span></span>  
  
|<span data-ttu-id="2b666-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2b666-112">HRESULT</span></span>|<span data-ttu-id="2b666-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b666-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2b666-114">`EnumTypeDefs` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="2b666-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2b666-115">Não há tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="2b666-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="2b666-116">Nesse caso, `pcTypeDefs` é zero.</span><span class="sxs-lookup"><span data-stu-id="2b666-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b666-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="2b666-117">Remarks</span></span>  
 <span data-ttu-id="2b666-118">O token TypeDef representa um tipo como uma classe ou uma interface, bem como qualquer tipo adicionado por meio de um mecanismo de extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="2b666-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b666-119">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="2b666-119">Requirements</span></span>  
 <span data-ttu-id="2b666-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b666-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b666-121">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2b666-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2b666-122">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2b666-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2b666-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b666-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b666-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b666-124">See also</span></span>

- [<span data-ttu-id="2b666-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="2b666-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="2b666-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="2b666-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
