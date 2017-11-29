---
title: "Função GetTypeLibInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetTypeLibInfo
api_location: TlbRef.dll
api_type: DLLExport
f1_keywords: GetTypeLibInfo
helpviewer_keywords: GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a5dc55a9538798b81dce9db02583c271b9f2ed54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="f020a-102">Função GetTypeLibInfo</span><span class="sxs-lookup"><span data-stu-id="f020a-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="f020a-103">Retorna informações sobre a biblioteca de tipos especificada examinando sua [TLIBATTR](https://msdn.microsoft.com/library/ms221376\(v=vs.85\).aspx) estrutura.</span><span class="sxs-lookup"><span data-stu-id="f020a-103">Returns information about the specified type library by examining its [TLIBATTR](https://msdn.microsoft.com/library/ms221376\(v=vs.85\).aspx) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f020a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f020a-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="f020a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f020a-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="f020a-106">[in] O nome do arquivo da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="f020a-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="f020a-107">[out] O GUID da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="f020a-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="f020a-108">[out] A identificação da localização da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="f020a-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="f020a-109">[out] Um [SYSKIND](https://msdn.microsoft.com/library/ms221272\(v=vs.85\).aspx) sinalizador que identifica o sistema operacional de destino para a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="f020a-109">[out] A [SYSKIND](https://msdn.microsoft.com/library/ms221272\(v=vs.85\).aspx) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="f020a-110">Os valores comuns são SYS_WIN32 e SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="f020a-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="f020a-111">[out] O número de versão principal da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="f020a-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="f020a-112">Por exemplo, para versão *x. y*, o número de versão principal é *x*.</span><span class="sxs-lookup"><span data-stu-id="f020a-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="f020a-113">[out] O número de versão secundária da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="f020a-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="f020a-114">Por exemplo, para versão *x. y*, é o número de versão secundária *y*.</span><span class="sxs-lookup"><span data-stu-id="f020a-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f020a-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="f020a-115">Remarks</span></span>  
 <span data-ttu-id="f020a-116">O `GetTypeLibInfo` função é chamada pelo [Tlbexp.exe (exportador da biblioteca)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="f020a-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="f020a-117">Essa ferramenta gera uma biblioteca de tipos que descreve os tipos em um assembly do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="f020a-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="f020a-118">Se nenhum parâmetro for nulo, a função retorna um `HRESULT` de `E_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="f020a-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="f020a-119">Caso contrário, retornará `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="f020a-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f020a-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f020a-120">Requirements</span></span>  
 <span data-ttu-id="f020a-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f020a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f020a-122">**Cabeçalho:** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="f020a-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="f020a-123">**Biblioteca:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="f020a-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="f020a-124">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f020a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f020a-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f020a-125">See Also</span></span>  
 [<span data-ttu-id="f020a-126">Funções auxiliares do TlbExp</span><span class="sxs-lookup"><span data-stu-id="f020a-126">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 <span data-ttu-id="f020a-127">[Função LoadTypeLibEx](https://msdn.microsoft.com/library/ms221249\(v=vs.85\).aspx)</span><span class="sxs-lookup"><span data-stu-id="f020a-127">[LoadTypeLibEx Function](https://msdn.microsoft.com/library/ms221249\(v=vs.85\).aspx)</span></span>
