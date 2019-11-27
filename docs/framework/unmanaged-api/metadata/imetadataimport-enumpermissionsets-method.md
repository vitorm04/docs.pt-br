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
ms.openlocfilehash: 9d0f443b5b7d2d358534e888c3fc84ad3f554119
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450050"
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="d9e72-102">Método IMetaDataImport::EnumPermissionSets</span><span class="sxs-lookup"><span data-stu-id="d9e72-102">IMetaDataImport::EnumPermissionSets Method</span></span>
<span data-ttu-id="d9e72-103">Enumera permissões para os objetos em um escopo de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="d9e72-103">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9e72-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9e72-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d9e72-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d9e72-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d9e72-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="d9e72-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="d9e72-107">Isso deve ser nulo para a primeira chamada deste método.</span><span class="sxs-lookup"><span data-stu-id="d9e72-107">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="d9e72-108">no Um token de metadados que limita o escopo da pesquisa ou nulo para pesquisar o escopo mais amplo possível.</span><span class="sxs-lookup"><span data-stu-id="d9e72-108">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="d9e72-109">no Sinalizadores que representam os valores de <xref:System.Security.Permissions.SecurityAction> a serem incluídos no `rPermission`ou zero para retornar todas as ações.</span><span class="sxs-lookup"><span data-stu-id="d9e72-109">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="d9e72-110">fora A matriz usada para armazenar os tokens de permissão.</span><span class="sxs-lookup"><span data-stu-id="d9e72-110">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d9e72-111">no O tamanho máximo da matriz de `rPermission`.</span><span class="sxs-lookup"><span data-stu-id="d9e72-111">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d9e72-112">fora O número de tokens de permissão retornados em `rPermission`.</span><span class="sxs-lookup"><span data-stu-id="d9e72-112">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9e72-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d9e72-113">Return Value</span></span>  
  
|<span data-ttu-id="d9e72-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9e72-114">HRESULT</span></span>|<span data-ttu-id="d9e72-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9e72-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d9e72-116">`EnumPermissionSets` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="d9e72-116">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d9e72-117">Não há tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="d9e72-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="d9e72-118">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="d9e72-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d9e72-119">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9e72-119">Requirements</span></span>  
 <span data-ttu-id="d9e72-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9e72-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9e72-121">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d9e72-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d9e72-122">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d9e72-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d9e72-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9e72-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e72-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9e72-124">See also</span></span>

- [<span data-ttu-id="d9e72-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="d9e72-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d9e72-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="d9e72-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
