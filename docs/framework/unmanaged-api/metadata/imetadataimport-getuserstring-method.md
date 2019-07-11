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
ms.openlocfilehash: edeaefd0792a5cc03ae6d4385ff669a343ffdfc9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778814"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="0aa24-102">Método IMetaDataImport::GetUserString</span><span class="sxs-lookup"><span data-stu-id="0aa24-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="0aa24-103">Obtém a cadeia de caracteres literal, representada pelo token de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="0aa24-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aa24-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0aa24-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0aa24-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0aa24-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="0aa24-106">[in] O token de cadeia de caracteres para retornar a cadeia de caracteres associada.</span><span class="sxs-lookup"><span data-stu-id="0aa24-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="0aa24-107">[out] Uma cópia da cadeia de caracteres solicitada.</span><span class="sxs-lookup"><span data-stu-id="0aa24-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="0aa24-108">[in] O tamanho máximo em caracteres largos da solicitada `szString`.</span><span class="sxs-lookup"><span data-stu-id="0aa24-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="0aa24-109">[out] O tamanho em caracteres largos da retornado `szString`.</span><span class="sxs-lookup"><span data-stu-id="0aa24-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0aa24-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0aa24-110">Requirements</span></span>  
 <span data-ttu-id="0aa24-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0aa24-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0aa24-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0aa24-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0aa24-113">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0aa24-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0aa24-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0aa24-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aa24-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0aa24-115">See also</span></span>

- [<span data-ttu-id="0aa24-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="0aa24-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0aa24-117">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="0aa24-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
