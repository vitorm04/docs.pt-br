---
title: Função GetCORVersion
ms.date: 03/30/2017
api_name:
- GetCORVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORVersion
helpviewer_keywords:
- GetCORVersion function [.NET Framework hosting]
ms.assetid: 2f09cd37-bf3a-4cc5-87b0-adc42a7eed31
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f66e00c3334aecdf8c653f57e28d1b327c4170e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61627996"
---
# <a name="getcorversion-function"></a><span data-ttu-id="87103-102">Função GetCORVersion</span><span class="sxs-lookup"><span data-stu-id="87103-102">GetCORVersion Function</span></span>
<span data-ttu-id="87103-103">Retorna o número de versão do common language runtime (CLR) que está em execução no processo atual.</span><span class="sxs-lookup"><span data-stu-id="87103-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="87103-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="87103-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87103-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87103-105">Syntax</span></span>  
  
```  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="87103-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="87103-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="87103-107">Um ponteiro para um buffer no qual o CLR retorna uma cadeia de caracteres que especifica a versão do tempo de execução que atualmente é carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="87103-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="87103-108">A cadeia de caracteres retornada usa a mesma forma como cadeias de caracteres passados para [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), por exemplo, "v1.0.1216".</span><span class="sxs-lookup"><span data-stu-id="87103-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="87103-109">Se o tempo de execução ainda não tiver sido carregado no processo, a função retorna as informações de diretório apropriado para a versão mais recente do tempo de execução instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="87103-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="87103-110">O número de caracteres (`WCHAR`s) que podem ser mantidos em `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="87103-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="87103-111">Um ponteiro para o número de caracteres retornado de fato no `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="87103-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="87103-112">Se `pbuffer` for um ponteiro nulo, o tempo de execução retorna E_POINTER.</span><span class="sxs-lookup"><span data-stu-id="87103-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="87103-113">Se o número de caracteres for maior, em seguida, o comprimento de `pbuffer` , o tempo de execução retorna ERROR_INSUFFICIENT_BUFFER.</span><span class="sxs-lookup"><span data-stu-id="87103-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87103-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="87103-114">Requirements</span></span>  
 <span data-ttu-id="87103-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87103-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87103-116">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="87103-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="87103-117">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="87103-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87103-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87103-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87103-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87103-119">See also</span></span>

- [<span data-ttu-id="87103-120">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="87103-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
