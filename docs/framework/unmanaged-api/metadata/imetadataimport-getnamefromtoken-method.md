---
title: Método IMetaDataImport::GetNameFromToken
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNameFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a39eac88537d47535844d1f05e0741cc94142f0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447247"
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="bbefa-102">Método IMetaDataImport::GetNameFromToken</span><span class="sxs-lookup"><span data-stu-id="bbefa-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="bbefa-103">Obtém o nome de UTF-8 do objeto referenciado pelo token de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="bbefa-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="bbefa-104">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="bbefa-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbefa-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bbefa-105">Syntax</span></span>  
  
```  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bbefa-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bbefa-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="bbefa-107">[in] O token que representa o objeto para retornar o nome.</span><span class="sxs-lookup"><span data-stu-id="bbefa-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="bbefa-108">[out] Um ponteiro para o nome do objeto UTF-8 no heap.</span><span class="sxs-lookup"><span data-stu-id="bbefa-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbefa-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="bbefa-109">Remarks</span></span>  
 <span data-ttu-id="bbefa-110">`GetNameFromToken` é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="bbefa-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="bbefa-111">Como alternativa, chamar um método para obter as propriedades de um determinado tipo de token necessário, como `GetFieldProps` para um campo ou `GetMethodProps` para um método.</span><span class="sxs-lookup"><span data-stu-id="bbefa-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbefa-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bbefa-112">Requirements</span></span>  
 <span data-ttu-id="bbefa-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbefa-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbefa-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bbefa-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bbefa-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="bbefa-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bbefa-116">**Versões do .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="bbefa-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbefa-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbefa-117">See Also</span></span>  
 [<span data-ttu-id="bbefa-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="bbefa-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="bbefa-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="bbefa-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
