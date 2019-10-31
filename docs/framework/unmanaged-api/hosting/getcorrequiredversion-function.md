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
ms.openlocfilehash: 661eb758e1651901bb56810640a68f0de0b4e851
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136473"
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="e3ded-102">Função GetCORRequiredVersion</span><span class="sxs-lookup"><span data-stu-id="e3ded-102">GetCORRequiredVersion Function</span></span>
<span data-ttu-id="e3ded-103">Obtém o número de versão do Common Language Runtime (CLR) necessário.</span><span class="sxs-lookup"><span data-stu-id="e3ded-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="e3ded-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e3ded-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3ded-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3ded-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3ded-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e3ded-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="e3ded-107">fora Um buffer que contém uma cadeia de caracteres que especifica o número de versão.</span><span class="sxs-lookup"><span data-stu-id="e3ded-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="e3ded-108">no O tamanho, em bytes, do buffer.</span><span class="sxs-lookup"><span data-stu-id="e3ded-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="e3ded-109">fora O número de bytes retornados no buffer.</span><span class="sxs-lookup"><span data-stu-id="e3ded-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3ded-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e3ded-110">Requirements</span></span>  
 <span data-ttu-id="e3ded-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3ded-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3ded-112">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e3ded-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e3ded-113">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e3ded-113">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3ded-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3ded-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3ded-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3ded-115">See also</span></span>

- [<span data-ttu-id="e3ded-116">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="e3ded-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
