---
title: Método IMetaDataTables::GetNextBlob
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextBlob
helpviewer_keywords:
- IMetaDataTables::GetNextBlob method [.NET Framework metadata]
- GetNextBlob method [.NET Framework metadata]
ms.assetid: 017c8ab4-4c09-4754-9935-5b0b49cabecb
topic_type:
- apiref
ms.openlocfilehash: 086448248364403b718408ad8bd32e48447742d0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490374"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="04e66-102">Método IMetaDataTables::GetNextBlob</span><span class="sxs-lookup"><span data-stu-id="04e66-102">IMetaDataTables::GetNextBlob Method</span></span>
<span data-ttu-id="04e66-103">Obtém o índice do próximo objeto binário grande (BLOB) na tabela.</span><span class="sxs-lookup"><span data-stu-id="04e66-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04e66-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="04e66-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04e66-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="04e66-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="04e66-106">no O índice, como retornado de uma coluna de BLOBs.</span><span class="sxs-lookup"><span data-stu-id="04e66-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="04e66-107">fora Um ponteiro para o índice do próximo BLOB.</span><span class="sxs-lookup"><span data-stu-id="04e66-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04e66-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="04e66-108">Requirements</span></span>  
 <span data-ttu-id="04e66-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04e66-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04e66-110">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="04e66-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="04e66-111">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="04e66-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="04e66-112">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04e66-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e66-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="04e66-113">See also</span></span>

- [<span data-ttu-id="04e66-114">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="04e66-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="04e66-115">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="04e66-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
