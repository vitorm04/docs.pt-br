---
title: "Função LoadFromHistory (referência de API não gerenciada WPF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: LoadFromHistory
api_location: PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cdb68700ab0c11bbd6b09b83a826dc5ca4faa086
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="6f636-102">Função LoadFromHistory (referência de API não gerenciada WPF)</span><span class="sxs-lookup"><span data-stu-id="6f636-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="6f636-103">Essa API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="6f636-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="6f636-104">Usado pela infraestrutura do Windows Presentation Foundation (WPF) para o gerenciamento do windows.</span><span class="sxs-lookup"><span data-stu-id="6f636-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f636-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f636-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f636-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6f636-106">Parameters</span></span>  
 <span data-ttu-id="6f636-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="6f636-107">pHistoryStream</span></span>  
 <span data-ttu-id="6f636-108">Um ponteiro para um fluxo de informações de histórico.</span><span class="sxs-lookup"><span data-stu-id="6f636-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="6f636-109">pBindCtx</span><span class="sxs-lookup"><span data-stu-id="6f636-109">pBindCtx</span></span>  
 <span data-ttu-id="6f636-110">Um ponteiro para um contexto de associação.</span><span class="sxs-lookup"><span data-stu-id="6f636-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f636-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6f636-111">Requirements</span></span>  
 <span data-ttu-id="6f636-112">**Plataformas:** consulte [requisitos de sistema do .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f636-112">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f636-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="6f636-113">**DLL:**</span></span>  
  
 <span data-ttu-id="6f636-114">No .NET Framework 3.0 e 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="6f636-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="6f636-115">No .NET Framework 4 e posterior: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="6f636-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="6f636-116">**Versão do .NET framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f636-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f636-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f636-117">See Also</span></span>  
 [<span data-ttu-id="6f636-118">Referência de API não gerenciada do WPF</span><span class="sxs-lookup"><span data-stu-id="6f636-118">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
