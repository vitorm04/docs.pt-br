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
ms.openlocfilehash: 52a00496c3b4d5ccd96adaf569c25c64a5709a9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717579"
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="4f25b-102">Método IMetaDataImport::IsGlobal</span><span class="sxs-lookup"><span data-stu-id="4f25b-102">IMetaDataImport::IsGlobal Method</span></span>
<span data-ttu-id="4f25b-103">Obtém um valor que indica se o campo, método ou tipo representado pelo token de metadados especificado tem escopo global.</span><span class="sxs-lookup"><span data-stu-id="4f25b-103">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f25b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f25b-104">Syntax</span></span>  
  
```  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f25b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4f25b-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="4f25b-106">[in] Um token de metadados que representa um tipo, campo ou método.</span><span class="sxs-lookup"><span data-stu-id="4f25b-106">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="4f25b-107">[out], 1 se o objeto tem escopo global; Caso contrário, 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="4f25b-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f25b-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4f25b-108">Requirements</span></span>  
 <span data-ttu-id="4f25b-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f25b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f25b-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4f25b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4f25b-111">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="4f25b-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4f25b-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f25b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f25b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f25b-113">See also</span></span>
- [<span data-ttu-id="4f25b-114">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="4f25b-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4f25b-115">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="4f25b-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
