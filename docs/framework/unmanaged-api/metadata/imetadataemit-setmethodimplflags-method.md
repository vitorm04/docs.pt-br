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
ms.openlocfilehash: b8755629cca27784609de8166dddf44ed1c82bdc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432539"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="cdebe-102">Método IMetaDataEmit::SetMethodImplFlags</span><span class="sxs-lookup"><span data-stu-id="cdebe-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="cdebe-103">Define ou atualiza a assinatura de metadados da implementação do método herdado que é referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="cdebe-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdebe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cdebe-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodImplFlags (   
    [in]  mdMethodDef   md,   
    [in]  DWORD         dwImplFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdebe-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cdebe-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="cdebe-106">no O token para o método a ser alterado.</span><span class="sxs-lookup"><span data-stu-id="cdebe-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="cdebe-107">no Uma combinação dos valores da enumeração [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) que especifica os recursos de implementação do método.</span><span class="sxs-lookup"><span data-stu-id="cdebe-107">[in] A combination of the values of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdebe-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cdebe-108">Requirements</span></span>  
 <span data-ttu-id="cdebe-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdebe-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdebe-110">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cdebe-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cdebe-111">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cdebe-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cdebe-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdebe-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdebe-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdebe-113">See also</span></span>

- [<span data-ttu-id="cdebe-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="cdebe-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="cdebe-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="cdebe-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
