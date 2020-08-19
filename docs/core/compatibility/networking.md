---
title: Alterações de quebra de rede
description: Lista as alterações significativas na rede no .NET Core.
ms.date: 05/05/2020
ms.openlocfilehash: 5d27f9663a2c1b79610ab002a03beeafa8b2818e
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557952"
---
# <a name="networking-breaking-changes"></a>Alterações de quebra de rede

As seguintes alterações significativas estão documentadas nesta página:

| Alteração significativa | Versão introduzida |
| - | - |
| [MulticastOption. Group não aceita um valor nulo](#multicastoptiongroup-doesnt-accept-a-null-value) | 5.0 |
| [Valor padrão de HttpRequestMessage. Version alterado para 1,1](#default-value-of-httprequestmessageversion-changed-to-11) | 3.0 |
| [WebClient. CancelAsync nem sempre cancela imediatamente](#webclientcancelasync-doesnt-always-cancel-immediately) | 2.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [multicastoption-group-doesnt-accept-null](../../../includes/core-changes/networking/5.0/multicastoption-group-doesnt-accept-null.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a>.NET Core 2.0

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
