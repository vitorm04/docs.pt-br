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
ms.openlocfilehash: 1f40f27651d2d75cf2c3e4d7d1c21e1f47d402af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178184"
---
# <a name="getcorversion-function"></a><span data-ttu-id="cb771-102">Função GetCORVersion</span><span class="sxs-lookup"><span data-stu-id="cb771-102">GetCORVersion Function</span></span>
<span data-ttu-id="cb771-103">Retorna o número da versão do tempo de execução do idioma comum (CLR) que está sendo executado no processo atual.</span><span class="sxs-lookup"><span data-stu-id="cb771-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="cb771-104">Esta função foi depreciada no Quadro .NET 4.</span><span class="sxs-lookup"><span data-stu-id="cb771-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb771-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb771-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="cb771-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="cb771-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="cb771-107">Um ponteiro para um buffer no qual o CLR retorna uma seqüência especificando a versão do tempo de execução que está atualmente carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="cb771-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="cb771-108">A seqüência retornada toma a mesma forma que as strings passadas para [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), por exemplo, "v1.0.1216".</span><span class="sxs-lookup"><span data-stu-id="cb771-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="cb771-109">Se o tempo de execução ainda não tiver sido carregado no processo, a função retorna as informações apropriadas do diretório para a versão mais recente do tempo de execução instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="cb771-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="cb771-110">O número de`WCHAR`caracteres (s) `pbuffer`que podem ser mantidos em .</span><span class="sxs-lookup"><span data-stu-id="cb771-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="cb771-111">Um ponteiro para o número de `pbuffer`caracteres realmente retornado em .</span><span class="sxs-lookup"><span data-stu-id="cb771-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="cb771-112">Se `pbuffer` for um ponteiro nulo, o tempo de execução retorna E_POINTER.</span><span class="sxs-lookup"><span data-stu-id="cb771-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="cb771-113">Se o número de caracteres `pbuffer` for maior, então o comprimento de , o tempo de execução retorna ERROR_INSUFFICIENT_BUFFER.</span><span class="sxs-lookup"><span data-stu-id="cb771-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb771-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cb771-114">Requirements</span></span>  
 <span data-ttu-id="cb771-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb771-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb771-116">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cb771-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb771-117">**Biblioteca:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="cb771-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb771-118">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb771-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb771-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="cb771-119">See also</span></span>

- [<span data-ttu-id="cb771-120">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="cb771-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
