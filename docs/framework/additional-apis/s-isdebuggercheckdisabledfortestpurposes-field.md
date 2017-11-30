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
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a><span data-ttu-id="fc381-102">s_isDebuggerCheckDisabledForTestPurposes campo</span><span class="sxs-lookup"><span data-stu-id="fc381-102">s_isDebuggerCheckDisabledForTestPurposes Field</span></span>

<span data-ttu-id="fc381-103">Este campo privado no `System.Windows.Diagnostics.VisualDiagnostics` pelo Visual Studio, a classe é usada para determinar se uma verificação interna de um depurador ativo será executada.</span><span class="sxs-lookup"><span data-stu-id="fc381-103">This private field in the `System.Windows.Diagnostics.VisualDiagnostics` class is used by Visual Studio to determine whether an internal check for an active debugger will be performed.</span></span>

## <a name="syntax"></a><span data-ttu-id="fc381-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc381-104">Syntax</span></span>
  
```csharp  
private static bool s_isDebuggerCheckDisabledForTestPurposes
```
  
> [!WARNING]
>  <span data-ttu-id="fc381-105">API no `System.Windows.Diagnostics.VisualDiagnostics` classe estão disponíveis somente quando um aplicativo está em execução em um depurador.</span><span class="sxs-lookup"><span data-stu-id="fc381-105">API's in the `System.Windows.Diagnostics.VisualDiagnostics` class are only available when an application is running under a debugger.</span></span> <span data-ttu-id="fc381-106">Definir `s_isDebuggerCheckDisabledForTestPurposes` para `true` para acessar as APIs fora de um depurador.</span><span class="sxs-lookup"><span data-stu-id="fc381-106">Set `s_isDebuggerCheckDisabledForTestPurposes` to `true` to access the APIs outside of a debugger.</span></span>  
>   
>  <span data-ttu-id="fc381-107">Microsoft não suporta o uso desse campo em um aplicativo de produção sob nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="fc381-107">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>  

## <a name="requirements"></a><span data-ttu-id="fc381-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fc381-108">Requirements</span></span>

<span data-ttu-id="fc381-109">**Namespace:**<xref:System.Windows.Diagnostics></span><span class="sxs-lookup"><span data-stu-id="fc381-109">**Namespace:** <xref:System.Windows.Diagnostics></span></span>

<span data-ttu-id="fc381-110">**Assembly:** PresentationCore (em PresentationCore.dll)</span><span class="sxs-lookup"><span data-stu-id="fc381-110">**Assembly:** PresentationCore (in PresentationCore.dll)</span></span>

<span data-ttu-id="fc381-111">**Versões do .NET framework:** disponível desde o 4.6.</span><span class="sxs-lookup"><span data-stu-id="fc381-111">**.NET Framework versions:** Available since 4.6.</span></span>
