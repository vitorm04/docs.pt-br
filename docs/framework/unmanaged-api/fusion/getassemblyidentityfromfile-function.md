---
title: Função GetAssemblyIdentityFromFile
ms.date: 03/30/2017
api_name:
- GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyIdentityFromFile
helpviewer_keywords:
- GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type:
- apiref
ms.openlocfilehash: 50ec5a23db4d2460480bcc3e463ecd88e7470bde
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134526"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="f736c-102">Função GetAssemblyIdentityFromFile</span><span class="sxs-lookup"><span data-stu-id="f736c-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="f736c-103">Obtém um ponteiro para um objeto `IUnknown` com o `IID` especificado no assembly no caminho de arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="f736c-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f736c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f736c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="f736c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f736c-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="f736c-106">no Um caminho válido para o assembly solicitado.</span><span class="sxs-lookup"><span data-stu-id="f736c-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="f736c-107">no A `IID` da interface a ser retornada.</span><span class="sxs-lookup"><span data-stu-id="f736c-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="f736c-108">fora O ponteiro de interface retornado.</span><span class="sxs-lookup"><span data-stu-id="f736c-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f736c-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f736c-109">Requirements</span></span>  
 <span data-ttu-id="f736c-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f736c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f736c-111">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f736c-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f736c-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f736c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f736c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f736c-113">See also</span></span>

- [<span data-ttu-id="f736c-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="f736c-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="f736c-115">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="f736c-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
