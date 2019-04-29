---
title: Campo de s_isDebuggerCheckDisabledForTestPurposes
ms.date: 03/30/2017
ms.technology: dotnet-wpf
topic_type:
- apiref
api_name:
- System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location:
- PresentationCore.dll
api_type:
- Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
ms.openlocfilehash: ab71ab6aa2b0ed454b86388ba369204a2131cca5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705994"
---
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a>Campo de s_isDebuggerCheckDisabledForTestPurposes

Esse campo particular no `System.Windows.Diagnostics.VisualDiagnostics` classe é usada pelo Visual Studio para determinar se uma verificação interna de um depurador ativo será executada.

## <a name="syntax"></a>Sintaxe

```csharp
private static bool s_isDebuggerCheckDisabledForTestPurposes
```

> [!WARNING]
> APIs no `System.Windows.Diagnostics.VisualDiagnostics` classe só estão disponíveis quando um aplicativo está em execução em um depurador. Definir `s_isDebuggerCheckDisabledForTestPurposes` para `true` para acessar as APIs fora de um depurador.
>
> Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Windows.Diagnostics>

**Assembly:** PresentationCore (em PresentationCore. dll)

**Versões do .NET framework:** Disponível desde o 4.6.