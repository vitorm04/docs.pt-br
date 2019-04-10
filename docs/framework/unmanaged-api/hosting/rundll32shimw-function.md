---
title: Função RunDll32ShimW
ms.date: 03/30/2017
api_name:
- RunDll32ShimW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- RunDll32ShimW
helpviewer_keywords:
- RunDll32ShimW function [.NET Framework hosting]
ms.assetid: 9ea07b57-96e2-44df-8711-8fe6c119087f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccfdf9ffab35f076b85c067c2b412020a5f541b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231078"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="96103-102">Função RunDll32ShimW</span><span class="sxs-lookup"><span data-stu-id="96103-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="96103-103">Executa o comando especificado.</span><span class="sxs-lookup"><span data-stu-id="96103-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="96103-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="96103-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96103-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96103-105">Syntax</span></span>  
  
```  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96103-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="96103-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="96103-107">[in] Um identificador para uma janela na qual a saída do comando será exibida.</span><span class="sxs-lookup"><span data-stu-id="96103-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="96103-108">[in] Um identificador para a biblioteca que contém o comando.</span><span class="sxs-lookup"><span data-stu-id="96103-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="96103-109">[in] Uma cadeia de caracteres que especifica o comando a ser executado.</span><span class="sxs-lookup"><span data-stu-id="96103-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="96103-110">[in] Um inteiro que especifica o modo de exibição da janela de saída.</span><span class="sxs-lookup"><span data-stu-id="96103-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96103-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="96103-111">Requirements</span></span>  
 <span data-ttu-id="96103-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96103-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96103-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="96103-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="96103-114">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="96103-114">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="96103-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="96103-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="96103-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96103-116">See also</span></span>

- [<span data-ttu-id="96103-117">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="96103-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
