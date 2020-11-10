---
title: Aviso de SYSLIB0008
description: Saiba mais sobre o obsoletion que gera SYSLIB0008 de aviso de tempo de compilação.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 22ac5b4c5f57ec3f92585ee8d1f8cf278a15dbb0
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440589"
---
# <a name="syslib0008-createpdbgenerator-is-not-supported"></a>SYSLIB0008: não há suporte para CreatePdbGenerator

A <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> API está marcada como obsoleta, começando no .net 5,0. O uso dessa API gera aviso `SYSLIB0008` no momento da compilação.

## <a name="suppress-the-warning"></a>Suprimir o aviso

Se você não puder alterar seu código, poderá suprimir o aviso por meio de uma `#pragma` diretiva ou `<NoWarn>` configuração de projeto. Para obter exemplos, consulte [suprimir avisos](syslib-obsoletions.md#suppress-warnings).
