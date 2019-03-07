---
title: Função CreateApplicationContext
ms.date: 03/30/2017
api_name:
- CreateApplicationContext
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateApplicationContext
helpviewer_keywords:
- CreateApplicationContext function [.NET Framework fusion]
ms.assetid: 7bf8a141-b2c0-4058-9885-1cef7dcaa811
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6b5aa78efcc19f1fc50c8e9bfc5105f9afd7d50
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495202"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="69821-102">Função CreateApplicationContext</span><span class="sxs-lookup"><span data-stu-id="69821-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="69821-103">Essa função dá suporte à infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="69821-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69821-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="69821-104">Syntax</span></span>  
  
```  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="69821-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="69821-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="69821-106">[in] Um ponteiro para um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="69821-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="69821-107">[out] Um ponteiro para um contexto de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="69821-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69821-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="69821-108">Requirements</span></span>  
 <span data-ttu-id="69821-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69821-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69821-110">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="69821-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="69821-111">**Biblioteca:** Incluído como um recurso no Fusion</span><span class="sxs-lookup"><span data-stu-id="69821-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="69821-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69821-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69821-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69821-113">See also</span></span>
- [<span data-ttu-id="69821-114">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="69821-114">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [<span data-ttu-id="69821-115">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="69821-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [<span data-ttu-id="69821-116">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="69821-116">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
