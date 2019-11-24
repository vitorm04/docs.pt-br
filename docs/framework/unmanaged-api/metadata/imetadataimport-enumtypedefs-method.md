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
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="37e8a-102">Método IMetaDataImport::EnumTypeDefs</span><span class="sxs-lookup"><span data-stu-id="37e8a-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="37e8a-103">Enumerates TypeDef tokens representing all types within the current scope.</span><span class="sxs-lookup"><span data-stu-id="37e8a-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37e8a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37e8a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37e8a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="37e8a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="37e8a-106">[out] A pointer to the new enumerator.</span><span class="sxs-lookup"><span data-stu-id="37e8a-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="37e8a-107">This must be NULL for the first call of this method.</span><span class="sxs-lookup"><span data-stu-id="37e8a-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="37e8a-108">[in] The array used to store the TypeDef tokens.</span><span class="sxs-lookup"><span data-stu-id="37e8a-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="37e8a-109">[in] The maximum size of the `rTypeDefs` array.</span><span class="sxs-lookup"><span data-stu-id="37e8a-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="37e8a-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="37e8a-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37e8a-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="37e8a-111">Return Value</span></span>  
  
|<span data-ttu-id="37e8a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="37e8a-112">HRESULT</span></span>|<span data-ttu-id="37e8a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="37e8a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="37e8a-114">`EnumTypeDefs` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="37e8a-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="37e8a-115">There are no tokens to enumerate.</span><span class="sxs-lookup"><span data-stu-id="37e8a-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="37e8a-116">In that case, `pcTypeDefs` is zero.</span><span class="sxs-lookup"><span data-stu-id="37e8a-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37e8a-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="37e8a-117">Remarks</span></span>  
 <span data-ttu-id="37e8a-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span><span class="sxs-lookup"><span data-stu-id="37e8a-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37e8a-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="37e8a-119">Requirements</span></span>  
 <span data-ttu-id="37e8a-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37e8a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37e8a-121">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="37e8a-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="37e8a-122">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="37e8a-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="37e8a-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37e8a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37e8a-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37e8a-124">See also</span></span>

- [<span data-ttu-id="37e8a-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="37e8a-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="37e8a-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="37e8a-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
