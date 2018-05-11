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
ms.openlocfilehash: 4156c3507ccbd21d59893c5e03e15fe9b7322e48
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="86ce7-102">Método IMetaDataImport::IsGlobal</span><span class="sxs-lookup"><span data-stu-id="86ce7-102">IMetaDataImport::IsGlobal Method</span></span>
<span data-ttu-id="86ce7-103">Obtém um valor que indica se o campo, método ou tipo representado pelo token de metadados especificado tem escopo global.</span><span class="sxs-lookup"><span data-stu-id="86ce7-103">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86ce7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86ce7-104">Syntax</span></span>  
  
```  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86ce7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="86ce7-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="86ce7-106">[in] Um token de metadados que representa um método, campo ou tipo.</span><span class="sxs-lookup"><span data-stu-id="86ce7-106">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="86ce7-107">[out] 1 se o objeto tem escopo global. Caso contrário, 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="86ce7-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86ce7-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="86ce7-108">Requirements</span></span>  
 <span data-ttu-id="86ce7-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86ce7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86ce7-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="86ce7-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="86ce7-111">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="86ce7-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="86ce7-112">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86ce7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86ce7-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86ce7-113">See Also</span></span>  
 [<span data-ttu-id="86ce7-114">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="86ce7-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="86ce7-115">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="86ce7-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
