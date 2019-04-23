---
title: Método IMetaDataEmit::SetMethodImplFlags
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodImplFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodImplFlags
helpviewer_keywords:
- IMetaDataEmit::SetMethodImplFlags method [.NET Framework metadata]
- SetMethodImpFlags method [.NET Framework metadata]
ms.assetid: 4bc82d9b-9544-4be3-ba51-a2d4d806158a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 28c0aa37bdcae2a09a4d53f920efd3ffe7117bd3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145165"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="4bb71-102">Método IMetaDataEmit::SetMethodImplFlags</span><span class="sxs-lookup"><span data-stu-id="4bb71-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="4bb71-103">Define ou atualiza a assinatura de metadados da implementação do método herdado que é referenciada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="4bb71-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bb71-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4bb71-104">Syntax</span></span>  
  
```  
HRESULT SetMethodImplFlags (   
    [in]  mdMethodDef   md,   
    [in]  DWORD         dwImplFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bb71-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4bb71-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="4bb71-106">[in] O token para o método a ser alterado.</span><span class="sxs-lookup"><span data-stu-id="4bb71-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="4bb71-107">[in] Uma combinação dos valores da [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeração que especifica os recursos de implementação do método.</span><span class="sxs-lookup"><span data-stu-id="4bb71-107">[in] A combination of the values of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bb71-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4bb71-108">Requirements</span></span>  
 <span data-ttu-id="4bb71-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bb71-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bb71-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4bb71-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4bb71-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="4bb71-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4bb71-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bb71-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bb71-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4bb71-113">See also</span></span>

- [<span data-ttu-id="4bb71-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="4bb71-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4bb71-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="4bb71-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
