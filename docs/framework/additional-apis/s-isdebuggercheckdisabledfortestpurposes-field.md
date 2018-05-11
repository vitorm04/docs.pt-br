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
---
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a><span data-ttu-id="e9bb3-102">s_isDebuggerCheckDisabledForTestPurposes campo</span><span class="sxs-lookup"><span data-stu-id="e9bb3-102">s_isDebuggerCheckDisabledForTestPurposes Field</span></span>

<span data-ttu-id="e9bb3-103">Este campo privado no `System.Windows.Diagnostics.VisualDiagnostics` pelo Visual Studio, a classe é usada para determinar se uma verificação interna de um depurador ativo será executada.</span><span class="sxs-lookup"><span data-stu-id="e9bb3-103">This private field in the `System.Windows.Diagnostics.VisualDiagnostics` class is used by Visual Studio to determine whether an internal check for an active debugger will be performed.</span></span>

## <a name="syntax"></a><span data-ttu-id="e9bb3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9bb3-104">Syntax</span></span>
  
```csharp  
private static bool s_isDebuggerCheckDisabledForTestPurposes
```
  
> [!WARNING]
>  <span data-ttu-id="e9bb3-105">API no `System.Windows.Diagnostics.VisualDiagnostics` classe estão disponíveis somente quando um aplicativo está em execução em um depurador.</span><span class="sxs-lookup"><span data-stu-id="e9bb3-105">API's in the `System.Windows.Diagnostics.VisualDiagnostics` class are only available when an application is running under a debugger.</span></span> <span data-ttu-id="e9bb3-106">Definir `s_isDebuggerCheckDisabledForTestPurposes` para `true` para acessar as APIs fora de um depurador.</span><span class="sxs-lookup"><span data-stu-id="e9bb3-106">Set `s_isDebuggerCheckDisabledForTestPurposes` to `true` to access the APIs outside of a debugger.</span></span>  
>   
>  <span data-ttu-id="e9bb3-107">Microsoft não suporta o uso desse campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="e9bb3-107">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>  

## <a name="requirements"></a><span data-ttu-id="e9bb3-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e9bb3-108">Requirements</span></span>

<span data-ttu-id="e9bb3-109">**Namespace:** <xref:System.Windows.Diagnostics></span><span class="sxs-lookup"><span data-stu-id="e9bb3-109">**Namespace:** <xref:System.Windows.Diagnostics></span></span>

<span data-ttu-id="e9bb3-110">**Assembly:** PresentationCore (em PresentationCore.dll)</span><span class="sxs-lookup"><span data-stu-id="e9bb3-110">**Assembly:** PresentationCore (in PresentationCore.dll)</span></span>

<span data-ttu-id="e9bb3-111">**Versões do .NET framework:** disponível desde o 4.6.</span><span class="sxs-lookup"><span data-stu-id="e9bb3-111">**.NET Framework versions:** Available since 4.6.</span></span>
