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
ms.openlocfilehash: 46cd8b5c22f48ba45c4da7fa8876d6807a21f2b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124150"
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="9f425-102">Método ResolveTypeLib</span><span class="sxs-lookup"><span data-stu-id="9f425-102">ResolveTypeLib Method</span></span>
<span data-ttu-id="9f425-103">Resolve o nome simples de uma biblioteca de tipos retornando seu caminho totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="9f425-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f425-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f425-104">Syntax</span></span>  
  
```cpp  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f425-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9f425-105">Parameters</span></span>  
 `bstrSimpleName`  
 <span data-ttu-id="9f425-106">no Um [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) que contém o nome simples da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="9f425-106">[in] A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="9f425-107">no O GUID atribuído à biblioteca de tipos no registro.</span><span class="sxs-lookup"><span data-stu-id="9f425-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="9f425-108">no A ID da localização da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="9f425-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="9f425-109">no O número de versão principal da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="9f425-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="9f425-110">Por exemplo, para a versão *x. y*, o número de versão principal é *x*.</span><span class="sxs-lookup"><span data-stu-id="9f425-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="9f425-111">no O número de versão secundária da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="9f425-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="9f425-112">Por exemplo, para a versão *x. y*, o número de versão secundária é *y*.</span><span class="sxs-lookup"><span data-stu-id="9f425-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="9f425-113">no Um sinalizador [SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind) que identifica o ambiente operacional.</span><span class="sxs-lookup"><span data-stu-id="9f425-113">[in] A [SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the operating environment.</span></span> <span data-ttu-id="9f425-114">Os valores comuns são SYS_WIN32 e SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="9f425-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="9f425-115">fora Um ponteiro para um [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) que contém o caminho completo da biblioteca de tipos denominada no parâmetro `bstrSimpleName`.</span><span class="sxs-lookup"><span data-stu-id="9f425-115">[out] A pointer to a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f425-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="9f425-116">Remarks</span></span>  
 <span data-ttu-id="9f425-117">O método `ResolveTypeLib` é chamado pela [função LoadTypeLibWithResolver](loadtypelibwithresolver-function.md) durante o processamento de [Tlbexp. exe (tipo de exportador de biblioteca de tipos)](../../tools/tlbexp-exe-type-library-exporter.md) .</span><span class="sxs-lookup"><span data-stu-id="9f425-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="9f425-118">Implementações personalizadas dessa interface devem retornar um [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) que contém o caminho completo da biblioteca de tipos denominada no parâmetro `bstrSimpleName`.</span><span class="sxs-lookup"><span data-stu-id="9f425-118">Custom implementations of this interface must return a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f425-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9f425-119">Requirements</span></span>  
 <span data-ttu-id="9f425-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f425-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f425-121">**Cabeçalho:** TlbRef. idl, TlbRef. h</span><span class="sxs-lookup"><span data-stu-id="9f425-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="9f425-122">**Biblioteca:** TlbRef. lib</span><span class="sxs-lookup"><span data-stu-id="9f425-122">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="9f425-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f425-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f425-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f425-124">See also</span></span>

- [<span data-ttu-id="9f425-125">Funções auxiliares do Tlbexp</span><span class="sxs-lookup"><span data-stu-id="9f425-125">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="9f425-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="9f425-126">LoadTypeLibEx</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
