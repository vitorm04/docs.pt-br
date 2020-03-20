---
title: Função LoadFromHistory - Referência de API não gerenciada do WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: be9b8658614e678b4370044a753554859d230fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141569"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="d52ae-102">Função LoadFromHistory (referência de API não gerenciada WPF)</span><span class="sxs-lookup"><span data-stu-id="d52ae-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="d52ae-103">Esta API suporta a infra-estrutura do Windows Presentation Foundation (WPF) e não se destina a ser usada diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="d52ae-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="d52ae-104">Usado pela infra-estrutura do Windows Presentation Foundation (WPF) para gerenciamento de janelas.</span><span class="sxs-lookup"><span data-stu-id="d52ae-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d52ae-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d52ae-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="d52ae-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="d52ae-106">Parameters</span></span>  
 <span data-ttu-id="d52ae-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="d52ae-107">pHistoryStream</span></span>  
 <span data-ttu-id="d52ae-108">Um ponteiro para um fluxo de informações históricas.</span><span class="sxs-lookup"><span data-stu-id="d52ae-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="d52ae-109">pBindCtx</span><span class="sxs-lookup"><span data-stu-id="d52ae-109">pBindCtx</span></span>  
 <span data-ttu-id="d52ae-110">Um ponteiro para um contexto de ligação.</span><span class="sxs-lookup"><span data-stu-id="d52ae-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d52ae-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d52ae-111">Requirements</span></span>  
 <span data-ttu-id="d52ae-112">**Plataformas:** Consulte [os requisitos do sistema de estrutura .NET](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d52ae-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d52ae-113">**Dll:**</span><span class="sxs-lookup"><span data-stu-id="d52ae-113">**DLL:**</span></span>  
  
 <span data-ttu-id="d52ae-114">No quadro .NET 3.0 e 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="d52ae-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="d52ae-115">No Quadro .NET 4 e posteriores: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="d52ae-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="d52ae-116">**.NET Framework Version:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d52ae-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d52ae-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="d52ae-117">See also</span></span>

- [<span data-ttu-id="d52ae-118">Referência de API não gerenciada do WPF</span><span class="sxs-lookup"><span data-stu-id="d52ae-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
