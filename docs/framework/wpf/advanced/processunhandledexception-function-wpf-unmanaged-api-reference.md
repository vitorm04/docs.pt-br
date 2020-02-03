---
title: Função ProcessUnhandledException – referência de API não gerenciada do WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: 757e5ac3aa2dc4c87b210b026998523bd82045c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743925"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="d9279-102">Função ProcessUnhandledException (referência de API não gerenciada do WPF)</span><span class="sxs-lookup"><span data-stu-id="d9279-102">ProcessUnhandledException Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="d9279-103">Esta API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usada diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="d9279-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="d9279-104">Usado pela infraestrutura do Windows Presentation Foundation (WPF) para manipulação de exceção.</span><span class="sxs-lookup"><span data-stu-id="d9279-104">Used by the Windows Presentation Foundation (WPF) infrastructure for exception handling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9279-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9279-105">Syntax</span></span>  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9279-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d9279-106">Parameters</span></span>  
 <span data-ttu-id="d9279-107">errorMsg</span><span class="sxs-lookup"><span data-stu-id="d9279-107">errorMsg</span></span>  
 <span data-ttu-id="d9279-108">A mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="d9279-108">The error message.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9279-109">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9279-109">Requirements</span></span>  
 <span data-ttu-id="d9279-110">**Plataformas:** Consulte [.NET Framework requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9279-110">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9279-111">**DLL**</span><span class="sxs-lookup"><span data-stu-id="d9279-111">**DLL:**</span></span>  
  
 <span data-ttu-id="d9279-112">No .NET Framework 3,0 e 3,5: PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="d9279-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="d9279-113">No .NET Framework 4 e posterior: PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="d9279-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="d9279-114">**Versão do .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9279-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9279-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9279-115">See also</span></span>

- [<span data-ttu-id="d9279-116">Referência de API não gerenciada do WPF</span><span class="sxs-lookup"><span data-stu-id="d9279-116">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
