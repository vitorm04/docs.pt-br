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
ms.openlocfilehash: 6d62739148280c7333cf7cdb6002b59a145496e3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503556"
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="798b2-102">Método IMetaDataImport::GetNameFromToken</span><span class="sxs-lookup"><span data-stu-id="798b2-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="798b2-103">Obtém o nome UTF-8 do objeto referenciado pelo token de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="798b2-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="798b2-104">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="798b2-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="798b2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="798b2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="798b2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="798b2-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="798b2-107">no O token que representa o objeto para o qual retornar o nome.</span><span class="sxs-lookup"><span data-stu-id="798b2-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="798b2-108">fora Um ponteiro para o nome do objeto UTF-8 no heap.</span><span class="sxs-lookup"><span data-stu-id="798b2-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="798b2-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="798b2-109">Remarks</span></span>  
 <span data-ttu-id="798b2-110">`GetNameFromToken` é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="798b2-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="798b2-111">Como alternativa, chame um método para obter as propriedades do tipo específico de token necessário, como `GetFieldProps` para um campo ou `GetMethodProps` para um método.</span><span class="sxs-lookup"><span data-stu-id="798b2-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="798b2-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="798b2-112">Requirements</span></span>  
 <span data-ttu-id="798b2-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="798b2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="798b2-114">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="798b2-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="798b2-115">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="798b2-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="798b2-116">**Versões do .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="798b2-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="798b2-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="798b2-117">See also</span></span>

- [<span data-ttu-id="798b2-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="798b2-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="798b2-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="798b2-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
