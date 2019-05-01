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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042283"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="71639-102">Método IMetaDataTables::GetString</span><span class="sxs-lookup"><span data-stu-id="71639-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="71639-103">Obtém a cadeia de caracteres no índice especificado da coluna de tabela no escopo atual de referência.</span><span class="sxs-lookup"><span data-stu-id="71639-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71639-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="71639-104">Syntax</span></span>  
  
```  
HRESULT GetString (   
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71639-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="71639-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="71639-106">[in] O índice no qual começar a procurar o próximo valor.</span><span class="sxs-lookup"><span data-stu-id="71639-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="71639-107">[out] Um ponteiro para um ponteiro para o valor de cadeia de caracteres retornada.</span><span class="sxs-lookup"><span data-stu-id="71639-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71639-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="71639-108">Requirements</span></span>  
 <span data-ttu-id="71639-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71639-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71639-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="71639-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="71639-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="71639-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="71639-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71639-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71639-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71639-113">See also</span></span>

- [<span data-ttu-id="71639-114">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="71639-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="71639-115">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="71639-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
