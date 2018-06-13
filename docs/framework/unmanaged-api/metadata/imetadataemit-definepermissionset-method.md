---
title: Método IMetaDataEmit::DefinePermissionSet
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePermissionSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 05339787b112ad029cb9870e8c6ffca37e55e631
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445183"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="65b2a-102">Método IMetaDataEmit::DefinePermissionSet</span><span class="sxs-lookup"><span data-stu-id="65b2a-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="65b2a-103">Cria uma definição para um conjunto de permissões com a assinatura de metadados especificado e recebe um token para essa definição de conjunto de permissões.</span><span class="sxs-lookup"><span data-stu-id="65b2a-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65b2a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65b2a-104">Syntax</span></span>  
  
```  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65b2a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="65b2a-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="65b2a-106">[in] O objeto a ser decorado.</span><span class="sxs-lookup"><span data-stu-id="65b2a-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="65b2a-107">[in] Um [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) valor que especifica o tipo de segurança declarativa para ser usado.</span><span class="sxs-lookup"><span data-stu-id="65b2a-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="65b2a-108">[in] O BLOB de permissão.</span><span class="sxs-lookup"><span data-stu-id="65b2a-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="65b2a-109">[in] O tamanho, em bytes, de `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="65b2a-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="65b2a-110">[out] O token retornado de permissão.</span><span class="sxs-lookup"><span data-stu-id="65b2a-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65b2a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65b2a-111">Requirements</span></span>  
 <span data-ttu-id="65b2a-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65b2a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65b2a-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="65b2a-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65b2a-114">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="65b2a-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65b2a-115">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65b2a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65b2a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65b2a-116">See Also</span></span>  
 [<span data-ttu-id="65b2a-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="65b2a-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="65b2a-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="65b2a-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
