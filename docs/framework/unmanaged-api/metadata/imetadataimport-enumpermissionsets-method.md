---
title: "Método IMetaDataImport::EnumPermissionSets"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.EnumPermissionSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumPermissionSets
helpviewer_keywords:
- EnumPermissionSets method [.NET Framework metadata]
- IMetaDataImport::EnumPermissionSets method [.NET Framework metadata]
ms.assetid: 347d7e5c-c90f-45ad-bd1e-2c7912b0b19c
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7f31d35f21a16983b6ab9c23f1f65c3916b5138d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="bd9c9-102">Método IMetaDataImport::EnumPermissionSets</span><span class="sxs-lookup"><span data-stu-id="bd9c9-102">IMetaDataImport::EnumPermissionSets Method</span></span>
<span data-ttu-id="bd9c9-103">Enumera as permissões para os objetos em um escopo de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="bd9c9-103">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd9c9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd9c9-104">Syntax</span></span>  
  
```  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,   
   [in]      mdToken       tk,   
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bd9c9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bd9c9-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="bd9c9-106">[out no] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="bd9c9-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="bd9c9-107">Isso deve ser NULL para a primeira chamada do método.</span><span class="sxs-lookup"><span data-stu-id="bd9c9-107">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="bd9c9-108">[in] Um token de metadados que limita o escopo da pesquisa, ou NULL para pesquisar o escopo mais amplo possível.</span><span class="sxs-lookup"><span data-stu-id="bd9c9-108">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="bd9c9-109">[in] Sinaliza que representa o <xref:System.Security.Permissions.SecurityAction> valores para incluir na `rPermission`, ou zero para retornar todas as ações.</span><span class="sxs-lookup"><span data-stu-id="bd9c9-109">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="bd9c9-110">[out] A matriz usada para armazenar os tokens de permissão.</span><span class="sxs-lookup"><span data-stu-id="bd9c9-110">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="bd9c9-111">[in] O tamanho máximo da `rPermission` matriz.</span><span class="sxs-lookup"><span data-stu-id="bd9c9-111">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="bd9c9-112">[out] O número de tokens de permissão retornados em `rPermission`.</span><span class="sxs-lookup"><span data-stu-id="bd9c9-112">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd9c9-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bd9c9-113">Return Value</span></span>  
  
|<span data-ttu-id="bd9c9-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bd9c9-114">HRESULT</span></span>|<span data-ttu-id="bd9c9-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="bd9c9-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="bd9c9-116">`EnumPermissionSets`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="bd9c9-116">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="bd9c9-117">Não há nenhum tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="bd9c9-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="bd9c9-118">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="bd9c9-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bd9c9-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bd9c9-119">Requirements</span></span>  
 <span data-ttu-id="bd9c9-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd9c9-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd9c9-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bd9c9-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bd9c9-122">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="bd9c9-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bd9c9-123">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd9c9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd9c9-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd9c9-124">See Also</span></span>  
 [<span data-ttu-id="bd9c9-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="bd9c9-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="bd9c9-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="bd9c9-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
