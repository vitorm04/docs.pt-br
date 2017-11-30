---
title: s_isDebuggerCheckDisabledForTestPurposes campo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
api_name: System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location: PresentationCore.dll
api_type: Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
robots: noindex,nofollow
ms.openlocfilehash: 97e5d32bff3e3150b56e8d9492aacc40f09f2afe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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

**Namespace:**<xref:System.Windows.Diagnostics>

**Assembly:** PresentationCore (em PresentationCore.dll)

**Versões do .NET framework:** disponível desde o 4.6.
