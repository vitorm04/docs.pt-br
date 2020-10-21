---
title: Aviso de SYSLIB0010
description: Saiba mais sobre o obsoletions que gera SYSLIB0010 de aviso de tempo de compilação.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: dcd331aa5c68381ea29848bc54ee4b1a5e75330d
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333201"
---
# <a name="syslib0010-unsupported-remoting-apis"></a>SYSLIB0010: APIs de comunicação remota sem suporte

A [comunicação remota do .net](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) é uma tecnologia herdada, e a infraestrutura existe somente no .NET Framework. As seguintes APIs relacionadas a comunicação remota são marcadas como obsoletas, a partir do .NET 5,0. Usá-los no código gera aviso `SYSLIB0010` no momento da compilação.

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType>

## <a name="workaround"></a>Solução alternativa

Considere usar o WCF ou serviços REST baseados em HTTP para se comunicar com objetos em outros aplicativos ou entre computadores. Para obter mais informações, consulte [.NET Framework Technologies indisponíveis no .NET Core](../porting/net-framework-tech-unavailable.md).

## <a name="see-also"></a>Consulte também

- [Comunicação remota do .NET](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))
