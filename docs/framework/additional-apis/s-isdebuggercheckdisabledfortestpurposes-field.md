---
title: Campo de s_isDebuggerCheckDisabledForTestPurposes
ms.date: 03/30/2017
ms.technology:
- dotnet-wpf
topic_type:
- apiref
api_name:
- System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location:
- PresentationCore.dll
api_type:
- Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
ms.openlocfilehash: b6490919163a7c4a618bf9a8d0e2aa145f60eda1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372302"
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