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
ms.openlocfilehash: 25364330dafdf858c4b41e9a05731c37e97fbb57
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795439"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="fc4ed-102">Função CreateApplicationContext</span><span class="sxs-lookup"><span data-stu-id="fc4ed-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="fc4ed-103">Essa função dá suporte à infraestrutura de .NET Framework e não se destina a ser usada diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="fc4ed-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc4ed-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc4ed-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc4ed-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fc4ed-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="fc4ed-106">no Um ponteiro para um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="fc4ed-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="fc4ed-107">fora Um ponteiro para um contexto de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fc4ed-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc4ed-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fc4ed-108">Requirements</span></span>  
 <span data-ttu-id="fc4ed-109">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc4ed-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc4ed-110">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="fc4ed-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="fc4ed-111">**Biblioteca** Incluído como um recurso em Fusion. dll</span><span class="sxs-lookup"><span data-stu-id="fc4ed-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="fc4ed-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc4ed-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc4ed-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc4ed-113">See also</span></span>

- [<span data-ttu-id="fc4ed-114">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="fc4ed-114">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="fc4ed-115">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="fc4ed-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="fc4ed-116">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="fc4ed-116">Global Assembly Cache</span></span>](../../app-domains/gac.md)
