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
ms.openlocfilehash: 216a1f7bd2ff5a596fa7abf7874b5e603d5a9f7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175233"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="aa50c-102">Método IMetaDataTables::GetString</span><span class="sxs-lookup"><span data-stu-id="aa50c-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="aa50c-103">Obtém a seqüência no índice especificado da coluna de tabela no escopo de referência atual.</span><span class="sxs-lookup"><span data-stu-id="aa50c-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa50c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa50c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa50c-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="aa50c-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="aa50c-106">[em] O índice para começar a procurar o próximo valor.</span><span class="sxs-lookup"><span data-stu-id="aa50c-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="aa50c-107">[fora] Um ponteiro para um ponteiro para o valor da seqüência retornado.</span><span class="sxs-lookup"><span data-stu-id="aa50c-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa50c-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aa50c-108">Requirements</span></span>  
 <span data-ttu-id="aa50c-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa50c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa50c-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="aa50c-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aa50c-111">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aa50c-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aa50c-112">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa50c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa50c-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="aa50c-113">See also</span></span>

- [<span data-ttu-id="aa50c-114">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="aa50c-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="aa50c-115">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="aa50c-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
