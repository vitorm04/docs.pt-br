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
ms.openlocfilehash: 56a9b97f37240e385dbd1788bafea62578d687a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457861"
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="5fe2f-102">Função GetTypeLibInfo</span><span class="sxs-lookup"><span data-stu-id="5fe2f-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="5fe2f-103">Retorna informações sobre a biblioteca de tipos especificada examinando sua [TLIBATTR](https://msdn.microsoft.com/library/ms221376\(v=vs.85\).aspx) estrutura.</span><span class="sxs-lookup"><span data-stu-id="5fe2f-103">Returns information about the specified type library by examining its [TLIBATTR](https://msdn.microsoft.com/library/ms221376\(v=vs.85\).aspx) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fe2f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5fe2f-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5fe2f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5fe2f-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="5fe2f-106">[in] O nome do arquivo da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="5fe2f-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="5fe2f-107">[out] O GUID da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="5fe2f-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="5fe2f-108">[out] A identificação da localização da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="5fe2f-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="5fe2f-109">[out] Um [SYSKIND](https://msdn.microsoft.com/library/ms221272\(v=vs.85\).aspx) sinalizador que identifica o sistema operacional de destino para a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="5fe2f-109">[out] A [SYSKIND](https://msdn.microsoft.com/library/ms221272\(v=vs.85\).aspx) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="5fe2f-110">Os valores comuns são SYS_WIN32 e SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="5fe2f-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="5fe2f-111">[out] O número de versão principal da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="5fe2f-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="5fe2f-112">Por exemplo, para versão *x. y*, o número de versão principal é *x*.</span><span class="sxs-lookup"><span data-stu-id="5fe2f-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="5fe2f-113">[out] O número de versão secundária da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="5fe2f-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="5fe2f-114">Por exemplo, para versão *x. y*, é o número de versão secundária *y*.</span><span class="sxs-lookup"><span data-stu-id="5fe2f-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fe2f-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="5fe2f-115">Remarks</span></span>  
 <span data-ttu-id="5fe2f-116">O `GetTypeLibInfo` função é chamada pelo [Tlbexp.exe (exportador da biblioteca)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="5fe2f-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="5fe2f-117">Essa ferramenta gera uma biblioteca de tipos que descreve os tipos em um assembly do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="5fe2f-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="5fe2f-118">Se nenhum parâmetro for nulo, a função retorna um `HRESULT` de `E_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="5fe2f-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="5fe2f-119">Caso contrário, retornará `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="5fe2f-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fe2f-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5fe2f-120">Requirements</span></span>  
 <span data-ttu-id="5fe2f-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fe2f-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fe2f-122">**Cabeçalho:** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="5fe2f-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="5fe2f-123">**Biblioteca:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="5fe2f-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="5fe2f-124">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fe2f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fe2f-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5fe2f-125">See Also</span></span>  
 [<span data-ttu-id="5fe2f-126">Funções auxiliares do Tlbexp</span><span class="sxs-lookup"><span data-stu-id="5fe2f-126">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 <span data-ttu-id="5fe2f-127">[Função LoadTypeLibEx](https://msdn.microsoft.com/library/ms221249\(v=vs.85\).aspx)</span><span class="sxs-lookup"><span data-stu-id="5fe2f-127">[LoadTypeLibEx Function](https://msdn.microsoft.com/library/ms221249\(v=vs.85\).aspx)</span></span>
