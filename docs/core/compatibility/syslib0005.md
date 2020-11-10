---
title: Aviso de SYSLIB0005
description: Saiba mais sobre o obsoletion que gera SYSLIB0005 de aviso de tempo de compilação.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 8e5420b5cfaa9515ed7a3ac4472dc5d4e49f5bcb
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94439996"
---
# <a name="syslib0005-the-global-assembly-cache-gac-is-not-supported"></a>SYSLIB0005: não há suporte para o GAC (cache de assembly global)

O .NET Core e o .NET 5,0 e versões posteriores eliminam o conceito do GAC (cache de assembly global) que estava presente no .NET Framework. Para ajudar os desenvolvedores a se afastar dessas APIs, algumas APIs relacionadas ao GAC são marcadas como obsoletas, a partir do .NET 5,0. O uso dessas APIs gera aviso `SYSLIB0005` no momento da compilação.

As seguintes APIs relacionadas ao GAC estão marcadas como obsoletas:

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType>

  Bibliotecas e aplicativos não devem usar a <xref:System.Reflection.Assembly.GlobalAssemblyCache> API para fazer determinações sobre o comportamento de tempo de execução, como sempre retorna `false` no .NET Core e no .NET 5 +.

## <a name="workarounds"></a>Soluções Alternativas

Se seu aplicativo consulta a <xref:System.Reflection.Assembly.GlobalAssemblyCache> propriedade, considere remover a chamada. Se você usar o <xref:System.Reflection.Assembly.GlobalAssemblyCache> valor para escolher entre um "assembly no GAC"-Flow versus um "assembly que não está no GAC"-Flow em tempo de execução, reconsidere se o fluxo ainda faz sentido para um aplicativo .NET 5 +.

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>Confira também

- [Cache de assembly global](../../framework/app-domains/gac.md)
