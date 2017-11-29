---
title: "Método IMetaDataImport::EnumModuleRefs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumModuleRefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumModuleRefs
helpviewer_keywords:
- EnumModuleRefs method [.NET Framework metadata]
- IMetaDataImport::EnumModuleRefs method [.NET Framework metadata]
ms.assetid: 53441f3a-68d2-477c-906e-37c55dfcfb4d
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ebba448881b934220f0eb46c392ab0909ae37f68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="009ca-102">Método IMetaDataImport::EnumModuleRefs</span><span class="sxs-lookup"><span data-stu-id="009ca-102">IMetaDataImport::EnumModuleRefs Method</span></span>
<span data-ttu-id="009ca-103">Enumera ModuleRef tokens que representam os módulos importados.</span><span class="sxs-lookup"><span data-stu-id="009ca-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="009ca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="009ca-104">Syntax</span></span>  
  
```  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="009ca-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="009ca-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="009ca-106">[out no] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="009ca-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="009ca-107">Isso deve ser NULL para a primeira chamada do método.</span><span class="sxs-lookup"><span data-stu-id="009ca-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="009ca-108">[out] A matriz usada para armazenar os tokens de ModuleRef.</span><span class="sxs-lookup"><span data-stu-id="009ca-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="009ca-109">[in] O tamanho máximo da `rModuleRefs` matriz.</span><span class="sxs-lookup"><span data-stu-id="009ca-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="009ca-110">[out] O número de tokens de ModuleRef retornados em `rModuleRefs`.</span><span class="sxs-lookup"><span data-stu-id="009ca-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="009ca-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="009ca-111">Return Value</span></span>  
  
|<span data-ttu-id="009ca-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="009ca-112">HRESULT</span></span>|<span data-ttu-id="009ca-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="009ca-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="009ca-114">`EnumModuleRefs`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="009ca-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="009ca-115">Não há nenhum tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="009ca-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="009ca-116">Nesse caso, `pcModuleRefs` é zero.</span><span class="sxs-lookup"><span data-stu-id="009ca-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="009ca-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="009ca-117">Requirements</span></span>  
 <span data-ttu-id="009ca-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="009ca-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="009ca-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="009ca-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="009ca-120">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="009ca-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="009ca-121">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="009ca-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="009ca-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="009ca-122">See Also</span></span>  
 [<span data-ttu-id="009ca-123">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="009ca-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="009ca-124">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="009ca-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
