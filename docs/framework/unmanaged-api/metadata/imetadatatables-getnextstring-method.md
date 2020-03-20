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
ms.openlocfilehash: a1cd932051a9ed90a29ff5eeaa818a67104192bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175246"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="317fc-102">Método IMetaDataTables::GetNextString</span><span class="sxs-lookup"><span data-stu-id="317fc-102">IMetaDataTables::GetNextString Method</span></span>
<span data-ttu-id="317fc-103">Obtém o índice da próxima string na coluna de tabela atual.</span><span class="sxs-lookup"><span data-stu-id="317fc-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="317fc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="317fc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextString (
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="317fc-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="317fc-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="317fc-106">[em] O valor do índice de uma coluna de tabela de strings.</span><span class="sxs-lookup"><span data-stu-id="317fc-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="317fc-107">[fora] Um ponteiro para o índice da próxima string na coluna.</span><span class="sxs-lookup"><span data-stu-id="317fc-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="317fc-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="317fc-108">Requirements</span></span>  
 <span data-ttu-id="317fc-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="317fc-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="317fc-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="317fc-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="317fc-111">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="317fc-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="317fc-112">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="317fc-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="317fc-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="317fc-113">See also</span></span>

- [<span data-ttu-id="317fc-114">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="317fc-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="317fc-115">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="317fc-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
