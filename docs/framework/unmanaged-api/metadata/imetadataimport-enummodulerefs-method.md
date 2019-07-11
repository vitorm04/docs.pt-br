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
ms.openlocfilehash: afa2d35a193a11360b52bcbdc1d9e5dae16d1c90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782122"
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="9acec-102">Método IMetaDataImport::EnumModuleRefs</span><span class="sxs-lookup"><span data-stu-id="9acec-102">IMetaDataImport::EnumModuleRefs Method</span></span>
<span data-ttu-id="9acec-103">Enumera ModuleRef tokens que representam os módulos importados.</span><span class="sxs-lookup"><span data-stu-id="9acec-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9acec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9acec-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9acec-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9acec-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="9acec-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="9acec-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="9acec-107">Isso deve ser NULL para a primeira chamada desse método.</span><span class="sxs-lookup"><span data-stu-id="9acec-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="9acec-108">[out] A matriz usada para armazenar os tokens ModuleRef.</span><span class="sxs-lookup"><span data-stu-id="9acec-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9acec-109">[in] O tamanho máximo da `rModuleRefs` matriz.</span><span class="sxs-lookup"><span data-stu-id="9acec-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="9acec-110">[out] O número de tokens ModuleRef retornado no `rModuleRefs`.</span><span class="sxs-lookup"><span data-stu-id="9acec-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9acec-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9acec-111">Return Value</span></span>  
  
|<span data-ttu-id="9acec-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9acec-112">HRESULT</span></span>|<span data-ttu-id="9acec-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="9acec-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9acec-114">`EnumModuleRefs` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="9acec-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9acec-115">Não há nenhum token para enumerar.</span><span class="sxs-lookup"><span data-stu-id="9acec-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="9acec-116">Nesse caso, `pcModuleRefs` é zero.</span><span class="sxs-lookup"><span data-stu-id="9acec-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9acec-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9acec-117">Requirements</span></span>  
 <span data-ttu-id="9acec-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9acec-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9acec-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9acec-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9acec-120">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="9acec-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9acec-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9acec-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9acec-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9acec-122">See also</span></span>

- [<span data-ttu-id="9acec-123">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="9acec-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="9acec-124">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="9acec-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
