---
title: Função _CorImageUnloading
ms.date: 03/30/2017
api_name:
- _CorImageUnloading
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorImageUnloading
helpviewer_keywords:
- _CorImageUnloading function [.NET Framework hosting]
ms.assetid: b4367214-6dac-4280-aa11-fd487ff30bc4
topic_type:
- apiref
ms.openlocfilehash: 4932e1fd6294f4a01264e982835dd0707324082a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178229"
---
# <a name="_corimageunloading-function"></a><span data-ttu-id="ba53a-102">Função _CorImageUnloading</span><span class="sxs-lookup"><span data-stu-id="ba53a-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="ba53a-103">Notifica o carregador quando as imagens do módulo gerenciado são descarregadas.</span><span class="sxs-lookup"><span data-stu-id="ba53a-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="ba53a-104">Esta função não é implementada.</span><span class="sxs-lookup"><span data-stu-id="ba53a-104">This function is not implemented.</span></span> <span data-ttu-id="ba53a-105">Se for chamado, ele retorna E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="ba53a-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba53a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ba53a-106">Syntax</span></span>  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba53a-107">parâmetros</span><span class="sxs-lookup"><span data-stu-id="ba53a-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="ba53a-108">[em] Um ponteiro para o local de partida da imagem para descarregar.</span><span class="sxs-lookup"><span data-stu-id="ba53a-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba53a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ba53a-109">Requirements</span></span>  
 <span data-ttu-id="ba53a-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba53a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba53a-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ba53a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ba53a-112">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ba53a-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ba53a-113">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba53a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba53a-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="ba53a-114">See also</span></span>

- [<span data-ttu-id="ba53a-115">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="ba53a-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
