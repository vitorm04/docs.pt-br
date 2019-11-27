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
ms.openlocfilehash: 4e11a52c977de7796043868e80c147d8cfd1f506
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431579"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="b8def-102">Método IMetaDataEmit::DefinePermissionSet</span><span class="sxs-lookup"><span data-stu-id="b8def-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="b8def-103">Cria uma definição para um conjunto de permissões com a assinatura de metadados especificada e Obtém um token para essa definição de conjunto de permissões.</span><span class="sxs-lookup"><span data-stu-id="b8def-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8def-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8def-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8def-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b8def-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="b8def-106">no O objeto a ser decorado.</span><span class="sxs-lookup"><span data-stu-id="b8def-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="b8def-107">no Um valor de [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) que especifica o tipo de segurança declarativa a ser usado.</span><span class="sxs-lookup"><span data-stu-id="b8def-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="b8def-108">no O BLOB de permissão.</span><span class="sxs-lookup"><span data-stu-id="b8def-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="b8def-109">no O tamanho, em bytes, de `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="b8def-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="b8def-110">fora O token de permissão retornado.</span><span class="sxs-lookup"><span data-stu-id="b8def-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8def-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="b8def-111">Requirements</span></span>  
 <span data-ttu-id="b8def-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8def-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8def-113">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b8def-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b8def-114">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b8def-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b8def-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8def-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8def-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8def-116">See also</span></span>

- [<span data-ttu-id="b8def-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="b8def-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b8def-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="b8def-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
