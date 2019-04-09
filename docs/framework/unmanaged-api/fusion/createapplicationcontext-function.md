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
ms.openlocfilehash: d98829b29100824e5d606e23aaf287c9f6e81d69
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170957"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="8a3b3-102">Função CreateApplicationContext</span><span class="sxs-lookup"><span data-stu-id="8a3b3-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="8a3b3-103">Essa função dá suporte à infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="8a3b3-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a3b3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a3b3-104">Syntax</span></span>  
  
```  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a3b3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8a3b3-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="8a3b3-106">[in] Um ponteiro para um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="8a3b3-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="8a3b3-107">[out] Um ponteiro para um contexto de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8a3b3-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a3b3-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8a3b3-108">Requirements</span></span>  
 <span data-ttu-id="8a3b3-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a3b3-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a3b3-110">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="8a3b3-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8a3b3-111">**Biblioteca:** Incluído como um recurso no Fusion</span><span class="sxs-lookup"><span data-stu-id="8a3b3-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 **<span data-ttu-id="8a3b3-112">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="8a3b3-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8a3b3-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a3b3-113">See also</span></span>

- [<span data-ttu-id="8a3b3-114">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="8a3b3-114">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [<span data-ttu-id="8a3b3-115">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="8a3b3-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [<span data-ttu-id="8a3b3-116">Cache de assemblies global</span><span class="sxs-lookup"><span data-stu-id="8a3b3-116">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
