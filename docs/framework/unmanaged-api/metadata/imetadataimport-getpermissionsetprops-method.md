---
title: Método IMetaDataImport::GetPermissionSetProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPermissionSetProps
helpviewer_keywords:
- GetPermissionSetProps method [.NET Framework metadata]
- IMetaDataImport::GetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 9855f0e4-12c0-4d3d-ab5d-d6bc52d25eae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ff91a24dec7f8507989b701ea24b569c1670c89
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777605"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="b9383-102">Método IMetaDataImport::GetPermissionSetProps</span><span class="sxs-lookup"><span data-stu-id="b9383-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="b9383-103">Obtém os metadados associados a <xref:System.Security.PermissionSet?displayProperty=nameWithType> representado pelo token de permissão especificado.</span><span class="sxs-lookup"><span data-stu-id="b9383-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9383-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9383-104">Syntax</span></span>  
  
```  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,   
   [out] void const        **ppvPermission,   
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9383-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b9383-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="b9383-106">[in] O token de metadados de permissão que representa o conjunto de permissões para obter as propriedades de metadados.</span><span class="sxs-lookup"><span data-stu-id="b9383-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="b9383-107">[out] Um ponteiro para o conjunto de permissões.</span><span class="sxs-lookup"><span data-stu-id="b9383-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="b9383-108">[out] Um ponteiro para a assinatura binária de metadados do conjunto de permissões.</span><span class="sxs-lookup"><span data-stu-id="b9383-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="b9383-109">[out] O tamanho em bytes do `ppvPermission`.</span><span class="sxs-lookup"><span data-stu-id="b9383-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9383-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b9383-110">Requirements</span></span>  
 <span data-ttu-id="b9383-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9383-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9383-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b9383-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b9383-113">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b9383-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b9383-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9383-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9383-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9383-115">See also</span></span>

- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="b9383-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="b9383-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b9383-117">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="b9383-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
