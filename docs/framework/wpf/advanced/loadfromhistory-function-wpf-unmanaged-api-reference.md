---
title: Função LoadFromHistory (referência de API não gerenciada WPF)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: a4480d54390aea2771e2939b0a0825f6c49c3564
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084944"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="fa43f-102">Função LoadFromHistory (referência de API não gerenciada WPF)</span><span class="sxs-lookup"><span data-stu-id="fa43f-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="fa43f-103">Essa API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="fa43f-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="fa43f-104">Usado pela infraestrutura do Windows Presentation Foundation (WPF) para gerenciamento do windows.</span><span class="sxs-lookup"><span data-stu-id="fa43f-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa43f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fa43f-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa43f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fa43f-106">Parameters</span></span>  
 <span data-ttu-id="fa43f-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="fa43f-107">pHistoryStream</span></span>  
 <span data-ttu-id="fa43f-108">Um ponteiro para um fluxo de informações do histórico.</span><span class="sxs-lookup"><span data-stu-id="fa43f-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="fa43f-109">pBindCtx</span><span class="sxs-lookup"><span data-stu-id="fa43f-109">pBindCtx</span></span>  
 <span data-ttu-id="fa43f-110">Um ponteiro para um contexto de associação.</span><span class="sxs-lookup"><span data-stu-id="fa43f-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa43f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fa43f-111">Requirements</span></span>  
 <span data-ttu-id="fa43f-112">**Plataformas:** Ver [requisitos de sistema do .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa43f-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 **<span data-ttu-id="fa43f-113">DLL:</span><span class="sxs-lookup"><span data-stu-id="fa43f-113">DLL:</span></span>**  
  
 <span data-ttu-id="fa43f-114">No .NET Framework 3.0 e 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="fa43f-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="fa43f-115">No .NET Framework 4 e posterior: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="fa43f-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 **<span data-ttu-id="fa43f-116">Versão do .NET framework:</span><span class="sxs-lookup"><span data-stu-id="fa43f-116">.NET Framework Version:</span></span>** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fa43f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa43f-117">See also</span></span>

- [<span data-ttu-id="fa43f-118">Referência de API não gerenciada do WPF</span><span class="sxs-lookup"><span data-stu-id="fa43f-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
