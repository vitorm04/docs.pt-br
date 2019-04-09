---
title: Método IMetaDataTables::GetString
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetString
helpviewer_keywords:
- IMetaDataTables::GetString method [.NET Framework metadata]
- GetString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 895c35cf-b95d-4e3b-93b5-cfc1cf9044fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8fed98521c0609ebd8b5f65885d69c77814e9e85
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119334"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="f12ba-102">Método IMetaDataTables::GetString</span><span class="sxs-lookup"><span data-stu-id="f12ba-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="f12ba-103">Obtém a cadeia de caracteres no índice especificado da coluna de tabela no escopo atual de referência.</span><span class="sxs-lookup"><span data-stu-id="f12ba-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f12ba-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f12ba-104">Syntax</span></span>  
  
```  
HRESULT GetString (   
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f12ba-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f12ba-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="f12ba-106">[in] O índice no qual começar a procurar o próximo valor.</span><span class="sxs-lookup"><span data-stu-id="f12ba-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="f12ba-107">[out] Um ponteiro para um ponteiro para o valor de cadeia de caracteres retornada.</span><span class="sxs-lookup"><span data-stu-id="f12ba-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f12ba-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f12ba-108">Requirements</span></span>  
 <span data-ttu-id="f12ba-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f12ba-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f12ba-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f12ba-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f12ba-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f12ba-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="f12ba-112">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="f12ba-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f12ba-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f12ba-113">See also</span></span>

- [<span data-ttu-id="f12ba-114">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="f12ba-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="f12ba-115">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="f12ba-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
