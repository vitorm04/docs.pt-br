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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992453"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="a2054-102">Método IMetaDataEmit::SetMethodImplFlags</span><span class="sxs-lookup"><span data-stu-id="a2054-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="a2054-103">Define ou atualiza a assinatura de metadados da implementação do método herdado que é referenciada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="a2054-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2054-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a2054-104">Syntax</span></span>  
  
```  
HRESULT SetMethodImplFlags (   
    [in]  mdMethodDef   md,   
    [in]  DWORD         dwImplFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2054-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a2054-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="a2054-106">[in] O token para o método a ser alterado.</span><span class="sxs-lookup"><span data-stu-id="a2054-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="a2054-107">[in] Uma combinação dos valores da [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeração que especifica os recursos de implementação do método.</span><span class="sxs-lookup"><span data-stu-id="a2054-107">[in] A combination of the values of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2054-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a2054-108">Requirements</span></span>  
 <span data-ttu-id="a2054-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2054-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2054-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a2054-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a2054-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a2054-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2054-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2054-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2054-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2054-113">See also</span></span>

- [<span data-ttu-id="a2054-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="a2054-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a2054-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="a2054-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
