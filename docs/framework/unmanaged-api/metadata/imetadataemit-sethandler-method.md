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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ada84df2a08b992aa178c2fb63c713b05a8937a2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57503210"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="3f537-102">Método IMetaDataEmit::SetHandler</span><span class="sxs-lookup"><span data-stu-id="3f537-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="3f537-103">Define o método referenciado pelo especificado `IUnknown` ponteiro como um retorno de chamada de notificação para remapeamentos de token.</span><span class="sxs-lookup"><span data-stu-id="3f537-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f537-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3f537-104">Syntax</span></span>  
  
```  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f537-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3f537-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="3f537-106">[in] O manipulador para registrar.</span><span class="sxs-lookup"><span data-stu-id="3f537-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f537-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="3f537-107">Remarks</span></span>  
 <span data-ttu-id="3f537-108">O mecanismo de metadados envia notificação por meio do método que é fornecido pelo `SetHandler`, para compiladores que não geram registros de forma otimizada e que gostaria de otimizar os registros salvos.</span><span class="sxs-lookup"><span data-stu-id="3f537-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="3f537-109">Se o método de retorno de chamada não é fornecido por meio `SetHandler`, sem otimização será executada no salvamento, exceto onde vários importar escopos foram mesclados usando `IMapToken` na mesclagem para cada escopo.</span><span class="sxs-lookup"><span data-stu-id="3f537-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f537-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3f537-110">Requirements</span></span>  
 <span data-ttu-id="3f537-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f537-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f537-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3f537-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f537-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3f537-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f537-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f537-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f537-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f537-115">See also</span></span>
- [<span data-ttu-id="3f537-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="3f537-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3f537-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="3f537-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
