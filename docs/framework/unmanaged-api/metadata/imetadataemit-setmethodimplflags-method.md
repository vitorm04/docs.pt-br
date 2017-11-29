---
title: "Método IMetaDataEmit::SetMethodImplFlags"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetMethodImplFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetMethodImplFlags
helpviewer_keywords:
- IMetaDataEmit::SetMethodImplFlags method [.NET Framework metadata]
- SetMethodImpFlags method [.NET Framework metadata]
ms.assetid: 4bc82d9b-9544-4be3-ba51-a2d4d806158a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d69940d5cffe397d009b7364a20a09dbbd95db4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="78245-102">Método IMetaDataEmit::SetMethodImplFlags</span><span class="sxs-lookup"><span data-stu-id="78245-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="78245-103">Define ou atualiza a assinatura de metadados da implementação do método herdado que é referenciada por token especificado.</span><span class="sxs-lookup"><span data-stu-id="78245-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78245-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="78245-104">Syntax</span></span>  
  
```  
HRESULT SetMethodImplFlags (   
    [in]  mdMethodDef   md,   
    [in]  DWORD         dwImplFlags   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78245-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="78245-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="78245-106">[in] O token para o método a ser alterado.</span><span class="sxs-lookup"><span data-stu-id="78245-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="78245-107">[in] Uma combinação dos valores da [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeração que especifica os recursos de implementação de método.</span><span class="sxs-lookup"><span data-stu-id="78245-107">[in] A combination of the values of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78245-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="78245-108">Requirements</span></span>  
 <span data-ttu-id="78245-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78245-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78245-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="78245-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="78245-111">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="78245-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78245-112">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78245-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78245-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78245-113">See Also</span></span>  
 [<span data-ttu-id="78245-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="78245-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="78245-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="78245-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
