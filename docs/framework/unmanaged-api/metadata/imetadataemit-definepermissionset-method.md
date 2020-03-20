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
ms.openlocfilehash: a0fd3fdb6dde9fd6b88ea6c64ed907c8a3e9e46d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175792"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="c97a9-102">Método IMetaDataEmit::DefinePermissionSet</span><span class="sxs-lookup"><span data-stu-id="c97a9-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="c97a9-103">Cria uma definição para um conjunto de permissões com a assinatura de metadados especificada e obtém um token para essa definição de conjunto de permissões.</span><span class="sxs-lookup"><span data-stu-id="c97a9-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c97a9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c97a9-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,
    [in]  DWORD          dwAction,
    [in]  void const     *pvPermission,
    [in]  ULONG          cbPermission,
    [out] mdPermission   *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c97a9-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="c97a9-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="c97a9-106">[em] O objeto a ser decorado.</span><span class="sxs-lookup"><span data-stu-id="c97a9-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="c97a9-107">[em] Um valor [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) que especifica o tipo de segurança declarativa a ser usada.</span><span class="sxs-lookup"><span data-stu-id="c97a9-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="c97a9-108">[em] A permissão BLOB.</span><span class="sxs-lookup"><span data-stu-id="c97a9-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="c97a9-109">[em] O tamanho, em bytes, de `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="c97a9-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="c97a9-110">[fora] O sinal de permissão devolvido.</span><span class="sxs-lookup"><span data-stu-id="c97a9-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c97a9-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c97a9-111">Requirements</span></span>  
 <span data-ttu-id="c97a9-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c97a9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c97a9-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c97a9-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c97a9-114">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c97a9-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c97a9-115">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c97a9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c97a9-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="c97a9-116">See also</span></span>

- [<span data-ttu-id="c97a9-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="c97a9-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c97a9-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="c97a9-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
