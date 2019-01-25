---
title: Método IMetaDataImport::EnumModuleRefs
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumModuleRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumModuleRefs
helpviewer_keywords:
- EnumModuleRefs method [.NET Framework metadata]
- IMetaDataImport::EnumModuleRefs method [.NET Framework metadata]
ms.assetid: 53441f3a-68d2-477c-906e-37c55dfcfb4d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e84581a0642fe5bee3b88b6774ab2155fd2736a0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490778"
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="33b68-102">Método IMetaDataImport::EnumModuleRefs</span><span class="sxs-lookup"><span data-stu-id="33b68-102">IMetaDataImport::EnumModuleRefs Method</span></span>
<span data-ttu-id="33b68-103">Enumera ModuleRef tokens que representam os módulos importados.</span><span class="sxs-lookup"><span data-stu-id="33b68-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33b68-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="33b68-104">Syntax</span></span>  
  
```  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33b68-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="33b68-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="33b68-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="33b68-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="33b68-107">Isso deve ser NULL para a primeira chamada desse método.</span><span class="sxs-lookup"><span data-stu-id="33b68-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="33b68-108">[out] A matriz usada para armazenar os tokens ModuleRef.</span><span class="sxs-lookup"><span data-stu-id="33b68-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="33b68-109">[in] O tamanho máximo da `rModuleRefs` matriz.</span><span class="sxs-lookup"><span data-stu-id="33b68-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="33b68-110">[out] O número de tokens ModuleRef retornado no `rModuleRefs`.</span><span class="sxs-lookup"><span data-stu-id="33b68-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33b68-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="33b68-111">Return Value</span></span>  
  
|<span data-ttu-id="33b68-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="33b68-112">HRESULT</span></span>|<span data-ttu-id="33b68-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="33b68-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="33b68-114">`EnumModuleRefs` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="33b68-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="33b68-115">Não há nenhum token para enumerar.</span><span class="sxs-lookup"><span data-stu-id="33b68-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="33b68-116">Nesse caso, `pcModuleRefs` é zero.</span><span class="sxs-lookup"><span data-stu-id="33b68-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="33b68-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="33b68-117">Requirements</span></span>  
 <span data-ttu-id="33b68-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33b68-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33b68-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="33b68-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="33b68-120">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="33b68-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="33b68-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33b68-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33b68-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33b68-122">See also</span></span>
- [<span data-ttu-id="33b68-123">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="33b68-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="33b68-124">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="33b68-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
