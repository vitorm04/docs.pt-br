---
title: "Método IMetaDataImport::GetScopeProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetScopeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5b0936a9f47e2d0fa52816b78a7eecf3d244d594
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetscopeprops-method"></a><span data-ttu-id="b50ee-102">Método IMetaDataImport::GetScopeProps</span><span class="sxs-lookup"><span data-stu-id="b50ee-102">IMetaDataImport::GetScopeProps Method</span></span>
<span data-ttu-id="b50ee-103">Obtém o nome e, opcionalmente, o identificador da versão do assembly ou módulo no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="b50ee-103">Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b50ee-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b50ee-104">Syntax</span></span>  
  
```  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b50ee-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b50ee-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="b50ee-106">[out] Um buffer para o nome do assembly ou módulo.</span><span class="sxs-lookup"><span data-stu-id="b50ee-106">[out] A buffer for the assembly or module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b50ee-107">[in] O tamanho em caracteres largos de `szName`.</span><span class="sxs-lookup"><span data-stu-id="b50ee-107">[in] The size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="b50ee-108">[out] O número de caracteres largos retornados em `szName`.</span><span class="sxs-lookup"><span data-stu-id="b50ee-108">[out] The number of wide characters returned in `szName`.</span></span>  
  
 `pmvid`  
 <span data-ttu-id="b50ee-109">[out, opcional] Um ponteiro para um GUID que identifica com exclusividade a versão do assembly ou módulo.</span><span class="sxs-lookup"><span data-stu-id="b50ee-109">[out, optional] A pointer to a GUID that uniquely identifies the version of the assembly or module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b50ee-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b50ee-110">Remarks</span></span>  
 <span data-ttu-id="b50ee-111">O [: Setmoduleprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) método é usado para definir essas propriedades.</span><span class="sxs-lookup"><span data-stu-id="b50ee-111">The [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) method is used to set these properties.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b50ee-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b50ee-112">Requirements</span></span>  
 <span data-ttu-id="b50ee-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b50ee-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b50ee-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b50ee-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b50ee-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b50ee-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b50ee-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b50ee-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b50ee-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b50ee-117">See Also</span></span>  
 [<span data-ttu-id="b50ee-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="b50ee-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b50ee-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="b50ee-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
