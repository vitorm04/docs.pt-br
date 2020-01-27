---
title: Função LoadFromHistory – referência de API não gerenciada do WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: 7807e073d1f09ac6a6213aee6d86d53cc75a3c56
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727936"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="928d7-102">Função LoadFromHistory (referência de API não gerenciada do WPF)</span><span class="sxs-lookup"><span data-stu-id="928d7-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="928d7-103">Esta API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usada diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="928d7-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="928d7-104">Usado pela infraestrutura do Windows Presentation Foundation (WPF) para o gerenciamento do Windows.</span><span class="sxs-lookup"><span data-stu-id="928d7-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="928d7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="928d7-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="928d7-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="928d7-106">Parameters</span></span>  
 <span data-ttu-id="928d7-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="928d7-107">pHistoryStream</span></span>  
 <span data-ttu-id="928d7-108">Um ponteiro para um fluxo de informações de histórico.</span><span class="sxs-lookup"><span data-stu-id="928d7-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="928d7-109">pBindCtx</span><span class="sxs-lookup"><span data-stu-id="928d7-109">pBindCtx</span></span>  
 <span data-ttu-id="928d7-110">Um ponteiro para um contexto de associação.</span><span class="sxs-lookup"><span data-stu-id="928d7-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="928d7-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="928d7-111">Requirements</span></span>  
 <span data-ttu-id="928d7-112">**Plataformas:** Consulte [.NET Framework requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="928d7-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="928d7-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="928d7-113">**DLL:**</span></span>  
  
 <span data-ttu-id="928d7-114">No .NET Framework 3,0 e 3,5: PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="928d7-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="928d7-115">No .NET Framework 4 e posterior: PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="928d7-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="928d7-116">**Versão do .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="928d7-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="928d7-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="928d7-117">See also</span></span>

- [<span data-ttu-id="928d7-118">Referência de API não gerenciada do WPF</span><span class="sxs-lookup"><span data-stu-id="928d7-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
