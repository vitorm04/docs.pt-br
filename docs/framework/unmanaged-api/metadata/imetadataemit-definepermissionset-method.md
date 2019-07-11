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
ms.openlocfilehash: 16675e8bfde74c1f9c30ac9d52f8eeb919d22477
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777531"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="35cb7-102">Método IMetaDataEmit::DefinePermissionSet</span><span class="sxs-lookup"><span data-stu-id="35cb7-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="35cb7-103">Cria uma definição para um conjunto de permissões com a assinatura de metadados especificado e obtém um token para essa definição de conjunto de permissões.</span><span class="sxs-lookup"><span data-stu-id="35cb7-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35cb7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="35cb7-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35cb7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="35cb7-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="35cb7-106">[in] O objeto a ser decorada.</span><span class="sxs-lookup"><span data-stu-id="35cb7-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="35cb7-107">[in] Um [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) valor que especifica o tipo de segurança declarativa a ser usado.</span><span class="sxs-lookup"><span data-stu-id="35cb7-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="35cb7-108">[in] A permissão de BLOB.</span><span class="sxs-lookup"><span data-stu-id="35cb7-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="35cb7-109">[in] O tamanho, em bytes, do `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="35cb7-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="35cb7-110">[out] O token retornado de permissão.</span><span class="sxs-lookup"><span data-stu-id="35cb7-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35cb7-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="35cb7-111">Requirements</span></span>  
 <span data-ttu-id="35cb7-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35cb7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35cb7-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="35cb7-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="35cb7-114">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="35cb7-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="35cb7-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35cb7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35cb7-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35cb7-116">See also</span></span>

- [<span data-ttu-id="35cb7-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="35cb7-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="35cb7-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="35cb7-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
