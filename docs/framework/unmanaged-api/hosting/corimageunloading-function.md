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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086423"
---
# <a name="corimageunloading-function"></a><span data-ttu-id="9e2e7-102">Função _CorImageUnloading</span><span class="sxs-lookup"><span data-stu-id="9e2e7-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="9e2e7-103">Notifica o carregador quando as imagens de módulo gerenciado são descarregadas.</span><span class="sxs-lookup"><span data-stu-id="9e2e7-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="9e2e7-104">Essa função não está implementada.</span><span class="sxs-lookup"><span data-stu-id="9e2e7-104">This function is not implemented.</span></span> <span data-ttu-id="9e2e7-105">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="9e2e7-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e2e7-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e2e7-106">Syntax</span></span>  
  
```  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e2e7-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9e2e7-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="9e2e7-108">[in] Um ponteiro para o local inicial da imagem a ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="9e2e7-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e2e7-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9e2e7-109">Requirements</span></span>  
 <span data-ttu-id="9e2e7-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e2e7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e2e7-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9e2e7-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9e2e7-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="9e2e7-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="9e2e7-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="9e2e7-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9e2e7-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e2e7-114">See also</span></span>

- [<span data-ttu-id="9e2e7-115">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="9e2e7-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
