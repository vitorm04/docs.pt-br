---
title: Ativar a função (referência de API não gerenciada WPF)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Activate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: ee231653815bd5ef75d58979034e3b3be9f5ba54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777163"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="24dfb-102">Ativar a função (referência de API não gerenciada WPF)</span><span class="sxs-lookup"><span data-stu-id="24dfb-102">Activate Function (WPF Unmanaged API Reference)</span></span>

<span data-ttu-id="24dfb-103">Essa API dá suporte à infraestrutura do Windows Presentation Foundation (WPF) e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="24dfb-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>

<span data-ttu-id="24dfb-104">Usado pela infraestrutura do Windows Presentation Foundation (WPF) para gerenciamento do windows.</span><span class="sxs-lookup"><span data-stu-id="24dfb-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>

## <a name="syntax"></a><span data-ttu-id="24dfb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="24dfb-105">Syntax</span></span>

```cpp
void Activate(
    const ActivateParameters* pParameters,
    __deref_out_ecount(1) LPUNKNOWN* ppInner,
    );
```

## <a name="parameters"></a><span data-ttu-id="24dfb-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="24dfb-106">Parameters</span></span>

`pParameters`\
<span data-ttu-id="24dfb-107">Um ponteiro para os parâmetros de ativação da janela.</span><span class="sxs-lookup"><span data-stu-id="24dfb-107">A pointer to the window's activation parameters.</span></span>

`ppInner`\
<span data-ttu-id="24dfb-108">Um ponteiro para o endereço de um buffer de elemento único que contém um ponteiro para um <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> objeto.</span><span class="sxs-lookup"><span data-stu-id="24dfb-108">A pointer to the address of a single-element buffer that contains a pointer to an <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> object.</span></span>

## <a name="requirements"></a><span data-ttu-id="24dfb-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="24dfb-109">Requirements</span></span>

<span data-ttu-id="24dfb-110">**Plataformas:** Ver [requisitos de sistema do .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24dfb-110">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="24dfb-111">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="24dfb-111">**DLL:**</span></span>

<span data-ttu-id="24dfb-112">No .NET Framework 3.0 e 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="24dfb-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>

<span data-ttu-id="24dfb-113">No .NET Framework 4 e posterior: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="24dfb-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>

<span data-ttu-id="24dfb-114">**Versão do .NET framework:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24dfb-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="24dfb-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24dfb-115">See also</span></span>

- [<span data-ttu-id="24dfb-116">Referência de API não gerenciada do WPF</span><span class="sxs-lookup"><span data-stu-id="24dfb-116">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
