---
title: Função CallFunctionShim
ms.date: 03/30/2017
api_name:
- CallFunctionShim
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CallFunctionShim
helpviewer_keywords:
- CallfunctionShim function [.NET Framework hosting]
ms.assetid: 37118465-ddf3-41f0-bf27-335b72777e63
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1060ca140db0304c8e5667f7fdf9624b3ac2b64a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429277"
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="5c9f0-102">Função CallFunctionShim</span><span class="sxs-lookup"><span data-stu-id="5c9f0-102">CallFunctionShim Function</span></span>
<span data-ttu-id="5c9f0-103">Faz uma chamada para a função que tem o nome especificado e os parâmetros na biblioteca especificada.</span><span class="sxs-lookup"><span data-stu-id="5c9f0-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="5c9f0-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c9f0-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c9f0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5c9f0-105">Syntax</span></span>  
  
```  
HRESULT CallFunctionShim (  
    [in] LPCWSTR     szDllName,  
    [in] LPCSTR      szFunctionName,  
    [in] LPVOID      lpvArgument1,  
    [in] LPVOID      lpvArgument2,  
    [in] LPCWSTR     szVersion,  
    [in] LPVOID      pvReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c9f0-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5c9f0-106">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="5c9f0-107">[in] O nome da biblioteca que contém a função.</span><span class="sxs-lookup"><span data-stu-id="5c9f0-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="5c9f0-108">[in] O nome da função.</span><span class="sxs-lookup"><span data-stu-id="5c9f0-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="5c9f0-109">[in] O primeiro argumento para passar para a função.</span><span class="sxs-lookup"><span data-stu-id="5c9f0-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="5c9f0-110">[in] O segundo argumento para passar para a função.</span><span class="sxs-lookup"><span data-stu-id="5c9f0-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="5c9f0-111">[in] A versão da biblioteca que contém a função.</span><span class="sxs-lookup"><span data-stu-id="5c9f0-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="5c9f0-112">[in] Reservado para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="5c9f0-112">[in] Reserved for future use.</span></span> <span data-ttu-id="5c9f0-113">Transmitir zero nesse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5c9f0-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c9f0-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5c9f0-114">Requirements</span></span>  
 <span data-ttu-id="5c9f0-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c9f0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c9f0-116">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5c9f0-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c9f0-117">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5c9f0-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c9f0-118">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c9f0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c9f0-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c9f0-119">See Also</span></span>  
 [<span data-ttu-id="5c9f0-120">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="5c9f0-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
