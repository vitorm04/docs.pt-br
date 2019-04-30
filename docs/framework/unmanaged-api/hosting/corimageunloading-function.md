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
ms.openlocfilehash: 1cb5f9decbcdfb71f67a5132dc59773f1de8b0a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985797"
---
# <a name="corimageunloading-function"></a><span data-ttu-id="a0d17-102">Função _CorImageUnloading</span><span class="sxs-lookup"><span data-stu-id="a0d17-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="a0d17-103">Notifica o carregador quando as imagens de módulo gerenciado são descarregadas.</span><span class="sxs-lookup"><span data-stu-id="a0d17-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="a0d17-104">Essa função não está implementada.</span><span class="sxs-lookup"><span data-stu-id="a0d17-104">This function is not implemented.</span></span> <span data-ttu-id="a0d17-105">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="a0d17-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0d17-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a0d17-106">Syntax</span></span>  
  
```  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0d17-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a0d17-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="a0d17-108">[in] Um ponteiro para o local inicial da imagem a ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="a0d17-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0d17-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a0d17-109">Requirements</span></span>  
 <span data-ttu-id="a0d17-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0d17-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0d17-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a0d17-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a0d17-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a0d17-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a0d17-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0d17-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0d17-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0d17-114">See also</span></span>

- [<span data-ttu-id="a0d17-115">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="a0d17-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
