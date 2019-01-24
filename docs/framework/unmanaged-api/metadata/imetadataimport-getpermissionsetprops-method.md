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
ms.openlocfilehash: bdee4df6964097f1c333a8fe96756a8898f7c1cc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54598887"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="e19ee-102">Método IMetaDataImport::GetPermissionSetProps</span><span class="sxs-lookup"><span data-stu-id="e19ee-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="e19ee-103">Obtém os metadados associados a <xref:System.Security.PermissionSet?displayProperty=nameWithType> representado pelo token de permissão especificado.</span><span class="sxs-lookup"><span data-stu-id="e19ee-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e19ee-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e19ee-104">Syntax</span></span>  
  
```  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,   
   [out] void const        **ppvPermission,   
   [out] ULONG             *pcbPermission  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e19ee-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e19ee-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="e19ee-106">[in] O token de metadados de permissão que representa o conjunto de permissões para obter as propriedades de metadados.</span><span class="sxs-lookup"><span data-stu-id="e19ee-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="e19ee-107">[out] Um ponteiro para o conjunto de permissões.</span><span class="sxs-lookup"><span data-stu-id="e19ee-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="e19ee-108">[out] Um ponteiro para a assinatura binária de metadados do conjunto de permissões.</span><span class="sxs-lookup"><span data-stu-id="e19ee-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="e19ee-109">[out] O tamanho em bytes do `ppvPermission`.</span><span class="sxs-lookup"><span data-stu-id="e19ee-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e19ee-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e19ee-110">Requirements</span></span>  
 <span data-ttu-id="e19ee-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e19ee-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e19ee-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e19ee-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e19ee-113">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e19ee-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e19ee-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e19ee-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e19ee-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e19ee-115">See also</span></span>
- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="e19ee-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="e19ee-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e19ee-117">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="e19ee-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
