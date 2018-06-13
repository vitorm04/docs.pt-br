---
title: s_isDebuggerCheckDisabledForTestPurposes campo
ms.date: 03/30/2017
ms.technology:
- dotnet-wpf
api_name:
- System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location:
- PresentationCore.dll
api_type:
- Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
robots: noindex,nofollow
ms.openlocfilehash: fbbd8d33ea163efaad1417ab4a1435df729e4897
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752190"
---
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a>s_isDebuggerCheckDisabledForTestPurposes campo

Este campo privado no `System.Windows.Diagnostics.VisualDiagnostics` pelo Visual Studio, a classe é usada para determinar se uma verificação interna de um depurador ativo será executada.

## <a name="syntax"></a>Sintaxe
  
```csharp  
private static bool s_isDebuggerCheckDisabledForTestPurposes
```
  
> [!WARNING]
>  API no `System.Windows.Diagnostics.VisualDiagnostics` classe estão disponíveis somente quando um aplicativo está em execução em um depurador. Definir `s_isDebuggerCheckDisabledForTestPurposes` para `true` para acessar as APIs fora de um depurador.  
>   
>  Microsoft não suporta o uso desse campo em um aplicativo de produção sob nenhuma circunstância.  

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Windows.Diagnostics>

**Assembly:** PresentationCore (em PresentationCore.dll)

**Versões do .NET framework:** disponível desde o 4.6.
