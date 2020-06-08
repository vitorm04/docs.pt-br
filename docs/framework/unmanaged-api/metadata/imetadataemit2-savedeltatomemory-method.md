---
title: Método IMetaDataEmit2::SaveDeltaToMemory
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToMemory
helpviewer_keywords:
- SaveDeltaToMemory method [.NET Framework metadata]
- IMetaDataEmit2::SaveDeltaToMemory method [.NET Framework metadata]
ms.assetid: e2146726-0084-4c9e-a2d2-e8d461b13b21
topic_type:
- apiref
ms.openlocfilehash: 8a6f11996425c92d9b0e3123ee2d3a064739454b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492738"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="344b9-102">Método IMetaDataEmit2::SaveDeltaToMemory</span><span class="sxs-lookup"><span data-stu-id="344b9-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="344b9-103">Salva as alterações da sessão de edição e continuação atual na memória.</span><span class="sxs-lookup"><span data-stu-id="344b9-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="344b9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="344b9-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,
    [in]  ULONG       cbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="344b9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="344b9-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="344b9-106">fora O endereço no qual começar a gravar o Delta de metadados.</span><span class="sxs-lookup"><span data-stu-id="344b9-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="344b9-107">no O tamanho das alterações.</span><span class="sxs-lookup"><span data-stu-id="344b9-107">[in] The size of the changes.</span></span> <span data-ttu-id="344b9-108">Use [IMetaDataEmit2:: GetDeltaSaveSize](imetadataemit2-getdeltasavesize-method.md) para determinar o tamanho.</span><span class="sxs-lookup"><span data-stu-id="344b9-108">Use [IMetaDataEmit2::GetDeltaSaveSize](imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="344b9-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="344b9-109">Requirements</span></span>  
 <span data-ttu-id="344b9-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="344b9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="344b9-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="344b9-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="344b9-112">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="344b9-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="344b9-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="344b9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="344b9-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="344b9-114">See also</span></span>

- [<span data-ttu-id="344b9-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="344b9-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="344b9-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="344b9-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
