---
title: Função GetCORRequiredVersion
ms.date: 03/30/2017
api_name:
- GetCORRequiredVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetCORRequiredVersion
helpviewer_keywords:
- GetCORRequiredVersion function [.NET Framework hosting]
ms.assetid: 1588fe7b-c378-4f4b-9c4b-48647f1119cc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5786444c36fcfc9547be1db0006757b0a9376c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175182"
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="b4d9b-102">Função GetCORRequiredVersion</span><span class="sxs-lookup"><span data-stu-id="b4d9b-102">GetCORRequiredVersion Function</span></span>
<span data-ttu-id="b4d9b-103">Obtém o número de versão do common language runtime (CLR) necessária.</span><span class="sxs-lookup"><span data-stu-id="b4d9b-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="b4d9b-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b4d9b-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4d9b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4d9b-105">Syntax</span></span>  
  
```  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4d9b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b4d9b-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="b4d9b-107">[out] Um buffer que contém uma cadeia de caracteres que especifica o número de versão.</span><span class="sxs-lookup"><span data-stu-id="b4d9b-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="b4d9b-108">[in] O tamanho, em bytes, do buffer.</span><span class="sxs-lookup"><span data-stu-id="b4d9b-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="b4d9b-109">[out] O número de bytes retornados no buffer.</span><span class="sxs-lookup"><span data-stu-id="b4d9b-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4d9b-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b4d9b-110">Requirements</span></span>  
 <span data-ttu-id="b4d9b-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4d9b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4d9b-112">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b4d9b-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b4d9b-113">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b4d9b-113">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b4d9b-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="b4d9b-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b4d9b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4d9b-115">See also</span></span>

- [<span data-ttu-id="b4d9b-116">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="b4d9b-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
