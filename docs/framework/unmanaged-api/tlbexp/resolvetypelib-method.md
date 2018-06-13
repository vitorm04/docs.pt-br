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
ms.openlocfilehash: 96a9672ee05cb1fe2573620bd1dea23e57339c93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460835"
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="cb55e-102">Método ResolveTypeLib</span><span class="sxs-lookup"><span data-stu-id="cb55e-102">ResolveTypeLib Method</span></span>
<span data-ttu-id="cb55e-103">Resolve o nome simple de uma biblioteca de tipos, retornando o caminho totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="cb55e-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb55e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb55e-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="cb55e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cb55e-105">Parameters</span></span>  
 `bstrSimpleName`  
 <span data-ttu-id="cb55e-106">[in] Um [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) que contém o nome simple da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="cb55e-106">[in] A [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="cb55e-107">[in] O GUID atribuído à biblioteca de tipos no registro.</span><span class="sxs-lookup"><span data-stu-id="cb55e-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="cb55e-108">[in] A identificação da localização da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="cb55e-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="cb55e-109">[in] O número de versão principal da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="cb55e-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="cb55e-110">Por exemplo, para versão *x. y*, o número de versão principal é *x*.</span><span class="sxs-lookup"><span data-stu-id="cb55e-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="cb55e-111">[in] O número de versão secundária da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="cb55e-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="cb55e-112">Por exemplo, para versão *x. y*, é o número de versão secundária *y*.</span><span class="sxs-lookup"><span data-stu-id="cb55e-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="cb55e-113">[in] Um [SYSKIND](http://msdn.microsoft.com/library/662048b2-59a8-48ca-9e4f-2f9a5306faa1) sinalizador que identifica o ambiente operacional.</span><span class="sxs-lookup"><span data-stu-id="cb55e-113">[in] A [SYSKIND](http://msdn.microsoft.com/library/662048b2-59a8-48ca-9e4f-2f9a5306faa1) flag that identifies the operating environment.</span></span> <span data-ttu-id="cb55e-114">Os valores comuns são SYS_WIN32 e SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="cb55e-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="cb55e-115">[out] Um ponteiro para um [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) que contém o caminho completo da biblioteca de tipos nomeado no `bstrSimpleName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cb55e-115">[out] A pointer to a [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb55e-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="cb55e-116">Remarks</span></span>  
 <span data-ttu-id="cb55e-117">O `ResolveTypeLib` método é chamado pelo [função LoadTypeLibWithResolver](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) durante [Tlbexp.exe (exportador da biblioteca)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) de processamento.</span><span class="sxs-lookup"><span data-stu-id="cb55e-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="cb55e-118">Implementações personalizadas dessa interface devem retornar um [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) que contém o caminho completo da biblioteca de tipos nomeado no `bstrSimpleName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cb55e-118">Custom implementations of this interface must return a [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb55e-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cb55e-119">Requirements</span></span>  
 <span data-ttu-id="cb55e-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb55e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb55e-121">**Cabeçalho:** TlbRef.idl, TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="cb55e-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="cb55e-122">**Biblioteca:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="cb55e-122">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="cb55e-123">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb55e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb55e-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb55e-124">See Also</span></span>  
 [<span data-ttu-id="cb55e-125">Funções auxiliares do Tlbexp</span><span class="sxs-lookup"><span data-stu-id="cb55e-125">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [<span data-ttu-id="cb55e-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="cb55e-126">LoadTypeLibEx</span></span>](http://msdn.microsoft.com/library/56a7f9e1-810b-4a42-aa4d-691f4304f5ef)
