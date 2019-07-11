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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b488b6a887b0c66d8c17f8ea78f48f7d2ea31011
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758401"
---
# <a name="corimageunloading-function"></a><span data-ttu-id="7e0de-102">Função _CorImageUnloading</span><span class="sxs-lookup"><span data-stu-id="7e0de-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="7e0de-103">Notifica o carregador quando as imagens de módulo gerenciado são descarregadas.</span><span class="sxs-lookup"><span data-stu-id="7e0de-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="7e0de-104">Essa função não está implementada.</span><span class="sxs-lookup"><span data-stu-id="7e0de-104">This function is not implemented.</span></span> <span data-ttu-id="7e0de-105">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="7e0de-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e0de-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e0de-106">Syntax</span></span>  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e0de-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7e0de-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="7e0de-108">[in] Um ponteiro para o local inicial da imagem a ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="7e0de-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e0de-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7e0de-109">Requirements</span></span>  
 <span data-ttu-id="7e0de-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e0de-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e0de-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7e0de-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7e0de-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="7e0de-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7e0de-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e0de-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e0de-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e0de-114">See also</span></span>

- [<span data-ttu-id="7e0de-115">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="7e0de-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
