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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b772de720a8c3b669bd3cbe9591637d931cb8763
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="getfileversion-function"></a><span data-ttu-id="0fc0e-102">Função GetFileVersion</span><span class="sxs-lookup"><span data-stu-id="0fc0e-102">GetFileVersion Function</span></span>
<span data-ttu-id="0fc0e-103">Obtém as informações de versão de runtime (CLR) de linguagem comum do arquivo especificado, usando o buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="0fc0e-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="0fc0e-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0fc0e-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fc0e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0fc0e-105">Syntax</span></span>  
  
```  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,   
    [in, out] LPWSTR   szBuffer,   
    [in]  DWORD        cchBuffer,   
    [out] DWORD        *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0fc0e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0fc0e-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="0fc0e-107">[in] O caminho do arquivo a ser examinado.</span><span class="sxs-lookup"><span data-stu-id="0fc0e-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="0fc0e-108">[out no] O buffer alocado para as informações de versão que são retornadas.</span><span class="sxs-lookup"><span data-stu-id="0fc0e-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="0fc0e-109">[in] O tamanho, em caracteres largos, de `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="0fc0e-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="0fc0e-110">[out] O tamanho, em bytes, do retornado `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="0fc0e-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fc0e-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0fc0e-111">Requirements</span></span>  
 <span data-ttu-id="0fc0e-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fc0e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fc0e-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0fc0e-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0fc0e-114">**Versões do .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fc0e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fc0e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0fc0e-115">See Also</span></span>  
 [<span data-ttu-id="0fc0e-116">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="0fc0e-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
