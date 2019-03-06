---
title: Função ForwardTranslateAccelerator (referência de API não gerenciada WPF)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: 02d5d23ec44d9fb7a244fc635ac174cf81ead173
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362182"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="dc54c-102">Função ForwardTranslateAccelerator (referência de API não gerenciada WPF)</span><span class="sxs-lookup"><span data-stu-id="dc54c-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="dc54c-103">Essa API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="dc54c-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="dc54c-104">Usado pela infraestrutura do Windows Presentation Foundation (WPF) para gerenciamento do windows.</span><span class="sxs-lookup"><span data-stu-id="dc54c-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc54c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dc54c-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc54c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc54c-106">Parameters</span></span>  
 <span data-ttu-id="dc54c-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="dc54c-107">pMsg</span></span>  
 <span data-ttu-id="dc54c-108">Um ponteiro para uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="dc54c-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="dc54c-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="dc54c-109">appUnhandled</span></span>  
 <span data-ttu-id="dc54c-110">`true` Quando o aplicativo já tem a oportunidade de manipular a mensagem de entrada, mas não tratada. Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="dc54c-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc54c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dc54c-111">Requirements</span></span>  
 <span data-ttu-id="dc54c-112">**Plataformas:** Ver [requisitos de sistema do .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc54c-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc54c-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="dc54c-113">**DLL:**</span></span>  
  
 <span data-ttu-id="dc54c-114">No .NET Framework 3.0 e 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="dc54c-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="dc54c-115">No .NET Framework 4 e posterior: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="dc54c-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="dc54c-116">**Versão do .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc54c-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc54c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc54c-117">See also</span></span>
- [<span data-ttu-id="dc54c-118">Referência de API não gerenciada do WPF</span><span class="sxs-lookup"><span data-stu-id="dc54c-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
