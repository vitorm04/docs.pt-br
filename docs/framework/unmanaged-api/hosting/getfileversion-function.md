---
title: Função GetFileVersion
ms.date: 03/30/2017
api_name:
- GetFileVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetFileVersion
helpviewer_keywords:
- GetFileVersion function [.NET Framework hosting]
ms.assetid: b3222c85-da88-4485-97d7-3a6ee3e8d358
topic_type:
- apiref
ms.openlocfilehash: f197c8802bd9e55391b3e3e20c64398736070a16
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136329"
---
# <a name="getfileversion-function"></a><span data-ttu-id="60694-102">Função GetFileVersion</span><span class="sxs-lookup"><span data-stu-id="60694-102">GetFileVersion Function</span></span>
<span data-ttu-id="60694-103">Obtém as informações de versão do Common Language Runtime (CLR) do arquivo especificado, usando o buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="60694-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="60694-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="60694-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60694-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60694-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,   
    [in, out] LPWSTR   szBuffer,   
    [in]  DWORD        cchBuffer,   
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60694-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="60694-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="60694-107">no O caminho do arquivo a ser examinado.</span><span class="sxs-lookup"><span data-stu-id="60694-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="60694-108">[entrada, saída] O buffer alocado para as informações de versão que são retornadas.</span><span class="sxs-lookup"><span data-stu-id="60694-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="60694-109">no O tamanho, em caracteres largos, de `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="60694-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="60694-110">fora O tamanho, em bytes, do `szBuffer`retornado.</span><span class="sxs-lookup"><span data-stu-id="60694-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60694-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="60694-111">Requirements</span></span>  
 <span data-ttu-id="60694-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60694-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60694-113">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="60694-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="60694-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60694-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60694-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60694-115">See also</span></span>

- [<span data-ttu-id="60694-116">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="60694-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
