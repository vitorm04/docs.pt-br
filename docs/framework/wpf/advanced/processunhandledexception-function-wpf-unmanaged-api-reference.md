---
title: Função ProcessUnhandledException (referência de API não gerenciada WPF)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: bcde3fe6d3fdc1749f29a5c9f7625f802dd49535
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544518"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="8fdb3-102">Função ProcessUnhandledException (referência de API não gerenciada WPF)</span><span class="sxs-lookup"><span data-stu-id="8fdb3-102">ProcessUnhandledException Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="8fdb3-103">Essa API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="8fdb3-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="8fdb3-104">Usado pela infraestrutura do Windows Presentation Foundation (WPF) para manipulação de exceção.</span><span class="sxs-lookup"><span data-stu-id="8fdb3-104">Used by the Windows Presentation Foundation (WPF) infrastructure for exception handling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fdb3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8fdb3-105">Syntax</span></span>  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8fdb3-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8fdb3-106">Parameters</span></span>  
 <span data-ttu-id="8fdb3-107">errorMsg</span><span class="sxs-lookup"><span data-stu-id="8fdb3-107">errorMsg</span></span>  
 <span data-ttu-id="8fdb3-108">A mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="8fdb3-108">The error message.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fdb3-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8fdb3-109">Requirements</span></span>  
 <span data-ttu-id="8fdb3-110">**Plataformas:** consulte [requisitos de sistema do .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fdb3-110">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fdb3-111">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="8fdb3-111">**DLL:**</span></span>  
  
 <span data-ttu-id="8fdb3-112">No .NET Framework 3.0 e 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="8fdb3-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="8fdb3-113">No .NET Framework 4 e posterior: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="8fdb3-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="8fdb3-114">**Versão do .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fdb3-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fdb3-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8fdb3-115">See Also</span></span>  
 [<span data-ttu-id="8fdb3-116">Referência de API não gerenciada do WPF</span><span class="sxs-lookup"><span data-stu-id="8fdb3-116">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
