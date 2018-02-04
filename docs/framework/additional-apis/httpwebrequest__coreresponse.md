---
title: HttpWebRequest._CoreResponse Field
ms.date: 01/29/2018
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._CoreResponse
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.author: stwhi
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: e6493747cf6c894357223f011da026770778e26c
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="httpwebrequestcoreresponse-field"></a>HttpWebRequest. \_CoreResponse campo

`HttpWebRequest._CoreResponse`é um objeto (ou um [CoreResponseData](coreresponsedata.md) ou um <xref:System.Exception>) que contém o resultado da análise de resposta HTTP.

## <a name="syntax"></a>Sintaxe
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> Esta API não é destinada a ser usada diretamente no seu código. Em vez disso, você deve usar um <xref:System.Diagnostics.DiagnosticSource> para capturar o código de rede. Consulte [guia do usuário DiagnosticSource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).
> 
> Microsoft não suporta o uso dessa classe em um aplicativo de produção sob nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Net>

**Assembly:** sistema (em System. dll)

**Versões do .NET framework:** disponível desde o 2.0.
