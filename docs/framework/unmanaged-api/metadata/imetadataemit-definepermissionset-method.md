---
title: "Método IMetaDataEmit::DefinePermissionSet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefinePermissionSet
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6a503f22710f392ecbb0ae2704d2c2950a858c30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="1e353-102">Método IMetaDataEmit::DefinePermissionSet</span><span class="sxs-lookup"><span data-stu-id="1e353-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="1e353-103">Cria uma definição para um conjunto de permissões com a assinatura de metadados especificado e recebe um token para essa definição de conjunto de permissões.</span><span class="sxs-lookup"><span data-stu-id="1e353-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e353-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1e353-104">Syntax</span></span>  
  
```  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1e353-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1e353-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="1e353-106">[in] O objeto a ser decorado.</span><span class="sxs-lookup"><span data-stu-id="1e353-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="1e353-107">[in] Um [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) valor que especifica o tipo de segurança declarativa para ser usado.</span><span class="sxs-lookup"><span data-stu-id="1e353-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="1e353-108">[in] O BLOB de permissão.</span><span class="sxs-lookup"><span data-stu-id="1e353-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="1e353-109">[in] O tamanho, em bytes, de `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="1e353-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="1e353-110">[out] O token retornado de permissão.</span><span class="sxs-lookup"><span data-stu-id="1e353-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e353-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1e353-111">Requirements</span></span>  
 <span data-ttu-id="1e353-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e353-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e353-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1e353-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1e353-114">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="1e353-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e353-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e353-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e353-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e353-116">See Also</span></span>  
 [<span data-ttu-id="1e353-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="1e353-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="1e353-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="1e353-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
