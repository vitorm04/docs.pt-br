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
ms.openlocfilehash: 569efa9d14ef10d8c5cf735091778a6c78882815
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781158"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="fbb3c-102">Função RunDll32ShimW</span><span class="sxs-lookup"><span data-stu-id="fbb3c-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="fbb3c-103">Executa o comando especificado.</span><span class="sxs-lookup"><span data-stu-id="fbb3c-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="fbb3c-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="fbb3c-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbb3c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fbb3c-105">Syntax</span></span>  
  
```cpp  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbb3c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fbb3c-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="fbb3c-107">[in] Um identificador para uma janela na qual a saída do comando será exibida.</span><span class="sxs-lookup"><span data-stu-id="fbb3c-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="fbb3c-108">[in] Um identificador para a biblioteca que contém o comando.</span><span class="sxs-lookup"><span data-stu-id="fbb3c-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="fbb3c-109">[in] Uma cadeia de caracteres que especifica o comando a ser executado.</span><span class="sxs-lookup"><span data-stu-id="fbb3c-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="fbb3c-110">[in] Um inteiro que especifica o modo de exibição da janela de saída.</span><span class="sxs-lookup"><span data-stu-id="fbb3c-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbb3c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fbb3c-111">Requirements</span></span>  
 <span data-ttu-id="fbb3c-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbb3c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbb3c-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fbb3c-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fbb3c-114">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fbb3c-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fbb3c-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbb3c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbb3c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbb3c-116">See also</span></span>

- [<span data-ttu-id="fbb3c-117">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="fbb3c-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
