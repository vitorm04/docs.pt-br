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
ms.openlocfilehash: eea43e5eaa037a3b70f482b0602d8d8d3d594f75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="ddb24-102">Método IMetaDataTables::GetNextString</span><span class="sxs-lookup"><span data-stu-id="ddb24-102">IMetaDataTables::GetNextString Method</span></span>
<span data-ttu-id="ddb24-103">Obtém o índice da seguinte cadeia de caracteres na coluna da tabela atual.</span><span class="sxs-lookup"><span data-stu-id="ddb24-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddb24-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ddb24-104">Syntax</span></span>  
  
```  
HRESULT GetNextString (   
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ddb24-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ddb24-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="ddb24-106">[in] O valor de índice de uma coluna de tabela de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ddb24-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="ddb24-107">[out] Um ponteiro para o índice da seguinte cadeia de caracteres na coluna.</span><span class="sxs-lookup"><span data-stu-id="ddb24-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddb24-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ddb24-108">Requirements</span></span>  
 <span data-ttu-id="ddb24-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddb24-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddb24-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ddb24-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ddb24-111">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ddb24-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ddb24-112">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddb24-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddb24-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ddb24-113">See Also</span></span>  
 [<span data-ttu-id="ddb24-114">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="ddb24-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="ddb24-115">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="ddb24-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
