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
ms.openlocfilehash: 6737275fb77e6f177832eb1d96214c37942bcd22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442162"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="64cf9-102">Método IMetaDataEmit::SetHandler</span><span class="sxs-lookup"><span data-stu-id="64cf9-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="64cf9-103">Define o método referenciado pelo ponteiro de `IUnknown` especificado como um retorno de chamada de notificação para remapeamentos de token.</span><span class="sxs-lookup"><span data-stu-id="64cf9-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64cf9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64cf9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64cf9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="64cf9-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="64cf9-106">no O manipulador a ser registrado.</span><span class="sxs-lookup"><span data-stu-id="64cf9-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64cf9-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="64cf9-107">Remarks</span></span>  
 <span data-ttu-id="64cf9-108">O mecanismo de metadados envia a notificação usando o método fornecido pelo `SetHandler`, para compiladores que não geram registros de maneira otimizada e que gostaria de otimizar os registros salvos.</span><span class="sxs-lookup"><span data-stu-id="64cf9-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="64cf9-109">Se o método de retorno de chamada não for fornecido por meio de `SetHandler`, nenhuma otimização será executada no salvamento, exceto onde vários escopos de importação tiverem sido mesclados usando `IMapToken` na mesclagem para cada escopo.</span><span class="sxs-lookup"><span data-stu-id="64cf9-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64cf9-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="64cf9-110">Requirements</span></span>  
 <span data-ttu-id="64cf9-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64cf9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64cf9-112">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="64cf9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="64cf9-113">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="64cf9-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64cf9-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64cf9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64cf9-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64cf9-115">See also</span></span>

- [<span data-ttu-id="64cf9-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="64cf9-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="64cf9-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="64cf9-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
