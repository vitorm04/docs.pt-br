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
ms.openlocfilehash: 4f05eb2e6ef31cf1993a623c38bb177f7e3c297e
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935644"
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="02d4a-102">Função GetTypeLibInfo</span><span class="sxs-lookup"><span data-stu-id="02d4a-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="02d4a-103">Retorna informações sobre a biblioteca de tipos especificada examinando sua estrutura [TLIBATTR](/windows/win32/api/oaidl/ns-oaidl-tlibattr) .</span><span class="sxs-lookup"><span data-stu-id="02d4a-103">Returns information about the specified type library by examining its [TLIBATTR](/windows/win32/api/oaidl/ns-oaidl-tlibattr) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02d4a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02d4a-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="02d4a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="02d4a-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="02d4a-106">no O nome do arquivo da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="02d4a-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="02d4a-107">fora O GUID da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="02d4a-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="02d4a-108">fora A ID da localização da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="02d4a-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="02d4a-109">fora Um sinalizador [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) que identifica o sistema operacional de destino para a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="02d4a-109">[out] A [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="02d4a-110">Os valores comuns são SYS_WIN32 e SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="02d4a-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="02d4a-111">fora O número de versão principal da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="02d4a-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="02d4a-112">Por exemplo, para a versão *x. y*, o número de versão principal é *x*.</span><span class="sxs-lookup"><span data-stu-id="02d4a-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="02d4a-113">fora O número de versão secundária da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="02d4a-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="02d4a-114">Por exemplo, para a versão *x. y*, o número de versão secundária é *y*.</span><span class="sxs-lookup"><span data-stu-id="02d4a-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02d4a-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="02d4a-115">Remarks</span></span>  
 <span data-ttu-id="02d4a-116">A função `GetTypeLibInfo` é chamada pelo [Tlbexp. exe (tipo de exportador da biblioteca de tipos)](../../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="02d4a-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="02d4a-117">Essa ferramenta gera uma biblioteca de tipos que descreve os tipos em um assembly Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="02d4a-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="02d4a-118">Se qualquer parâmetro for nulo, a função retornará uma `HRESULT` de `E_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="02d4a-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="02d4a-119">Caso contrário, retornará `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="02d4a-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02d4a-120">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="02d4a-120">Requirements</span></span>  
 <span data-ttu-id="02d4a-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02d4a-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02d4a-122">**Cabeçalho:** TlbRef. h</span><span class="sxs-lookup"><span data-stu-id="02d4a-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="02d4a-123">**Biblioteca:** TlbRef. lib</span><span class="sxs-lookup"><span data-stu-id="02d4a-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="02d4a-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02d4a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02d4a-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="02d4a-125">See also</span></span>

- [<span data-ttu-id="02d4a-126">Funções auxiliares do Tlbexp</span><span class="sxs-lookup"><span data-stu-id="02d4a-126">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="02d4a-127">Função LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="02d4a-127">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
