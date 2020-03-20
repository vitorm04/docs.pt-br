---
title: Método IMetaDataEmit::SetHandler
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
ms.openlocfilehash: 375c4b2cece0bdfd763ae383c5412c9e25614baf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177536"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="65746-102">Método IMetaDataEmit::SetHandler</span><span class="sxs-lookup"><span data-stu-id="65746-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="65746-103">Define o método referenciado `IUnknown` pelo ponteiro especificado como um retorno de chamada de notificação para remapeamento de tokens.</span><span class="sxs-lookup"><span data-stu-id="65746-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65746-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65746-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65746-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="65746-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="65746-106">[em] O manipulador para se registrar.</span><span class="sxs-lookup"><span data-stu-id="65746-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65746-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="65746-107">Remarks</span></span>  
 <span data-ttu-id="65746-108">O mecanismo de metadados envia notificação usando `SetHandler`o método fornecido por , para compiladores que não geram registros de forma otimizada e que gostariam de otimizar registros salvos.</span><span class="sxs-lookup"><span data-stu-id="65746-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="65746-109">Se o método de retorno `SetHandler`de chamada não for fornecido através, nenhuma otimização será `IMapToken` realizada no save, exceto quando vários escopos de importação foram mesclados usando na mesclagem para cada escopo.</span><span class="sxs-lookup"><span data-stu-id="65746-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65746-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65746-110">Requirements</span></span>  
 <span data-ttu-id="65746-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65746-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65746-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="65746-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65746-113">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65746-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65746-114">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65746-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65746-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="65746-115">See also</span></span>

- [<span data-ttu-id="65746-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="65746-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="65746-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="65746-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
