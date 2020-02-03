---
title: Função CreateIDispatchSTAForwarder – referência de API não gerenciada do WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: 67f2542733fb9c6af197c99ede2bd097ce876b5d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738034"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="d4a21-102">Função CreateIDispatchSTAForwarder (referência de API não gerenciada do WPF)</span><span class="sxs-lookup"><span data-stu-id="d4a21-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="d4a21-103">Esta API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usada diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="d4a21-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="d4a21-104">Usado pela infraestrutura de Windows Presentation Foundation (WPF) para gerenciamento de threads e do Windows.</span><span class="sxs-lookup"><span data-stu-id="d4a21-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4a21-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d4a21-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4a21-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d4a21-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="d4a21-107">Valor da propriedade/Valor do retorno</span><span class="sxs-lookup"><span data-stu-id="d4a21-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="d4a21-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="d4a21-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="d4a21-109">Um ponteiro para uma interface `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="d4a21-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="d4a21-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="d4a21-110">ppForwarder</span></span>  
 <span data-ttu-id="d4a21-111">Um ponteiro para o endereço de uma interface de `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="d4a21-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4a21-112">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d4a21-112">Requirements</span></span>  
 <span data-ttu-id="d4a21-113">**Plataformas:** Consulte [.NET Framework requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4a21-113">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4a21-114">**DLL**</span><span class="sxs-lookup"><span data-stu-id="d4a21-114">**DLL:**</span></span>  
  
 <span data-ttu-id="d4a21-115">No .NET Framework 3,0 e 3,5: PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="d4a21-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="d4a21-116">No .NET Framework 4 e posterior: PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="d4a21-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="d4a21-117">**Versão do .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4a21-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4a21-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4a21-118">See also</span></span>

- [<span data-ttu-id="d4a21-119">Referência de API não gerenciada do WPF</span><span class="sxs-lookup"><span data-stu-id="d4a21-119">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
