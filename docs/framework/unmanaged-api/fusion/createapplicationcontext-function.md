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
ms.openlocfilehash: 80012d030d0ea51ab3d150a7fd346b78e29dbde5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430094"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="62f05-102">Função CreateApplicationContext</span><span class="sxs-lookup"><span data-stu-id="62f05-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="62f05-103">Essa função dá suporte à infraestrutura .NET Framework e não se destina a ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="62f05-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62f05-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="62f05-104">Syntax</span></span>  
  
```  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62f05-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="62f05-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="62f05-106">[in] Um ponteiro para um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="62f05-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="62f05-107">[out] Um ponteiro para um contexto de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="62f05-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62f05-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="62f05-108">Requirements</span></span>  
 <span data-ttu-id="62f05-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62f05-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62f05-110">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="62f05-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="62f05-111">**Biblioteca:** incluído como um recurso no Fusion</span><span class="sxs-lookup"><span data-stu-id="62f05-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="62f05-112">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62f05-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f05-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62f05-113">See Also</span></span>  
 [<span data-ttu-id="62f05-114">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="62f05-114">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [<span data-ttu-id="62f05-115">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="62f05-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [<span data-ttu-id="62f05-116">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="62f05-116">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
