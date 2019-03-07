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
ms.openlocfilehash: 9afe4afcaefb9409edb93bd1da96a02db20dbd20
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466703"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="624bd-102">Função GetCORSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="624bd-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="624bd-103">Retorna o diretório de instalação do common language runtime (CLR) que é carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="624bd-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="624bd-104">O diretório de instalação é totalmente qualificado, por exemplo, "c:\windows\microsoft.net\framework\v1.0.3705".</span><span class="sxs-lookup"><span data-stu-id="624bd-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="624bd-105">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="624bd-105">This function is deprecated.</span></span> <span data-ttu-id="624bd-106">Ele é substituído pelo [iclrruntimeinfo:: Getruntimedirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) método fornecido no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="624bd-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) method provided in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="624bd-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="624bd-107">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="624bd-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="624bd-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="624bd-109">[out] Um buffer no qual o tempo de execução retorna uma cadeia de caracteres que contém o nome totalmente qualificado do diretório de instalação para o tempo de execução é carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="624bd-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="624bd-110">Se o tempo de execução ainda não tiver sido carregado no processo, a função retorna as informações de diretório apropriado para a versão mais recente do tempo de execução instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="624bd-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="624bd-111">[in] O tamanho, em bytes, do `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="624bd-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="624bd-112">[out] O número de caracteres retornados na `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="624bd-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="624bd-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="624bd-113">Remarks</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="624bd-114">Não use essa função em processos que estão executando a versão 4 do CLR.</span><span class="sxs-lookup"><span data-stu-id="624bd-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="624bd-115">Se uma versão anterior do CLR está instalada no computador, essa função retorna o diretório de instalação para essa versão.</span><span class="sxs-lookup"><span data-stu-id="624bd-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="624bd-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="624bd-116">Requirements</span></span>  
 <span data-ttu-id="624bd-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="624bd-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="624bd-118">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="624bd-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="624bd-119">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="624bd-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="624bd-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="624bd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="624bd-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="624bd-121">See also</span></span>
- [<span data-ttu-id="624bd-122">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="624bd-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
