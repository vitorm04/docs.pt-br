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
ms.openlocfilehash: a02456393680169ce33369ee5914f6c5216081c6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009209"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="b6318-102">Método IMetaDataEmit::SetMethodImplFlags</span><span class="sxs-lookup"><span data-stu-id="b6318-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="b6318-103">Define ou atualiza a assinatura de metadados da implementação do método herdado que é referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="b6318-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6318-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6318-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodImplFlags (
    [in]  mdMethodDef   md,
    [in]  DWORD         dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6318-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b6318-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="b6318-106">no O token para o método a ser alterado.</span><span class="sxs-lookup"><span data-stu-id="b6318-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="b6318-107">no Uma combinação dos valores da enumeração [CorMethodImpl](cormethodimpl-enumeration.md) que especifica os recursos de implementação do método.</span><span class="sxs-lookup"><span data-stu-id="b6318-107">[in] A combination of the values of the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6318-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b6318-108">Requirements</span></span>  
 <span data-ttu-id="b6318-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6318-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6318-110">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b6318-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6318-111">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b6318-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6318-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6318-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6318-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="b6318-113">See also</span></span>

- [<span data-ttu-id="b6318-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="b6318-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="b6318-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="b6318-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
