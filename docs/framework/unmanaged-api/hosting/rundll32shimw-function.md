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
ms.openlocfilehash: fa7df47ab55b8dc7ef3f55f5591b44614052bcee
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490133"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="8602a-102">Função RunDll32ShimW</span><span class="sxs-lookup"><span data-stu-id="8602a-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="8602a-103">Executa o comando especificado.</span><span class="sxs-lookup"><span data-stu-id="8602a-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="8602a-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8602a-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8602a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8602a-105">Syntax</span></span>  
  
```  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8602a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8602a-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="8602a-107">[in] Um identificador para uma janela na qual a saída do comando será exibida.</span><span class="sxs-lookup"><span data-stu-id="8602a-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="8602a-108">[in] Um identificador para a biblioteca que contém o comando.</span><span class="sxs-lookup"><span data-stu-id="8602a-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="8602a-109">[in] Uma cadeia de caracteres que especifica o comando a ser executado.</span><span class="sxs-lookup"><span data-stu-id="8602a-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="8602a-110">[in] Um inteiro que especifica o modo de exibição da janela de saída.</span><span class="sxs-lookup"><span data-stu-id="8602a-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8602a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8602a-111">Requirements</span></span>  
 <span data-ttu-id="8602a-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8602a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8602a-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8602a-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8602a-114">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8602a-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8602a-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8602a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8602a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8602a-116">See also</span></span>

- [<span data-ttu-id="8602a-117">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="8602a-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
