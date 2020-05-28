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
ms.openlocfilehash: 90304eb94e6f53d3132c97f5ababdc45f6053d7c
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006565"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="61f9a-102">Função RunDll32ShimW</span><span class="sxs-lookup"><span data-stu-id="61f9a-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="61f9a-103">Executa o comando especificado.</span><span class="sxs-lookup"><span data-stu-id="61f9a-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="61f9a-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="61f9a-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61f9a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61f9a-105">Syntax</span></span>  
  
```cpp  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61f9a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="61f9a-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="61f9a-107">no Um identificador para uma janela na qual a saída do comando será exibida.</span><span class="sxs-lookup"><span data-stu-id="61f9a-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="61f9a-108">no Um identificador para a biblioteca que contém o comando.</span><span class="sxs-lookup"><span data-stu-id="61f9a-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="61f9a-109">no Uma cadeia de caracteres que especifica o comando a ser executado.</span><span class="sxs-lookup"><span data-stu-id="61f9a-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="61f9a-110">no Um inteiro que especifica o modo de exibição para a janela de saída.</span><span class="sxs-lookup"><span data-stu-id="61f9a-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61f9a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="61f9a-111">Requirements</span></span>  
 <span data-ttu-id="61f9a-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61f9a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61f9a-113">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="61f9a-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="61f9a-114">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="61f9a-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="61f9a-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61f9a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61f9a-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="61f9a-116">See also</span></span>

- [<span data-ttu-id="61f9a-117">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="61f9a-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
