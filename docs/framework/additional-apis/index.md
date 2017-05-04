---
title: Bibliotecas de classes e APIs adicionais | Microsoft Docs
ms.custom: 
ms.date: 04/12/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
caps.latest.revision: 12
author: mairaw
ms.author: mairaw
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: b53b8acc2a6c56db6a9d8a9b7c685a2d400a53e1
ms.openlocfilehash: 34815268b707aa70d174a1bbc04c32276db8412d
ms.lasthandoff: 05/02/2017

---

# <a name="additional-class-libraries-and-apis"></a>Bibliotecas de classes e APIs adicionais

O .NET Framework está em constante evolução e, para melhorar o desenvolvimento multiplataforma e introduzir novas funcionalidades o quanto antes para nossos clientes, lançamos novos recursos OOB (fora de banda). Este tópico lista os projetos OOB para os quais fornecemos documentação.  
  
Além disso, algumas bibliotecas são direcionadas a plataformas específicas ou implementações do .NET Framework. Por exemplo, a classe <xref:System.Text.CodePagesEncodingProvider> disponibiliza as codificações de página de código para aplicativos UWP desenvolvidos usando o .NET Framework. Este tópico também lista essas bibliotecas.  
  
## <a name="oob-projects"></a>Projetos OOB
  
| Projeto | Descrição |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | Fornece coleções que são thread-safe e têm garantias de que seu conteúdo nunca será alterado. |
| <xref:System.Net.Http.WinHttpHandler> | Fornece um manipulador de mensagens para <xref:System.Net.Http.HttpClient> com base na interface WinHTTP do Windows. |
| [System.Numerics.Vectors](https://msdn.microsoft.com/library/mt452176.aspx) | Fornece uma biblioteca de tipos de vetor que podem aproveitar a aceleração baseada em hardware SIMD.| 
| <xref:System.Threading.Tasks.Dataflow> | A Biblioteca de Fluxo de Dados TPL fornece componentes de fluxo de dados para ajudar a aumentar a robustez de aplicativos habilitados para simultaneidade. |  

## <a name="platform-specific-libraries"></a>Bibliotecas específicas da plataforma
  
| Projeto | Descrição |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Estende a classe <xref:System.Text.EncodingProvider> para disponibilizar codificações de página de código a aplicativos direcionados à Plataforma Universal do Windows. |  
  
## <a name="private-apis"></a>APIs privadas  

Essas APIs dão suporte à infraestrutura de produto e não se destinam/não têm suporte para uso diretamente do seu código.  
  
| Nome da API |  
| -------- |  
| [s_isDebuggerCheckDisabledForTestPurposes Field](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |  
| [DataMemberFieldEditor Class](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |  
| [DataMemberListEditor Class](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |  
  
## <a name="see-also"></a>Consulte também

[O .NET Framework e lançamentos fora da banda](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)

