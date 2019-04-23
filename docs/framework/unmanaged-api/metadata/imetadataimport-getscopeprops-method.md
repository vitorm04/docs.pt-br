---
title: Método IMetaDataImport::GetScopeProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetScopeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 17568a46c8e946989af0e401366d7eaa885886da
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220962"
---
# <a name="imetadataimportgetscopeprops-method"></a><span data-ttu-id="29b68-102">Método IMetaDataImport::GetScopeProps</span><span class="sxs-lookup"><span data-stu-id="29b68-102">IMetaDataImport::GetScopeProps Method</span></span>
<span data-ttu-id="29b68-103">Obtém o nome e, opcionalmente, o identificador de versão do assembly ou módulo no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="29b68-103">Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29b68-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29b68-104">Syntax</span></span>  
  
```  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29b68-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="29b68-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="29b68-106">[out] Um buffer para o nome do assembly ou módulo.</span><span class="sxs-lookup"><span data-stu-id="29b68-106">[out] A buffer for the assembly or module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="29b68-107">[in] O tamanho em caracteres largos da `szName`.</span><span class="sxs-lookup"><span data-stu-id="29b68-107">[in] The size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="29b68-108">[out] O número de caracteres largos retornado no `szName`.</span><span class="sxs-lookup"><span data-stu-id="29b68-108">[out] The number of wide characters returned in `szName`.</span></span>  
  
 `pmvid`  
 <span data-ttu-id="29b68-109">[out, opcional] Um ponteiro para um GUID que identifica com exclusividade a versão do assembly ou módulo.</span><span class="sxs-lookup"><span data-stu-id="29b68-109">[out, optional] A pointer to a GUID that uniquely identifies the version of the assembly or module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29b68-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="29b68-110">Remarks</span></span>  
 <span data-ttu-id="29b68-111">O [imetadataemit:: Setmoduleprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) método é usado para definir essas propriedades.</span><span class="sxs-lookup"><span data-stu-id="29b68-111">The [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) method is used to set these properties.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29b68-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29b68-112">Requirements</span></span>  
 <span data-ttu-id="29b68-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29b68-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29b68-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="29b68-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="29b68-115">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="29b68-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="29b68-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29b68-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29b68-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29b68-117">See also</span></span>

- [<span data-ttu-id="29b68-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="29b68-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="29b68-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="29b68-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
