---
title: Função GetTypeLibInfo
ms.date: 03/30/2017
api_name:
- GetTypeLibInfo
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- GetTypeLibInfo
helpviewer_keywords:
- GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 916d62a2b79a44d92611e735c6f9bbb3e01970e2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782736"
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="58baa-102">Função GetTypeLibInfo</span><span class="sxs-lookup"><span data-stu-id="58baa-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="58baa-103">Retorna informações sobre a biblioteca de tipos especificada, examinando sua [TLIBATTR](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagtlibattr) estrutura.</span><span class="sxs-lookup"><span data-stu-id="58baa-103">Returns information about the specified type library by examining its [TLIBATTR](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagtlibattr) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58baa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58baa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58baa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="58baa-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="58baa-106">[in] O nome do arquivo da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="58baa-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="58baa-107">[out] O GUID da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="58baa-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="58baa-108">[out] A ID de localização da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="58baa-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="58baa-109">[out] Um [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) sinalizador que identifica o sistema operacional de destino para a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="58baa-109">[out] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="58baa-110">Os valores comuns são SYS_WIN32 e SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="58baa-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="58baa-111">[out] O número de versão principal da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="58baa-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="58baa-112">Por exemplo, para versão *x. y*, o número de versão principal é *x*.</span><span class="sxs-lookup"><span data-stu-id="58baa-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="58baa-113">[out] O número de versão secundária da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="58baa-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="58baa-114">Por exemplo, para versão *x. y*, é o número de versão secundária *y*.</span><span class="sxs-lookup"><span data-stu-id="58baa-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58baa-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="58baa-115">Remarks</span></span>  
 <span data-ttu-id="58baa-116">O `GetTypeLibInfo` função é chamada pela [Tlbexp.exe (exportador da biblioteca)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="58baa-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="58baa-117">Essa ferramenta gera uma biblioteca de tipos que descreve os tipos em um assembly do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="58baa-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="58baa-118">Se nenhum parâmetro for nulo, a função retorna um `HRESULT` de `E_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="58baa-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="58baa-119">Caso contrário, retornará `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="58baa-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58baa-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="58baa-120">Requirements</span></span>  
 <span data-ttu-id="58baa-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58baa-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58baa-122">**Cabeçalho:** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="58baa-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="58baa-123">**Biblioteca:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="58baa-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="58baa-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58baa-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58baa-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58baa-125">See also</span></span>

- [<span data-ttu-id="58baa-126">Funções auxiliares do Tlbexp</span><span class="sxs-lookup"><span data-stu-id="58baa-126">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [<span data-ttu-id="58baa-127">Função LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="58baa-127">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
