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
ms.openlocfilehash: ebd7ef3b329eae8e35b680f3d8c74864e2a0f4d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428681"
---
# <a name="corimageunloading-function"></a><span data-ttu-id="85052-102">Função _CorImageUnloading</span><span class="sxs-lookup"><span data-stu-id="85052-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="85052-103">Notifica o carregador quando as imagens do módulo gerenciado são descarregadas.</span><span class="sxs-lookup"><span data-stu-id="85052-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="85052-104">Essa função não está implementada.</span><span class="sxs-lookup"><span data-stu-id="85052-104">This function is not implemented.</span></span> <span data-ttu-id="85052-105">Se chamado, ele retornará E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="85052-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85052-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="85052-106">Syntax</span></span>  
  
```  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="85052-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="85052-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="85052-108">[in] Um ponteiro para o local inicial da imagem a ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="85052-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85052-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="85052-109">Requirements</span></span>  
 <span data-ttu-id="85052-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85052-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85052-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="85052-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="85052-112">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="85052-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="85052-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85052-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85052-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85052-114">See Also</span></span>  
 [<span data-ttu-id="85052-115">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="85052-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
