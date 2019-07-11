---
title: Método IMetaDataImport::IsGlobal
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsGlobal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsGlobal
helpviewer_keywords:
- IsGlobal method [.NET Framework metadata]
- IMetaDataImport::IsGlobal method [.NET Framework metadata]
ms.assetid: 44cf6908-f555-4ae8-b2cf-24bd974bf2fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 13f8a50f3fcbe9d6e7602ca3bbeb36587ecff32c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778791"
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="24d98-102">Método IMetaDataImport::IsGlobal</span><span class="sxs-lookup"><span data-stu-id="24d98-102">IMetaDataImport::IsGlobal Method</span></span>
<span data-ttu-id="24d98-103">Obtém um valor que indica se o campo, método ou tipo representado pelo token de metadados especificado tem escopo global.</span><span class="sxs-lookup"><span data-stu-id="24d98-103">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24d98-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="24d98-104">Syntax</span></span>  
  
```cpp  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24d98-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="24d98-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="24d98-106">[in] Um token de metadados que representa um tipo, campo ou método.</span><span class="sxs-lookup"><span data-stu-id="24d98-106">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="24d98-107">[out], 1 se o objeto tem escopo global; Caso contrário, 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="24d98-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24d98-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="24d98-108">Requirements</span></span>  
 <span data-ttu-id="24d98-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24d98-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24d98-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="24d98-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="24d98-111">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="24d98-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="24d98-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24d98-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24d98-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24d98-113">See also</span></span>

- [<span data-ttu-id="24d98-114">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="24d98-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="24d98-115">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="24d98-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
