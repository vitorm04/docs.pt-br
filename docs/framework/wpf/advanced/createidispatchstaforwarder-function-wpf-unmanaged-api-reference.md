---
title: "Função CreateIDispatchSTAForwarder (referência de API não gerenciada WPF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5139784fdc067c09d032c0bf37114e0eb1caac33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="ec100-102">Função CreateIDispatchSTAForwarder (referência de API não gerenciada WPF)</span><span class="sxs-lookup"><span data-stu-id="ec100-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="ec100-103">Essa API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="ec100-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="ec100-104">Usado pela infraestrutura do Windows Presentation Foundation (WPF) para gerenciamento de thread e windows.</span><span class="sxs-lookup"><span data-stu-id="ec100-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec100-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec100-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec100-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ec100-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="ec100-107">Valor da propriedade/valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ec100-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="ec100-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="ec100-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="ec100-109">Um ponteiro para um `IDispatch` interface.</span><span class="sxs-lookup"><span data-stu-id="ec100-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="ec100-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="ec100-110">ppForwarder</span></span>  
 <span data-ttu-id="ec100-111">Um ponteiro para o endereço de um `IDispatch` interface.</span><span class="sxs-lookup"><span data-stu-id="ec100-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec100-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ec100-112">Requirements</span></span>  
 <span data-ttu-id="ec100-113">**Plataformas:** consulte [requisitos de sistema do .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec100-113">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec100-114">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="ec100-114">**DLL:**</span></span>  
  
 <span data-ttu-id="ec100-115">No .NET Framework 3.0 e 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="ec100-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="ec100-116">No .NET Framework 4 e posterior: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="ec100-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="ec100-117">**Versão do .NET framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec100-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec100-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec100-118">See Also</span></span>  
 [<span data-ttu-id="ec100-119">Referência de API não gerenciada do WPF</span><span class="sxs-lookup"><span data-stu-id="ec100-119">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
