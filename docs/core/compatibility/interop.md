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
# <a name="interop-breaking-changes"></a>Alterações significativas de interoperabilidade

As seguintes alterações significativas estão documentadas nesta página:

| Alteração significativa | Versão introduzida |
| - | :-: |
| [A conversão de RCW em uma `InterfaceIsIInspectable` interface gera PlatformNotSupportedException](#casting-rcw-to-an-interfaceisiinspectable-interface-throws-platformnotsupportedexception) | 5,0 |
| [Nenhuma investigação de sufixo A/W em plataformas não Windows](#no-aw-suffix-probing-on-non-windows-platforms) | 5,0 |
| [O suporte interno para o WinRT é removido do .NET](#built-in-support-for-winrt-is-removed-from-net) | 5,0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [casting-rcw-to-inspectable-interface-throws-exception](../../../includes/core-changes/interop/5.0/casting-rcw-to-inspectable-interface-throws-exception.md)]

***

[!INCLUDE [function-suffix-pinvoke](../../../includes/core-changes/interop/5.0/function-suffix-pinvoke.md)]

***

[!INCLUDE [built-in-support-for-winrt-removed](~/includes/core-changes/interop/5.0/built-in-support-for-winrt-removed.md)]

***
