---
title: Método IMetaDataEmit::SetMethodProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodProps
helpviewer_keywords:
- SetMethodProps method [.NET Framework metadata]
- IMetaDataEmit::SetMethodProps method [.NET Framework metadata]
ms.assetid: e0c6ac12-22ea-43f5-b799-8cda0faf3336
topic_type:
- apiref
ms.openlocfilehash: 9662a14b4ea97aed16968083489324d46c38dda2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177518"
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="d0276-102">Método IMetaDataEmit::SetMethodProps</span><span class="sxs-lookup"><span data-stu-id="d0276-102">IMetaDataEmit::SetMethodProps Method</span></span>
<span data-ttu-id="d0276-103">Define ou atualiza o recurso, armazenado no endereço virtual relativo especificado, de um método definido por uma chamada anterior ao [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="d0276-103">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0276-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0276-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodProps (
    [in]  mdMethodDef md,
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,
    [in]  DWORD       dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0276-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="d0276-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="d0276-106">[em] O token para que o método seja alterado.</span><span class="sxs-lookup"><span data-stu-id="d0276-106">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="d0276-107">[em] Os atributos do membro.</span><span class="sxs-lookup"><span data-stu-id="d0276-107">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="d0276-108">[em] O endereço do código.</span><span class="sxs-lookup"><span data-stu-id="d0276-108">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="d0276-109">[em] As bandeiras de implementação para o método.</span><span class="sxs-lookup"><span data-stu-id="d0276-109">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0276-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d0276-110">Requirements</span></span>  
 <span data-ttu-id="d0276-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0276-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0276-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d0276-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d0276-113">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d0276-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d0276-114">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0276-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0276-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="d0276-115">See also</span></span>

- [<span data-ttu-id="d0276-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="d0276-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d0276-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="d0276-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
