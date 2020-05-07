---
title: Alterações de quebra de rede
description: Lista as alterações significativas na rede no .NET Core.
ms.date: 05/05/2020
ms.openlocfilehash: 07e0b2e062ce244cd6312bbe08bcc63db4c74347
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859625"
---
# <a name="networking-breaking-changes"></a>Alterações de quebra de rede

As seguintes alterações significativas estão documentadas nesta página:

| Alteração significativa | Versão introduzida |
| - | - |
| [Valor padrão de HttpRequestMessage. Version alterado para 1,1](#default-value-of-httprequestmessageversion-changed-to-11) | 3.0 |
| [WebClient. CancelAsync nem sempre cancela imediatamente](#webclientcancelasync-doesnt-always-cancel-immediately) | 2,0 |

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a>.NET Core 2.0

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
