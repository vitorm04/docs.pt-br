---
title: Alterações significativas de interoperabilidade
description: Lista as alterações significativas na interoperabilidade no .NET Core e no .NET 5,0 e posterior.
ms.date: 06/23/2020
ms.openlocfilehash: a38fb1837e565be33f8ae1119480c8f1ae848ab0
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91438035"
---
# <a name="interop-breaking-changes"></a><span data-ttu-id="d1424-103">Alterações significativas de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="d1424-103">Interop breaking changes</span></span>

<span data-ttu-id="d1424-104">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="d1424-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="d1424-105">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="d1424-105">Breaking change</span></span> | <span data-ttu-id="d1424-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="d1424-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="d1424-107">A conversão de RCW em uma `InterfaceIsIInspectable` interface gera PlatformNotSupportedException</span><span class="sxs-lookup"><span data-stu-id="d1424-107">Casting RCW to an `InterfaceIsIInspectable` interface throws PlatformNotSupportedException</span></span>](#casting-rcw-to-an-interfaceisiinspectable-interface-throws-platformnotsupportedexception) | <span data-ttu-id="d1424-108">5,0</span><span class="sxs-lookup"><span data-stu-id="d1424-108">5.0</span></span> |
| [<span data-ttu-id="d1424-109">Nenhuma investigação de sufixo A/W em plataformas não Windows</span><span class="sxs-lookup"><span data-stu-id="d1424-109">No A/W suffix probing on non-Windows platforms</span></span>](#no-aw-suffix-probing-on-non-windows-platforms) | <span data-ttu-id="d1424-110">5,0</span><span class="sxs-lookup"><span data-stu-id="d1424-110">5.0</span></span> |
| [<span data-ttu-id="d1424-111">O suporte interno para o WinRT é removido do .NET</span><span class="sxs-lookup"><span data-stu-id="d1424-111">Built-in support for WinRT is removed from .NET</span></span>](#built-in-support-for-winrt-is-removed-from-net) | <span data-ttu-id="d1424-112">5,0</span><span class="sxs-lookup"><span data-stu-id="d1424-112">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="d1424-113">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="d1424-113">.NET 5.0</span></span>

[!INCLUDE [casting-rcw-to-inspectable-interface-throws-exception](../../../includes/core-changes/interop/5.0/casting-rcw-to-inspectable-interface-throws-exception.md)]

***

[!INCLUDE [function-suffix-pinvoke](../../../includes/core-changes/interop/5.0/function-suffix-pinvoke.md)]

***

[!INCLUDE [built-in-support-for-winrt-removed](~/includes/core-changes/interop/5.0/built-in-support-for-winrt-removed.md)]

***
