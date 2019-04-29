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
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a><span data-ttu-id="da8e7-102">Campo de s_isDebuggerCheckDisabledForTestPurposes</span><span class="sxs-lookup"><span data-stu-id="da8e7-102">s_isDebuggerCheckDisabledForTestPurposes Field</span></span>

<span data-ttu-id="da8e7-103">Esse campo particular no `System.Windows.Diagnostics.VisualDiagnostics` classe é usada pelo Visual Studio para determinar se uma verificação interna de um depurador ativo será executada.</span><span class="sxs-lookup"><span data-stu-id="da8e7-103">This private field in the `System.Windows.Diagnostics.VisualDiagnostics` class is used by Visual Studio to determine whether an internal check for an active debugger will be performed.</span></span>

## <a name="syntax"></a><span data-ttu-id="da8e7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da8e7-104">Syntax</span></span>

```csharp
private static bool s_isDebuggerCheckDisabledForTestPurposes
```

> [!WARNING]
> <span data-ttu-id="da8e7-105">APIs no `System.Windows.Diagnostics.VisualDiagnostics` classe só estão disponíveis quando um aplicativo está em execução em um depurador.</span><span class="sxs-lookup"><span data-stu-id="da8e7-105">APIs in the `System.Windows.Diagnostics.VisualDiagnostics` class are only available when an application is running under a debugger.</span></span> <span data-ttu-id="da8e7-106">Definir `s_isDebuggerCheckDisabledForTestPurposes` para `true` para acessar as APIs fora de um depurador.</span><span class="sxs-lookup"><span data-stu-id="da8e7-106">Set `s_isDebuggerCheckDisabledForTestPurposes` to `true` to access the APIs outside of a debugger.</span></span>
>
> <span data-ttu-id="da8e7-107">Microsoft não suporta o uso deste campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="da8e7-107">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="da8e7-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da8e7-108">Requirements</span></span>

<span data-ttu-id="da8e7-109">**Namespace:** <xref:System.Windows.Diagnostics></span><span class="sxs-lookup"><span data-stu-id="da8e7-109">**Namespace:** <xref:System.Windows.Diagnostics></span></span>

<span data-ttu-id="da8e7-110">**Assembly:** PresentationCore (em PresentationCore. dll)</span><span class="sxs-lookup"><span data-stu-id="da8e7-110">**Assembly:** PresentationCore (in PresentationCore.dll)</span></span>

<span data-ttu-id="da8e7-111">**Versões do .NET framework:** Disponível desde o 4.6.</span><span class="sxs-lookup"><span data-stu-id="da8e7-111">**.NET Framework versions:** Available since 4.6.</span></span>