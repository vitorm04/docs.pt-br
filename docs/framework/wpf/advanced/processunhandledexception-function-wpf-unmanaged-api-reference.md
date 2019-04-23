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
ms.openlocfilehash: 0c8751454be6e0eed547c38e9d0bc7931abaec3d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196964"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="1834a-102">Função ProcessUnhandledException (referência de API não gerenciada WPF)</span><span class="sxs-lookup"><span data-stu-id="1834a-102">ProcessUnhandledException Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="1834a-103">Essa API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="1834a-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="1834a-104">Usado pela infraestrutura do Windows Presentation Foundation (WPF) para manipulação de exceção.</span><span class="sxs-lookup"><span data-stu-id="1834a-104">Used by the Windows Presentation Foundation (WPF) infrastructure for exception handling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1834a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1834a-105">Syntax</span></span>  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="1834a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1834a-106">Parameters</span></span>  
 <span data-ttu-id="1834a-107">errorMsg</span><span class="sxs-lookup"><span data-stu-id="1834a-107">errorMsg</span></span>  
 <span data-ttu-id="1834a-108">A mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="1834a-108">The error message.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1834a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1834a-109">Requirements</span></span>  
 <span data-ttu-id="1834a-110">**Plataformas:** Ver [requisitos de sistema do .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1834a-110">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1834a-111">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="1834a-111">**DLL:**</span></span>  
  
 <span data-ttu-id="1834a-112">No .NET Framework 3.0 e 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="1834a-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="1834a-113">No .NET Framework 4 e posterior: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="1834a-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="1834a-114">**Versão do .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1834a-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1834a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1834a-115">See also</span></span>

- [<span data-ttu-id="1834a-116">Referência de API não gerenciada do WPF</span><span class="sxs-lookup"><span data-stu-id="1834a-116">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
