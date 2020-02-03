---
title: Ativar função-referência de API não gerenciada do WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Activate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: 9c0a235e8b94294ab82da88e43f7446c29739c12
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734503"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="1c27f-102">Ativar função (referência de API não gerenciada do WPF)</span><span class="sxs-lookup"><span data-stu-id="1c27f-102">Activate Function (WPF Unmanaged API Reference)</span></span>

<span data-ttu-id="1c27f-103">Esta API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usada diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="1c27f-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>

<span data-ttu-id="1c27f-104">Usado pela infraestrutura do Windows Presentation Foundation (WPF) para o gerenciamento do Windows.</span><span class="sxs-lookup"><span data-stu-id="1c27f-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>

## <a name="syntax"></a><span data-ttu-id="1c27f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c27f-105">Syntax</span></span>

```cpp
void Activate(
    const ActivateParameters* pParameters,
    __deref_out_ecount(1) LPUNKNOWN* ppInner,
    );
```

## <a name="parameters"></a><span data-ttu-id="1c27f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c27f-106">Parameters</span></span>

`pParameters`\
<span data-ttu-id="1c27f-107">Um ponteiro para os parâmetros de ativação da janela.</span><span class="sxs-lookup"><span data-stu-id="1c27f-107">A pointer to the window's activation parameters.</span></span>

`ppInner`\
<span data-ttu-id="1c27f-108">Um ponteiro para o endereço de um buffer de elemento único que contém um ponteiro para um objeto <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>.</span><span class="sxs-lookup"><span data-stu-id="1c27f-108">A pointer to the address of a single-element buffer that contains a pointer to an <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> object.</span></span>

## <a name="requirements"></a><span data-ttu-id="1c27f-109">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="1c27f-109">Requirements</span></span>

<span data-ttu-id="1c27f-110">**Plataformas:** Consulte [.NET Framework requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c27f-110">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="1c27f-111">**DLL**</span><span class="sxs-lookup"><span data-stu-id="1c27f-111">**DLL:**</span></span>

<span data-ttu-id="1c27f-112">No .NET Framework 3,0 e 3,5: PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="1c27f-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>

<span data-ttu-id="1c27f-113">No .NET Framework 4 e posterior: PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="1c27f-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>

<span data-ttu-id="1c27f-114">**Versão do .NET Framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c27f-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1c27f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c27f-115">See also</span></span>

- [<span data-ttu-id="1c27f-116">Referência de API não gerenciada do WPF</span><span class="sxs-lookup"><span data-stu-id="1c27f-116">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
