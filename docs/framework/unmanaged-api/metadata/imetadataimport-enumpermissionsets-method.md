---
title: Método IMetaDataImport::EnumPermissionSets
ms.date: 03/30/2017
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
ms.openlocfilehash: e628cf5dab8006b0df0ab6c60dc995cd0c6bb29d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175441"
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="6ca89-102">Método IMetaDataImport::EnumPermissionSets</span><span class="sxs-lookup"><span data-stu-id="6ca89-102">IMetaDataImport::EnumPermissionSets Method</span></span>
<span data-ttu-id="6ca89-103">Enumera permissões para os objetos em um escopo de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="6ca89-103">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ca89-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6ca89-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,
   [in]      mdToken       tk,
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ca89-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="6ca89-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="6ca89-106">[dentro, fora] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="6ca89-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="6ca89-107">Isto deve ser NULO para a primeira chamada deste método.</span><span class="sxs-lookup"><span data-stu-id="6ca89-107">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="6ca89-108">[em] Um token de metadados que limita o escopo da pesquisa ou NULL para pesquisar o escopo mais amplo possível.</span><span class="sxs-lookup"><span data-stu-id="6ca89-108">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="6ca89-109">[em] Bandeiras representando <xref:System.Security.Permissions.SecurityAction> os valores a serem incluemem , `rPermission`ou zero para retornar todas as ações.</span><span class="sxs-lookup"><span data-stu-id="6ca89-109">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="6ca89-110">[fora] A matriz usada para armazenar os tokens de permissão.</span><span class="sxs-lookup"><span data-stu-id="6ca89-110">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6ca89-111">[em] O tamanho máximo `rPermission` da matriz.</span><span class="sxs-lookup"><span data-stu-id="6ca89-111">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="6ca89-112">[fora] O número de tokens `rPermission`de permissão retornado em .</span><span class="sxs-lookup"><span data-stu-id="6ca89-112">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ca89-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="6ca89-113">Return Value</span></span>  
  
|<span data-ttu-id="6ca89-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6ca89-114">HRESULT</span></span>|<span data-ttu-id="6ca89-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="6ca89-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6ca89-116">`EnumPermissionSets`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="6ca89-116">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6ca89-117">Não há tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="6ca89-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="6ca89-118">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="6ca89-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6ca89-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6ca89-119">Requirements</span></span>  
 <span data-ttu-id="6ca89-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ca89-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ca89-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6ca89-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6ca89-122">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6ca89-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6ca89-123">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ca89-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ca89-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="6ca89-124">See also</span></span>

- [<span data-ttu-id="6ca89-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="6ca89-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6ca89-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="6ca89-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
