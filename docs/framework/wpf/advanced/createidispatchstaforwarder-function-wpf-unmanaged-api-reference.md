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
ms.openlocfilehash: c4da322bf779e084f12529d0da6949ef6ada5cf3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379647"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="b61fa-102">Função CreateIDispatchSTAForwarder (referência de API não gerenciada WPF)</span><span class="sxs-lookup"><span data-stu-id="b61fa-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="b61fa-103">Essa API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="b61fa-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="b61fa-104">Usado pela infraestrutura do Windows Presentation Foundation (WPF) para gerenciamento de thread e do windows.</span><span class="sxs-lookup"><span data-stu-id="b61fa-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b61fa-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b61fa-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b61fa-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b61fa-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="b61fa-107">Valor da propriedade/valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b61fa-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="b61fa-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="b61fa-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="b61fa-109">Um ponteiro para um `IDispatch` interface.</span><span class="sxs-lookup"><span data-stu-id="b61fa-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="b61fa-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="b61fa-110">ppForwarder</span></span>  
 <span data-ttu-id="b61fa-111">Um ponteiro para o endereço de um `IDispatch` interface.</span><span class="sxs-lookup"><span data-stu-id="b61fa-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b61fa-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b61fa-112">Requirements</span></span>  
 <span data-ttu-id="b61fa-113">**Plataformas:** Ver [requisitos de sistema do .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b61fa-113">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b61fa-114">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="b61fa-114">**DLL:**</span></span>  
  
 <span data-ttu-id="b61fa-115">No .NET Framework 3.0 e 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="b61fa-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="b61fa-116">No .NET Framework 4 e posterior: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="b61fa-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="b61fa-117">**Versão do .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b61fa-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b61fa-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b61fa-118">See also</span></span>
- [<span data-ttu-id="b61fa-119">Referência de API não gerenciada do WPF</span><span class="sxs-lookup"><span data-stu-id="b61fa-119">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
