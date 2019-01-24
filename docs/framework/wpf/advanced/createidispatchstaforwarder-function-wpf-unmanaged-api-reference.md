---
title: Função CreateIDispatchSTAForwarder (referência de API não gerenciada WPF)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: 215f6ff727b814e7e7d7c708c29a8c5221f5797f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575969"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="c52cd-102">Função CreateIDispatchSTAForwarder (referência de API não gerenciada WPF)</span><span class="sxs-lookup"><span data-stu-id="c52cd-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="c52cd-103">Essa API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="c52cd-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="c52cd-104">Usado pela infraestrutura do Windows Presentation Foundation (WPF) para gerenciamento de thread e do windows.</span><span class="sxs-lookup"><span data-stu-id="c52cd-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c52cd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c52cd-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c52cd-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c52cd-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="c52cd-107">Valor da propriedade/valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c52cd-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="c52cd-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="c52cd-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="c52cd-109">Um ponteiro para um `IDispatch` interface.</span><span class="sxs-lookup"><span data-stu-id="c52cd-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="c52cd-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="c52cd-110">ppForwarder</span></span>  
 <span data-ttu-id="c52cd-111">Um ponteiro para o endereço de um `IDispatch` interface.</span><span class="sxs-lookup"><span data-stu-id="c52cd-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c52cd-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c52cd-112">Requirements</span></span>  
 <span data-ttu-id="c52cd-113">**Plataformas:** Ver [requisitos de sistema do .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c52cd-113">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c52cd-114">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="c52cd-114">**DLL:**</span></span>  
  
 <span data-ttu-id="c52cd-115">No .NET Framework 3.0 e 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="c52cd-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="c52cd-116">No .NET Framework 4 e posterior: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="c52cd-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="c52cd-117">**Versão do .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c52cd-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c52cd-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c52cd-118">See also</span></span>
- [<span data-ttu-id="c52cd-119">Referência de API não gerenciada do WPF</span><span class="sxs-lookup"><span data-stu-id="c52cd-119">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
