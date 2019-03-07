---
title: Método ResolveTypeLib
ms.date: 03/30/2017
api_name:
- ResolveTypeLib
api_location:
- tlbref.dll
f1_keywords:
- ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b87460b9e525f2cf91b8f177c06286b5bbb3c52
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486115"
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="a2f52-102">Método ResolveTypeLib</span><span class="sxs-lookup"><span data-stu-id="a2f52-102">ResolveTypeLib Method</span></span>
<span data-ttu-id="a2f52-103">Resolve o nome simples de uma biblioteca de tipos, retornando seu caminho totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="a2f52-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2f52-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a2f52-104">Syntax</span></span>  
  
```  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2f52-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a2f52-105">Parameters</span></span>  
 `bstrSimpleName`  
 <span data-ttu-id="a2f52-106">[in] Um [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) que contém o nome simple da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="a2f52-106">[in] A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="a2f52-107">[in] O GUID atribuído à biblioteca de tipos no registro.</span><span class="sxs-lookup"><span data-stu-id="a2f52-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="a2f52-108">[in] A ID de localização da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="a2f52-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="a2f52-109">[in] O número de versão principal da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="a2f52-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="a2f52-110">Por exemplo, para versão *x. y*, o número de versão principal é *x*.</span><span class="sxs-lookup"><span data-stu-id="a2f52-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="a2f52-111">[in] O número de versão secundária da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="a2f52-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="a2f52-112">Por exemplo, para versão *x. y*, é o número de versão secundária *y*.</span><span class="sxs-lookup"><span data-stu-id="a2f52-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="a2f52-113">[in] Um [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) sinalizador que identifica o ambiente operacional.</span><span class="sxs-lookup"><span data-stu-id="a2f52-113">[in] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) flag that identifies the operating environment.</span></span> <span data-ttu-id="a2f52-114">Os valores comuns são SYS_WIN32 e SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="a2f52-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="a2f52-115">[out] Um ponteiro para um [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) que contém o caminho completo da biblioteca de tipos nomeado no `bstrSimpleName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a2f52-115">[out] A pointer to a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2f52-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="a2f52-116">Remarks</span></span>  
 <span data-ttu-id="a2f52-117">O `ResolveTypeLib` método é chamado pelo [função LoadTypeLibWithResolver](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) durante [Tlbexp.exe (exportador da biblioteca)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) de processamento.</span><span class="sxs-lookup"><span data-stu-id="a2f52-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="a2f52-118">As implementações personalizadas dessa interface devem retornar um [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) que contém o caminho completo da biblioteca de tipos nomeado no `bstrSimpleName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a2f52-118">Custom implementations of this interface must return a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2f52-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a2f52-119">Requirements</span></span>  
 <span data-ttu-id="a2f52-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2f52-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2f52-121">**Cabeçalho:** TlbRef.idl, TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="a2f52-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="a2f52-122">**Biblioteca:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="a2f52-122">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="a2f52-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2f52-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2f52-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2f52-124">See also</span></span>
- [<span data-ttu-id="a2f52-125">Funções auxiliares do Tlbexp</span><span class="sxs-lookup"><span data-stu-id="a2f52-125">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [<span data-ttu-id="a2f52-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="a2f52-126">LoadTypeLibEx</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
