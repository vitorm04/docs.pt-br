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
ms.openlocfilehash: 6f4764f016360a2ec0ab054b7a89ccb3f86aeb43
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490218"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="efced-102">Método IMetaDataTables::GetNextString</span><span class="sxs-lookup"><span data-stu-id="efced-102">IMetaDataTables::GetNextString Method</span></span>
<span data-ttu-id="efced-103">Obtém o índice da próxima cadeia de caracteres na coluna da tabela atual.</span><span class="sxs-lookup"><span data-stu-id="efced-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efced-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="efced-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextString (
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efced-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="efced-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="efced-106">no O valor de índice de uma coluna de tabela de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="efced-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="efced-107">fora Um ponteiro para o índice da próxima cadeia de caracteres na coluna.</span><span class="sxs-lookup"><span data-stu-id="efced-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efced-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="efced-108">Requirements</span></span>  
 <span data-ttu-id="efced-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efced-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efced-110">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="efced-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="efced-111">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="efced-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="efced-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efced-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efced-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="efced-113">See also</span></span>

- [<span data-ttu-id="efced-114">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="efced-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="efced-115">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="efced-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
