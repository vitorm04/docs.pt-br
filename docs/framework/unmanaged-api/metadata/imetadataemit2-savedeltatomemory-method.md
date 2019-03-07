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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8cc9544279c6be3efe278c3effda00bc2d387ec
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495358"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="701df-102">Método IMetaDataEmit2::SaveDeltaToMemory</span><span class="sxs-lookup"><span data-stu-id="701df-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="701df-103">Salva as alterações da sessão atual de editar e continuar para a memória.</span><span class="sxs-lookup"><span data-stu-id="701df-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="701df-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="701df-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,   
    [in]  ULONG       cbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="701df-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="701df-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="701df-106">[out] O endereço no qual começar a gravar o delta de metadados.</span><span class="sxs-lookup"><span data-stu-id="701df-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="701df-107">[in] O tamanho das alterações.</span><span class="sxs-lookup"><span data-stu-id="701df-107">[in] The size of the changes.</span></span> <span data-ttu-id="701df-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) para determinar o tamanho.</span><span class="sxs-lookup"><span data-stu-id="701df-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="701df-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="701df-109">Requirements</span></span>  
 <span data-ttu-id="701df-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="701df-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="701df-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="701df-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="701df-112">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="701df-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="701df-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="701df-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="701df-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="701df-114">See also</span></span>
- [<span data-ttu-id="701df-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="701df-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="701df-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="701df-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
