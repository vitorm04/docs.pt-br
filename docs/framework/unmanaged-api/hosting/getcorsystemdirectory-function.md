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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d30384ea8b9ff4eee41abd43ae39486f770039e7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041422"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="aaa9c-102">Função GetCORSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="aaa9c-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="aaa9c-103">Retorna o diretório de instalação do Common Language Runtime (CLR) que é carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="aaa9c-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="aaa9c-104">O diretório de instalação é totalmente qualificado, por exemplo, "c:\Windows\Microsoft.NET\Framework\v1.0.3705".</span><span class="sxs-lookup"><span data-stu-id="aaa9c-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="aaa9c-105">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="aaa9c-105">This function is deprecated.</span></span> <span data-ttu-id="aaa9c-106">Ele é substituído pelo método [ICLRRuntimeInfo:: GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) fornecido no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="aaa9c-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) method provided in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaa9c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aaa9c-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="aaa9c-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aaa9c-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="aaa9c-109">fora Um buffer no qual o tempo de execução retorna uma cadeia de caracteres que contém o nome totalmente qualificado do diretório de instalação para o tempo de execução que é carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="aaa9c-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="aaa9c-110">Se o tempo de execução ainda não tiver sido carregado no processo, a função retornará as informações de diretório apropriadas para a versão mais recente do tempo de execução instalada no computador.</span><span class="sxs-lookup"><span data-stu-id="aaa9c-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="aaa9c-111">no O tamanho, em bytes, de `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="aaa9c-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="aaa9c-112">fora O número de caracteres retornados em `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="aaa9c-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aaa9c-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="aaa9c-113">Remarks</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="aaa9c-114">Não use essa função em processos que estejam executando a versão 4 do CLR.</span><span class="sxs-lookup"><span data-stu-id="aaa9c-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="aaa9c-115">Se uma versão anterior do CLR estiver instalada no computador, essa função retornará o diretório de instalação para essa versão.</span><span class="sxs-lookup"><span data-stu-id="aaa9c-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaa9c-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aaa9c-116">Requirements</span></span>  
 <span data-ttu-id="aaa9c-117">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aaa9c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaa9c-118">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aaa9c-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aaa9c-119">**Biblioteca** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aaa9c-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aaa9c-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaa9c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaa9c-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aaa9c-121">See also</span></span>

- [<span data-ttu-id="aaa9c-122">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="aaa9c-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
