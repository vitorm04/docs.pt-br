---
title: Ativar a função (referência de API não gerenciada WPF)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Acrivate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: 6410b05a1b858a7b75c9bff3220d47505beabd7c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357268"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="e2384-102">Ativar a função (referência de API não gerenciada WPF)</span><span class="sxs-lookup"><span data-stu-id="e2384-102">Activate Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="e2384-103">Essa API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="e2384-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="e2384-104">Usado pela infraestrutura do Windows Presentation Foundation (WPF) para gerenciamento do windows.</span><span class="sxs-lookup"><span data-stu-id="e2384-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2384-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e2384-105">Syntax</span></span>  
  
```cpp  
void Activate(  
    const ActivateParameters* pParameters,  
    __deref_out_ecount(1) LPUNKNOWN* ppInner,  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2384-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e2384-106">Parameters</span></span>  
 <span data-ttu-id="e2384-107">pParameters</span><span class="sxs-lookup"><span data-stu-id="e2384-107">pParameters</span></span>  
 <span data-ttu-id="e2384-108">Um ponteiro para os parâmetros de ativação da janela.</span><span class="sxs-lookup"><span data-stu-id="e2384-108">A pointer to the window's activation parameters.</span></span>  
  
 <span data-ttu-id="e2384-109">ppInner</span><span class="sxs-lookup"><span data-stu-id="e2384-109">ppInner</span></span>  
 <span data-ttu-id="e2384-110">Um ponteiro para o endereço de um buffer de elemento único que contém um ponteiro para um <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> objeto.</span><span class="sxs-lookup"><span data-stu-id="e2384-110">A pointer to the address of a single-element buffer that contains a pointer to an <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2384-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e2384-111">Requirements</span></span>  
 <span data-ttu-id="e2384-112">**Plataformas:** Ver [requisitos de sistema do .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2384-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2384-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="e2384-113">**DLL:**</span></span>  
  
 <span data-ttu-id="e2384-114">No .NET Framework 3.0 e 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="e2384-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="e2384-115">No .NET Framework 4 e posterior: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="e2384-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="e2384-116">**Versão do .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2384-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2384-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2384-117">See also</span></span>
- [<span data-ttu-id="e2384-118">Referência de API não gerenciada do WPF</span><span class="sxs-lookup"><span data-stu-id="e2384-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
