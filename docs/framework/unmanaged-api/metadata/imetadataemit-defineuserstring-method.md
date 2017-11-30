---
title: "Método IMetaDataEmit::DefineUserString"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineUserString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineUserString
helpviewer_keywords:
- DefineUserString method [.NET Framework metadata]
- IMetaDataEmit::DefineUserString method [.NET Framework metadata]
ms.assetid: 88fb7ef3-bbdf-429c-b678-c9c153456461
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: eb3e21e88da8fec08acf1ecbe451c5914b6cccaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="c5d98-102">Método IMetaDataEmit::DefineUserString</span><span class="sxs-lookup"><span data-stu-id="c5d98-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="c5d98-103">Obtém metadados de um token de cadeia de caracteres literal especificada.</span><span class="sxs-lookup"><span data-stu-id="c5d98-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5d98-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5d98-104">Syntax</span></span>  
  
```  
HRESULT DefineUserString (   
    [in]  LPCWSTR     szString,   
    [in]  ULONG       cchString,   
    [out] mdString    *pstk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5d98-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c5d98-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="c5d98-106">[in] A cadeia de caracteres do usuário para armazenar.</span><span class="sxs-lookup"><span data-stu-id="c5d98-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="c5d98-107">[in] A contagem de caracteres largos em `szString`.</span><span class="sxs-lookup"><span data-stu-id="c5d98-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="c5d98-108">[out] O token de cadeia de caracteres atribuído.</span><span class="sxs-lookup"><span data-stu-id="c5d98-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5d98-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c5d98-109">Requirements</span></span>  
 <span data-ttu-id="c5d98-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5d98-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5d98-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c5d98-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c5d98-112">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="c5d98-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5d98-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5d98-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5d98-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5d98-114">See Also</span></span>  
 [<span data-ttu-id="c5d98-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="c5d98-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="c5d98-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="c5d98-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
