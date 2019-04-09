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
ms.openlocfilehash: 567e6533a9a9ac718f8b5acac769295c104f7f3c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144320"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="fbeda-102">Função GetCORSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="fbeda-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="fbeda-103">Retorna o diretório de instalação do common language runtime (CLR) que é carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="fbeda-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="fbeda-104">O diretório de instalação é totalmente qualificado, por exemplo, "c:\windows\microsoft.net\framework\v1.0.3705".</span><span class="sxs-lookup"><span data-stu-id="fbeda-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="fbeda-105">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="fbeda-105">This function is deprecated.</span></span> <span data-ttu-id="fbeda-106">Ele é substituído pelo [iclrruntimeinfo:: Getruntimedirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) método fornecido no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fbeda-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) method provided in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbeda-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fbeda-107">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="fbeda-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fbeda-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="fbeda-109">[out] Um buffer no qual o tempo de execução retorna uma cadeia de caracteres que contém o nome totalmente qualificado do diretório de instalação para o tempo de execução é carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="fbeda-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="fbeda-110">Se o tempo de execução ainda não tiver sido carregado no processo, a função retorna as informações de diretório apropriado para a versão mais recente do tempo de execução instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="fbeda-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="fbeda-111">[in] O tamanho, em bytes, do `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="fbeda-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="fbeda-112">[out] O número de caracteres retornados na `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="fbeda-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbeda-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="fbeda-113">Remarks</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="fbeda-114">Não use essa função em processos que estão executando a versão 4 do CLR.</span><span class="sxs-lookup"><span data-stu-id="fbeda-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="fbeda-115">Se uma versão anterior do CLR está instalada no computador, essa função retorna o diretório de instalação para essa versão.</span><span class="sxs-lookup"><span data-stu-id="fbeda-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbeda-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fbeda-116">Requirements</span></span>  
 <span data-ttu-id="fbeda-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbeda-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbeda-118">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fbeda-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fbeda-119">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fbeda-119">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="fbeda-120">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="fbeda-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fbeda-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbeda-121">See also</span></span>

- [<span data-ttu-id="fbeda-122">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="fbeda-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
