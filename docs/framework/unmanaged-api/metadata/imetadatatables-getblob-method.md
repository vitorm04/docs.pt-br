---
title: Método IMetaDataTables::GetBlob
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlob
helpviewer_keywords:
- GetBlob method [.NET Framework metadata]
- IMetaDataTables::GetBlob method [.NET Framework metadata]
ms.assetid: 94667c1c-6d58-4aa7-b74e-530b11e2a276
topic_type:
- apiref
ms.openlocfilehash: ff97e419c5309fa7cb820cb7e82db96fee34f30c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501268"
---
# <a name="imetadatatablesgetblob-method"></a><span data-ttu-id="b5d32-102">Método IMetaDataTables::GetBlob</span><span class="sxs-lookup"><span data-stu-id="b5d32-102">IMetaDataTables::GetBlob Method</span></span>
<span data-ttu-id="b5d32-103">Obtém um ponteiro para o objeto binário grande (BLOB) no índice de coluna especificado.</span><span class="sxs-lookup"><span data-stu-id="b5d32-103">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5d32-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5d32-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5d32-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b5d32-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="b5d32-106">no O endereço de memória do qual obter `ppData` .</span><span class="sxs-lookup"><span data-stu-id="b5d32-106">[in] The memory address from which to get `ppData`.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="b5d32-107">fora Um ponteiro para o tamanho, em bytes, de `ppData` .</span><span class="sxs-lookup"><span data-stu-id="b5d32-107">[out] A pointer to the size, in bytes, of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="b5d32-108">fora Um ponteiro para um ponteiro para os dados binários recuperados.</span><span class="sxs-lookup"><span data-stu-id="b5d32-108">[out] A pointer to a pointer to the binary data retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5d32-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b5d32-109">Requirements</span></span>  
 <span data-ttu-id="b5d32-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5d32-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5d32-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b5d32-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b5d32-112">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b5d32-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b5d32-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5d32-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5d32-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="b5d32-114">See also</span></span>

- [<span data-ttu-id="b5d32-115">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="b5d32-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="b5d32-116">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="b5d32-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
