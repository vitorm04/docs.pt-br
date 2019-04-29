---
title: CoreResponseData.m_ResponseHeaders Field
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData.m_ResponseHeaders
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: ea93b70ae8e1a710b4208050d7ec823a28b218b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705968"
---
# <a name="coreresponsedatamresponseheaders-field"></a>CoreResponseData.m\_ResponseHeaders campo

`CoreResponseData.m_ResponseHeaders` é um <xref:System.Net.WebHeaderCollection> de cabeçalhos associados a resposta do servidor.

## <a name="syntax"></a>Sintaxe
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> Essa API não se destina a ser usado diretamente em seu código. Em vez disso, você deve usar um <xref:System.Diagnostics.DiagnosticSource> para capturar o código de rede. Ver [guia do usuário DiagnosticSource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).
> 
> Microsoft não suporta o uso dessa classe em um aplicativo de produção sob nenhuma circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System.Net>

**Assembly:** Sistema (em System. dll)

**Versões do .NET framework:** Disponível desde o 2.0.
