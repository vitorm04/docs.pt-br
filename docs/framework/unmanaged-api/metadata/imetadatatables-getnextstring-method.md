---
title: Método IMetaDataTables::GetNextString
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextString
helpviewer_keywords:
- IMetaDataTables::GetNextString method [.NET Framework metadata]
- GetNextString method [.NET Framework metadata]
ms.assetid: d9720428-c353-4f07-a7e8-899e106a1b37
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9b057b0537bbeff7433b776e64456ccc810cee54
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473481"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="bfbf0-102">Método IMetaDataTables::GetNextString</span><span class="sxs-lookup"><span data-stu-id="bfbf0-102">IMetaDataTables::GetNextString Method</span></span>
<span data-ttu-id="bfbf0-103">Obtém o índice da próxima cadeia de caracteres na coluna da tabela atual.</span><span class="sxs-lookup"><span data-stu-id="bfbf0-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfbf0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bfbf0-104">Syntax</span></span>  
  
```  
HRESULT GetNextString (   
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfbf0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bfbf0-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="bfbf0-106">[in] O valor de índice de uma coluna de tabela de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="bfbf0-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="bfbf0-107">[out] Um ponteiro para o índice da próxima cadeia de caracteres na coluna.</span><span class="sxs-lookup"><span data-stu-id="bfbf0-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfbf0-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bfbf0-108">Requirements</span></span>  
 <span data-ttu-id="bfbf0-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfbf0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfbf0-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bfbf0-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bfbf0-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="bfbf0-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bfbf0-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfbf0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfbf0-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bfbf0-113">See also</span></span>
- [<span data-ttu-id="bfbf0-114">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="bfbf0-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="bfbf0-115">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="bfbf0-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
