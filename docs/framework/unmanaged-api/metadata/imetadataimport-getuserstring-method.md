---
title: Método IMetaDataImport::GetUserString
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetUserString
helpviewer_keywords:
- IMetaDataImport::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0fd3bb47-58b5-4083-b241-b9719df7a285
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 358346af540c8b6b7ee1523e763bebbacf8cd2bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127810"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="6ed46-102">Método IMetaDataImport::GetUserString</span><span class="sxs-lookup"><span data-stu-id="6ed46-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="6ed46-103">Obtém a cadeia de caracteres literal, representada pelo token de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="6ed46-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ed46-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6ed46-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ed46-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6ed46-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="6ed46-106">[in] O token de cadeia de caracteres para retornar a cadeia de caracteres associada.</span><span class="sxs-lookup"><span data-stu-id="6ed46-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="6ed46-107">[out] Uma cópia da cadeia de caracteres solicitada.</span><span class="sxs-lookup"><span data-stu-id="6ed46-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="6ed46-108">[in] O tamanho máximo em caracteres largos da solicitada `szString`.</span><span class="sxs-lookup"><span data-stu-id="6ed46-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="6ed46-109">[out] O tamanho em caracteres largos da retornado `szString`.</span><span class="sxs-lookup"><span data-stu-id="6ed46-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ed46-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6ed46-110">Requirements</span></span>  
 <span data-ttu-id="6ed46-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ed46-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ed46-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6ed46-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6ed46-113">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="6ed46-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6ed46-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ed46-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ed46-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ed46-115">See also</span></span>

- [<span data-ttu-id="6ed46-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="6ed46-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6ed46-117">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="6ed46-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
