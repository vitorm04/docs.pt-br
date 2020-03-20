---
title: Função GetCORSystemDirectory
ms.date: 03/30/2017
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
ms.openlocfilehash: bdafacfe52d678aacfcd44de1e924bcb88547424
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178201"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="b359b-102">Função GetCORSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="b359b-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="b359b-103">Retorna o diretório de instalação do tempo de execução de linguagem comum (CLR) que é carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="b359b-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="b359b-104">O diretório de instalação é totalmente qualificado, por exemplo, "c:\windows\microsoft.net\framework\v1.0.3705".</span><span class="sxs-lookup"><span data-stu-id="b359b-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="b359b-105">Esta função é preterida.</span><span class="sxs-lookup"><span data-stu-id="b359b-105">This function is deprecated.</span></span> <span data-ttu-id="b359b-106">Ele é substituído pelo método [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) fornecido no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b359b-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) method provided in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b359b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b359b-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (
    [out] LPWSTR  pbuffer,
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="b359b-108">parâmetros</span><span class="sxs-lookup"><span data-stu-id="b359b-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="b359b-109">[fora] Um buffer no qual o tempo de execução retorna uma seqüência que contém o nome totalmente qualificado do diretório de instalação para o tempo de execução que é carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="b359b-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="b359b-110">Se o tempo de execução ainda não tiver sido carregado no processo, a função retorna as informações apropriadas do diretório para a versão mais recente do tempo de execução instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="b359b-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="b359b-111">[em] O tamanho, em bytes, de `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="b359b-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="b359b-112">[fora] O número de caracteres retornou em `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="b359b-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b359b-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="b359b-113">Remarks</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="b359b-114">Não use esta função em processos que estão em execução versão 4 da CLR.</span><span class="sxs-lookup"><span data-stu-id="b359b-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="b359b-115">Se uma versão anterior do CLR estiver instalada no computador, esta função reameda o diretório de instalação dessa versão.</span><span class="sxs-lookup"><span data-stu-id="b359b-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b359b-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b359b-116">Requirements</span></span>  
 <span data-ttu-id="b359b-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b359b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b359b-118">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b359b-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b359b-119">**Biblioteca:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b359b-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b359b-120">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b359b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b359b-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="b359b-121">See also</span></span>

- [<span data-ttu-id="b359b-122">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="b359b-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
