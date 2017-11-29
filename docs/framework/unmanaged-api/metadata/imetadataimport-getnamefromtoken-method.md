---
title: "Método IMetaDataImport::GetNameFromToken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetNameFromToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e77954d5730417a005c6c1ac07fa171bd0f1b13a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="51ef9-102">Método IMetaDataImport::GetNameFromToken</span><span class="sxs-lookup"><span data-stu-id="51ef9-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="51ef9-103">Obtém o nome de UTF-8 do objeto referenciado pelo token de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="51ef9-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="51ef9-104">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="51ef9-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51ef9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51ef9-105">Syntax</span></span>  
  
```  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51ef9-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="51ef9-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="51ef9-107">[in] O token que representa o objeto para retornar o nome.</span><span class="sxs-lookup"><span data-stu-id="51ef9-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="51ef9-108">[out] Um ponteiro para o nome do objeto UTF-8 no heap.</span><span class="sxs-lookup"><span data-stu-id="51ef9-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51ef9-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="51ef9-109">Remarks</span></span>  
 <span data-ttu-id="51ef9-110">`GetNameFromToken` é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="51ef9-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="51ef9-111">Como alternativa, chamar um método para obter as propriedades de um determinado tipo de token necessário, como `GetFieldProps` para um campo ou `GetMethodProps` para um método.</span><span class="sxs-lookup"><span data-stu-id="51ef9-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51ef9-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="51ef9-112">Requirements</span></span>  
 <span data-ttu-id="51ef9-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51ef9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51ef9-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="51ef9-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="51ef9-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="51ef9-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="51ef9-116">**Versões do .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="51ef9-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51ef9-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51ef9-117">See Also</span></span>  
 [<span data-ttu-id="51ef9-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="51ef9-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="51ef9-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="51ef9-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
