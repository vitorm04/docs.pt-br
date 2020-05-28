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
ms.openlocfilehash: 4fa227d18b8cb10936d93fda9bcaf413ce63ca3b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003926"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="093b8-102">Método IMetaDataEmit::SetHandler</span><span class="sxs-lookup"><span data-stu-id="093b8-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="093b8-103">Define o método referenciado pelo `IUnknown` ponteiro especificado como um retorno de chamada de notificação para remapeamentos de token.</span><span class="sxs-lookup"><span data-stu-id="093b8-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="093b8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="093b8-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="093b8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="093b8-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="093b8-106">no O manipulador a ser registrado.</span><span class="sxs-lookup"><span data-stu-id="093b8-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="093b8-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="093b8-107">Remarks</span></span>  
 <span data-ttu-id="093b8-108">O mecanismo de metadados envia a notificação usando o método fornecido pelo `SetHandler` , para compiladores que não geram registros de forma otimizada e que gostaria de otimizar os registros salvos.</span><span class="sxs-lookup"><span data-stu-id="093b8-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="093b8-109">Se o método de retorno de chamada não for fornecido por meio `SetHandler` do, nenhuma otimização será executada no salvamento, exceto onde vários escopos de importação tiverem sido mesclados usando `IMapToken` na mesclagem para cada escopo.</span><span class="sxs-lookup"><span data-stu-id="093b8-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="093b8-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="093b8-110">Requirements</span></span>  
 <span data-ttu-id="093b8-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="093b8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="093b8-112">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="093b8-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="093b8-113">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="093b8-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="093b8-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="093b8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="093b8-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="093b8-115">See also</span></span>

- [<span data-ttu-id="093b8-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="093b8-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="093b8-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="093b8-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
