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
ms.openlocfilehash: 30e3a88140c8a438001e8428df4c5ee879c83376
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136916"
---
# <a name="_corimageunloading-function"></a><span data-ttu-id="a1d9b-102">Função _CorImageUnloading</span><span class="sxs-lookup"><span data-stu-id="a1d9b-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="a1d9b-103">Notifica o carregador quando as imagens do módulo gerenciado são descarregadas.</span><span class="sxs-lookup"><span data-stu-id="a1d9b-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="a1d9b-104">Esta função não está implementada.</span><span class="sxs-lookup"><span data-stu-id="a1d9b-104">This function is not implemented.</span></span> <span data-ttu-id="a1d9b-105">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="a1d9b-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1d9b-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1d9b-106">Syntax</span></span>  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1d9b-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a1d9b-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="a1d9b-108">no Um ponteiro para o local inicial da imagem a ser descarregada.</span><span class="sxs-lookup"><span data-stu-id="a1d9b-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1d9b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a1d9b-109">Requirements</span></span>  
 <span data-ttu-id="a1d9b-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1d9b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1d9b-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a1d9b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a1d9b-112">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a1d9b-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a1d9b-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1d9b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1d9b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1d9b-114">See also</span></span>

- [<span data-ttu-id="a1d9b-115">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="a1d9b-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
