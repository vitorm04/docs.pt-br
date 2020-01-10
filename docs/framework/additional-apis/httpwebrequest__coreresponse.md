---
title: Campo HttpWebRequest. _CoreResponse
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._CoreResponse
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: d16936f6984e73a886f5f48e05b53501ced63c1b
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740451"
---
# <a name="httpwebrequest_coreresponse-field"></a>HttpWebRequest.\_campo CoreResponse

`HttpWebRequest._CoreResponse` é um objeto (um [CoreResponseData](coreresponsedata.md) ou um <xref:System.Exception>) que contém o resultado da análise de resposta http.

## <a name="syntax"></a>Sintaxe
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> Essa API não deve ser usada diretamente no seu código. Em vez disso, você deve usar um <xref:System.Diagnostics.DiagnosticSource> para conectar o código de rede. Consulte o [Guia do usuário do diagnosticm](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).
> 
> A Microsoft não oferece suporte ao uso dessa classe em um aplicativo de produção em nenhuma circunstância.

## <a name="requirements"></a>Requisitos do

**Namespace:** <xref:System.Net>

**Assembly:** Sistema (em System. dll)

**.NET Framework versões:** Disponível desde 2,0.
