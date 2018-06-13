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
ms.openlocfilehash: 637ff0fca74dc123a3f7a47dcc3fdeded8d884ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430041"
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="3ccb4-102">Função GetCORRequiredVersion</span><span class="sxs-lookup"><span data-stu-id="3ccb4-102">GetCORRequiredVersion Function</span></span>
<span data-ttu-id="3ccb4-103">Obtém o número de versão do common language runtime (CLR) necessário.</span><span class="sxs-lookup"><span data-stu-id="3ccb4-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="3ccb4-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3ccb4-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ccb4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ccb4-105">Syntax</span></span>  
  
```  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3ccb4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3ccb4-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="3ccb4-107">[out] Um buffer que contém uma cadeia de caracteres que especifica o número de versão.</span><span class="sxs-lookup"><span data-stu-id="3ccb4-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="3ccb4-108">[in] O tamanho, em bytes, do buffer.</span><span class="sxs-lookup"><span data-stu-id="3ccb4-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="3ccb4-109">[out] O número de bytes retornados no buffer.</span><span class="sxs-lookup"><span data-stu-id="3ccb4-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ccb4-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3ccb4-110">Requirements</span></span>  
 <span data-ttu-id="3ccb4-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ccb4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ccb4-112">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3ccb4-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3ccb4-113">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3ccb4-113">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3ccb4-114">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ccb4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ccb4-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ccb4-115">See Also</span></span>  
 [<span data-ttu-id="3ccb4-116">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="3ccb4-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
