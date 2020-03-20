---
title: Função CreateIDispatchSTAForwarder - Referência de API não gerenciada do WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: e151ffa6eb5f1dc7479c699e0d7f9f3f57833ebd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174713"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="84971-102">Função CreateIDispatchSTAForwarder (referência de API não gerenciada WPF)</span><span class="sxs-lookup"><span data-stu-id="84971-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="84971-103">Esta API suporta a infra-estrutura do Windows Presentation Foundation (WPF) e não se destina a ser usada diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="84971-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="84971-104">Usado pela infra-estrutura do Windows Presentation Foundation (WPF) para gerenciamento de threads e janelas.</span><span class="sxs-lookup"><span data-stu-id="84971-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84971-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84971-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="84971-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="84971-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="84971-107">Valor da propriedade/Valor do retorno</span><span class="sxs-lookup"><span data-stu-id="84971-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="84971-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="84971-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="84971-109">Um ponteiro `IDispatch` para uma interface.</span><span class="sxs-lookup"><span data-stu-id="84971-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="84971-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="84971-110">ppForwarder</span></span>  
 <span data-ttu-id="84971-111">Um ponteiro para o `IDispatch` endereço de uma interface.</span><span class="sxs-lookup"><span data-stu-id="84971-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84971-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="84971-112">Requirements</span></span>  
 <span data-ttu-id="84971-113">**Plataformas:** Consulte [os requisitos do sistema de estrutura .NET](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84971-113">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84971-114">**Dll:**</span><span class="sxs-lookup"><span data-stu-id="84971-114">**DLL:**</span></span>  
  
 <span data-ttu-id="84971-115">No quadro .NET 3.0 e 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="84971-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="84971-116">No Quadro .NET 4 e posteriores: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="84971-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="84971-117">**.NET Framework Version:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84971-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84971-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="84971-118">See also</span></span>

- [<span data-ttu-id="84971-119">Referência de API não gerenciada do WPF</span><span class="sxs-lookup"><span data-stu-id="84971-119">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
