---
title: "Função CreateApplicationContext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateApplicationContext
api_location: fusion.dll
api_type: DLLExport
f1_keywords: CreateApplicationContext
helpviewer_keywords: CreateApplicationContext function [.NET Framework fusion]
ms.assetid: 7bf8a141-b2c0-4058-9885-1cef7dcaa811
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c089c32d4bc8474168274186a9303d39976abfca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="11358-102">Função CreateApplicationContext</span><span class="sxs-lookup"><span data-stu-id="11358-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="11358-103">Essa função dá suporte à infraestrutura .NET Framework e não se destina a ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="11358-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11358-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11358-104">Syntax</span></span>  
  
```  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="11358-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="11358-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="11358-106">[in] Um ponteiro para um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="11358-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="11358-107">[out] Um ponteiro para um contexto de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11358-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11358-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11358-108">Requirements</span></span>  
 <span data-ttu-id="11358-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11358-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11358-110">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="11358-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="11358-111">**Biblioteca:** incluído como um recurso no Fusion</span><span class="sxs-lookup"><span data-stu-id="11358-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="11358-112">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11358-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11358-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11358-113">See Also</span></span>  
 [<span data-ttu-id="11358-114">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="11358-114">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [<span data-ttu-id="11358-115">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="11358-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [<span data-ttu-id="11358-116">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="11358-116">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
