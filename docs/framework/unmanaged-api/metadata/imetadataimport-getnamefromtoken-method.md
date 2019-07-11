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
ms.openlocfilehash: fa6e8665e5e2194eb4a3dffad8e97a69deb202d0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778984"
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="74332-102">Método IMetaDataImport::GetNameFromToken</span><span class="sxs-lookup"><span data-stu-id="74332-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="74332-103">Obtém o nome de UTF-8 do objeto referenciado pelo token de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="74332-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="74332-104">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="74332-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74332-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="74332-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74332-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="74332-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="74332-107">[in] O token que representa o objeto para retornar o nome para o.</span><span class="sxs-lookup"><span data-stu-id="74332-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="74332-108">[out] Um ponteiro para o nome do objeto UTF-8 no heap.</span><span class="sxs-lookup"><span data-stu-id="74332-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74332-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="74332-109">Remarks</span></span>  
 <span data-ttu-id="74332-110">`GetNameFromToken` é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="74332-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="74332-111">Como alternativa, chamar um método para obter as propriedades de um determinado tipo de token necessário, como `GetFieldProps` para um campo ou `GetMethodProps` para um método.</span><span class="sxs-lookup"><span data-stu-id="74332-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74332-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="74332-112">Requirements</span></span>  
 <span data-ttu-id="74332-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74332-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74332-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="74332-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="74332-115">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="74332-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="74332-116">**Versões do .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="74332-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74332-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74332-117">See also</span></span>

- [<span data-ttu-id="74332-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="74332-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="74332-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="74332-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
