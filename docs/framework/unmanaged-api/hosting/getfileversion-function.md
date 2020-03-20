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
ms.openlocfilehash: f3b51c1b376fa9c664de53aa76ec724ca305ae6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178172"
---
# <a name="getfileversion-function"></a><span data-ttu-id="2ca70-102">Função GetFileVersion</span><span class="sxs-lookup"><span data-stu-id="2ca70-102">GetFileVersion Function</span></span>
<span data-ttu-id="2ca70-103">Obtém as informações da versão de tempo de execução do idioma comum (CLR) do arquivo especificado, usando o buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="2ca70-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="2ca70-104">Esta função foi depreciada no Quadro .NET 4.</span><span class="sxs-lookup"><span data-stu-id="2ca70-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ca70-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2ca70-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,
    [in, out] LPWSTR   szBuffer,
    [in]  DWORD        cchBuffer,
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ca70-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="2ca70-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="2ca70-107">[em] O caminho do arquivo a ser examinado.</span><span class="sxs-lookup"><span data-stu-id="2ca70-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="2ca70-108">[dentro, fora] O buffer alocado para as informações da versão que são retornadas.</span><span class="sxs-lookup"><span data-stu-id="2ca70-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="2ca70-109">[em] O tamanho, em caracteres largos, de `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="2ca70-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="2ca70-110">[fora] O tamanho, em bytes, `szBuffer`do devolvido.</span><span class="sxs-lookup"><span data-stu-id="2ca70-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ca70-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2ca70-111">Requirements</span></span>  
 <span data-ttu-id="2ca70-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ca70-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ca70-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2ca70-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2ca70-114">**.NET Framework Versions:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ca70-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ca70-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="2ca70-115">See also</span></span>

- [<span data-ttu-id="2ca70-116">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="2ca70-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
