---
title: Função ForwardTranslateAccelerator – referência de API não gerenciada do WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: f6e8208ffe2c186234f30f31e346ca6b1d0be4c0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747042"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="e4fcc-102">Função ForwardTranslateAccelerator (referência de API não gerenciada do WPF)</span><span class="sxs-lookup"><span data-stu-id="e4fcc-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="e4fcc-103">Esta API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usada diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="e4fcc-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="e4fcc-104">Usado pela infraestrutura do Windows Presentation Foundation (WPF) para o gerenciamento do Windows.</span><span class="sxs-lookup"><span data-stu-id="e4fcc-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4fcc-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4fcc-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4fcc-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e4fcc-106">Parameters</span></span>  
 <span data-ttu-id="e4fcc-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="e4fcc-107">pMsg</span></span>  
 <span data-ttu-id="e4fcc-108">Um ponteiro para uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="e4fcc-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="e4fcc-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="e4fcc-109">appUnhandled</span></span>  
 <span data-ttu-id="e4fcc-110">`true` quando o aplicativo já tem a oportunidade de lidar com a mensagem de entrada, mas não a tratou; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="e4fcc-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4fcc-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e4fcc-111">Requirements</span></span>  
 <span data-ttu-id="e4fcc-112">**Plataformas:** Consulte [.NET Framework requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4fcc-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4fcc-113">**DLL**</span><span class="sxs-lookup"><span data-stu-id="e4fcc-113">**DLL:**</span></span>  
  
 <span data-ttu-id="e4fcc-114">No .NET Framework 3,0 e 3,5: PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="e4fcc-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="e4fcc-115">No .NET Framework 4 e posterior: PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="e4fcc-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="e4fcc-116">**Versão do .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4fcc-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4fcc-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4fcc-117">See also</span></span>

- [<span data-ttu-id="e4fcc-118">Referência de API não gerenciada do WPF</span><span class="sxs-lookup"><span data-stu-id="e4fcc-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
