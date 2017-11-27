---
title: "Função SaveToHistory (referência de API não gerenciada WPF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: SaveToHistory
api_location: PresentationHost_v0400.dll
ms.assetid: 6dd101a3-44ad-4143-b228-772156f9b8ff
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b30884433f81aa5e4bf1241ae4fe34494bef788e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="savetohistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="81e15-102">Função SaveToHistory (referência de API não gerenciada WPF)</span><span class="sxs-lookup"><span data-stu-id="81e15-102">SaveToHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="81e15-103">Essa API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="81e15-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="81e15-104">Usado pela infraestrutura do Windows Presentation Foundation (WPF) para o gerenciamento do windows.</span><span class="sxs-lookup"><span data-stu-id="81e15-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81e15-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81e15-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveToHistory(  
   __in_ecount(1) IStream* pHistoryStream  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81e15-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="81e15-106">Parameters</span></span>  
 <span data-ttu-id="81e15-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="81e15-107">pHistoryStream</span></span>  
 <span data-ttu-id="81e15-108">Um ponteiro para o fluxo de histórico.</span><span class="sxs-lookup"><span data-stu-id="81e15-108">A pointer to the history stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81e15-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="81e15-109">Requirements</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81e15-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="81e15-110">Requirements</span></span>  
 <span data-ttu-id="81e15-111">**Plataformas:** consulte [requisitos de sistema do .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81e15-111">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81e15-112">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="81e15-112">**DLL:**</span></span>  
  
 <span data-ttu-id="81e15-113">No .NET Framework 3.0 e 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="81e15-113">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="81e15-114">No .NET Framework 4 e posterior: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="81e15-114">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="81e15-115">**Versão do .NET framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81e15-115">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81e15-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81e15-116">See Also</span></span>  
 [<span data-ttu-id="81e15-117">Referência de API não gerenciada do WPF</span><span class="sxs-lookup"><span data-stu-id="81e15-117">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
