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
ms.openlocfilehash: 5ec4fe2a8e949cf6e9aa0ce68f4d4e49b72170b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177432"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="049f0-102">Método IMetaDataEmit2::SaveDeltaToMemory</span><span class="sxs-lookup"><span data-stu-id="049f0-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="049f0-103">Salva alterações da sessão de edição e continuação atual para a memória.</span><span class="sxs-lookup"><span data-stu-id="049f0-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="049f0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="049f0-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,
    [in]  ULONG       cbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="049f0-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="049f0-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="049f0-106">[fora] O endereço para começar a escrever o delta de metadados.</span><span class="sxs-lookup"><span data-stu-id="049f0-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="049f0-107">[em] O tamanho das mudanças.</span><span class="sxs-lookup"><span data-stu-id="049f0-107">[in] The size of the changes.</span></span> <span data-ttu-id="049f0-108">Use [iMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) para determinar o tamanho.</span><span class="sxs-lookup"><span data-stu-id="049f0-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="049f0-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="049f0-109">Requirements</span></span>  
 <span data-ttu-id="049f0-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="049f0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="049f0-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="049f0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="049f0-112">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="049f0-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="049f0-113">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="049f0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="049f0-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="049f0-114">See also</span></span>

- [<span data-ttu-id="049f0-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="049f0-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="049f0-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="049f0-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
