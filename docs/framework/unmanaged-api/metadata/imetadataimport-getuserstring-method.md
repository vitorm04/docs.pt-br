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
ms.openlocfilehash: 358ca84f32e1b233116605bf5486cc9a01b42e67
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503491"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="762b8-102">Método IMetaDataImport::GetUserString</span><span class="sxs-lookup"><span data-stu-id="762b8-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="762b8-103">Obtém a cadeia de caracteres literal representada pelo token de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="762b8-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="762b8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="762b8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="762b8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="762b8-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="762b8-106">no O token da cadeia de caracteres para o qual retornar a cadeia de caracteres associada.</span><span class="sxs-lookup"><span data-stu-id="762b8-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="762b8-107">fora Uma cópia da cadeia de caracteres solicitada.</span><span class="sxs-lookup"><span data-stu-id="762b8-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="762b8-108">no O tamanho máximo em caracteres largos do solicitado `szString` .</span><span class="sxs-lookup"><span data-stu-id="762b8-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="762b8-109">fora O tamanho em caracteres largos do retornado `szString` .</span><span class="sxs-lookup"><span data-stu-id="762b8-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="762b8-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="762b8-110">Requirements</span></span>  
 <span data-ttu-id="762b8-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="762b8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="762b8-112">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="762b8-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="762b8-113">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="762b8-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="762b8-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="762b8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="762b8-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="762b8-115">See also</span></span>

- [<span data-ttu-id="762b8-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="762b8-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="762b8-117">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="762b8-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
