---
title: Função CreateAssemblyCache
ms.date: 03/30/2017
api_name:
- CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyCache
helpviewer_keywords:
- CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf78ded62f11b336d9f5fe0f3a205275ae37189b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157398"
---
# <a name="createassemblycache-function"></a><span data-ttu-id="4e5cc-102">Função CreateAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="4e5cc-102">CreateAssemblyCache Function</span></span>
<span data-ttu-id="4e5cc-103">Obtém um ponteiro para um novo [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instância que representa o cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="4e5cc-103">Gets a pointer to a new [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e5cc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4e5cc-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e5cc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4e5cc-105">Parameters</span></span>  
 `ppAsmCache`  
 <span data-ttu-id="4e5cc-106">[out] Retornado `IAssemblyCache` ponteiro.</span><span class="sxs-lookup"><span data-stu-id="4e5cc-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="4e5cc-107">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="4e5cc-107">[in] Reserved for future extensibility.</span></span> `dwReserved` <span data-ttu-id="4e5cc-108">deve ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="4e5cc-108">must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e5cc-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4e5cc-109">Requirements</span></span>  
 <span data-ttu-id="4e5cc-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e5cc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e5cc-111">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="4e5cc-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4e5cc-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="4e5cc-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="4e5cc-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="4e5cc-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4e5cc-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4e5cc-114">See also</span></span>

- [<span data-ttu-id="4e5cc-115">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="4e5cc-115">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [<span data-ttu-id="4e5cc-116">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="4e5cc-116">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [<span data-ttu-id="4e5cc-117">Cache de assemblies global</span><span class="sxs-lookup"><span data-stu-id="4e5cc-117">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
