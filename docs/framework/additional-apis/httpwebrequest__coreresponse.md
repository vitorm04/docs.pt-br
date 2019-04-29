---
title: Campo HttpWebRequest._CoreResponse
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
ms.openlocfilehash: 3627c9bf0d72ccec3a0d6d9c7c89b62f83dcd4b4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706059"
---
# <a name="httpwebrequestcoreresponse-field"></a>HttpWebRequest. \_Campo CoreResponse

`HttpWebRequest._CoreResponse` é um objeto (qualquer um [CoreResponseData](coreresponsedata.md) ou um <xref:System.Exception>) que contém o resultado da análise da resposta HTTP.

## <a name="syntax"></a>Sintaxe
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> Essa API não se destina a ser usado diretamente em seu código. Em vez disso, você deve usar um <xref:System.Diagnostics.DiagnosticSource> para capturar o código de rede. Ver [guia do usuário DiagnosticSource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).
> 
> Microsoft não suporta o uso dessa classe em um aplicativo de produção sob nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Net>

**Assembly:** Sistema (em System. dll)

**Versões do .NET framework:** Disponível desde o 2.0.
