---
title: Método ICLRRuntimeInfo::GetRuntimeDirectory
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetRuntimeDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetRuntimeDirectory
helpviewer_keywords:
- GetRuntimeDirectory method [.NET Framework hosting]
- ICLRRuntimeInfo::GetRuntimeDirectory method [.NET Framework hosting]
ms.assetid: 4401546e-4d48-453f-a1fb-b2ebda54df5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2455c896ebdc12f2bb92a30d55745f7bd5bc308a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765525"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="4bdb5-102">Método ICLRRuntimeInfo::GetRuntimeDirectory</span><span class="sxs-lookup"><span data-stu-id="4bdb5-102">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>
<span data-ttu-id="4bdb5-103">Obtém o diretório de instalação do common language runtime (CLR) associado a essa interface.</span><span class="sxs-lookup"><span data-stu-id="4bdb5-103">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="4bdb5-104">Esse método substitui o [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) função fornecido nas versões do .NET Framework 2.0, 3.0 e 3.5.</span><span class="sxs-lookup"><span data-stu-id="4bdb5-104">This method supersedes the [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bdb5-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4bdb5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bdb5-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4bdb5-106">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="4bdb5-107">[out] Retorna o diretório de instalação do CLR.</span><span class="sxs-lookup"><span data-stu-id="4bdb5-107">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="4bdb5-108">O caminho de instalação é totalmente qualificado; Por exemplo, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span><span class="sxs-lookup"><span data-stu-id="4bdb5-108">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="4bdb5-109">[no, out] Especifica o tamanho do `pwzBuffer` para evitar estouros de buffer.</span><span class="sxs-lookup"><span data-stu-id="4bdb5-109">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="4bdb5-110">Se `pwzBuffer` for nulo, `pchBuffer` retorna o tamanho necessário da `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="4bdb5-110">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4bdb5-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4bdb5-111">Return Value</span></span>  
 <span data-ttu-id="4bdb5-112">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="4bdb5-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4bdb5-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4bdb5-113">HRESULT</span></span>|<span data-ttu-id="4bdb5-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="4bdb5-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4bdb5-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="4bdb5-115">S_OK</span></span>|<span data-ttu-id="4bdb5-116">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="4bdb5-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="4bdb5-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="4bdb5-117">E_POINTER</span></span>|<span data-ttu-id="4bdb5-118">`pwzBuffer` ou `pchBuffer` é nulo.</span><span class="sxs-lookup"><span data-stu-id="4bdb5-118">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bdb5-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="4bdb5-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bdb5-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4bdb5-120">Requirements</span></span>  
 <span data-ttu-id="4bdb5-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bdb5-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bdb5-122">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="4bdb5-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4bdb5-123">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="4bdb5-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4bdb5-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bdb5-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bdb5-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4bdb5-125">See also</span></span>

- [<span data-ttu-id="4bdb5-126">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="4bdb5-126">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="4bdb5-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="4bdb5-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
