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
ms.openlocfilehash: 23d68e8e4bbd87779e3b49f0c40f5a5ab9f5124f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617211"
---
# <a name="getcorversion-function"></a><span data-ttu-id="7272b-102">Função GetCORVersion</span><span class="sxs-lookup"><span data-stu-id="7272b-102">GetCORVersion Function</span></span>
<span data-ttu-id="7272b-103">Retorna o número de versão do Common Language Runtime (CLR) em execução no processo atual.</span><span class="sxs-lookup"><span data-stu-id="7272b-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="7272b-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7272b-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7272b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7272b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="7272b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7272b-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="7272b-107">Um ponteiro para um buffer no qual o CLR retorna uma cadeia de caracteres especificando a versão do tempo de execução que está atualmente carregada no processo.</span><span class="sxs-lookup"><span data-stu-id="7272b-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="7272b-108">A cadeia de caracteres retornada assume a mesma forma que as cadeias passadas para [CorBindToRuntimeEx](corbindtoruntimeex-function.md), por exemplo, "v 1.0.1216".</span><span class="sxs-lookup"><span data-stu-id="7272b-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="7272b-109">Se o tempo de execução ainda não tiver sido carregado no processo, a função retornará as informações de diretório apropriadas para a versão mais recente do tempo de execução instalada no computador.</span><span class="sxs-lookup"><span data-stu-id="7272b-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="7272b-110">O número de caracteres `WCHAR` que podem ser mantidos em `pbuffer` .</span><span class="sxs-lookup"><span data-stu-id="7272b-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="7272b-111">Um ponteiro para o número de caracteres realmente retornados em `pbuffer` .</span><span class="sxs-lookup"><span data-stu-id="7272b-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="7272b-112">Se `pbuffer` for um ponteiro NULL, o tempo de execução retornará E_POINTER.</span><span class="sxs-lookup"><span data-stu-id="7272b-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="7272b-113">Se o número de caracteres for maior que o comprimento de `pbuffer` , o tempo de execução retornará ERROR_INSUFFICIENT_BUFFER.</span><span class="sxs-lookup"><span data-stu-id="7272b-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7272b-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7272b-114">Requirements</span></span>  
 <span data-ttu-id="7272b-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7272b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7272b-116">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7272b-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7272b-117">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7272b-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7272b-118">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7272b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7272b-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="7272b-119">See also</span></span>

- [<span data-ttu-id="7272b-120">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="7272b-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
