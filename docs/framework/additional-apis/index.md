---
title: Bibliotecas de classes e APIs adicionais
ms.date: 01/29/2018
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: 0aed6f32bbd3ffdc9446e9d17be2d90c62444ee1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053250"
---
# <a name="additional-class-libraries-and-apis"></a>Bibliotecas de classes e APIs adicionais

A .NET Framework está constantemente evoluindo. Para melhorar o desenvolvimento de plataforma cruzada e introduzir novas funcionalidades desde o início, novos recursos são lançados fora de banda (OOB). Este tópico lista os projetos OOB para os quais fornecemos documentação.  
  
Além disso, algumas bibliotecas são direcionadas a plataformas específicas ou implementações do .NET Framework. Por exemplo, a <xref:System.Text.CodePagesEncodingProvider> classe torna codificações de página de código disponíveis para aplicativos UWP desenvolvidos usando o .NET Framework. Este tópico também lista essas bibliotecas.  
  
## <a name="oob-projects"></a>Projetos OOB
  
| Projeto | Descrição |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | Fornece coleções que são thread-safe e têm garantias de que seu conteúdo nunca será alterado. |
| <xref:System.Net.Http.WinHttpHandler> | Fornece um manipulador de mensagens <xref:System.Net.Http.HttpClient> para o com base na interface WinHTTP do Windows. |
| <xref:System.Numerics> | Fornece uma biblioteca de tipos de vetor que podem aproveitar a aceleração baseada em hardware SIMD.| 
| <xref:System.Threading.Tasks.Dataflow> | A Biblioteca de Fluxo de Dados TPL fornece componentes de fluxo de dados para ajudar a aumentar a robustez de aplicativos habilitados para simultaneidade. |  

## <a name="platform-specific-libraries"></a>Bibliotecas específicas da plataforma
  
| Projeto | Descrição |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Estende a <xref:System.Text.EncodingProvider> classe para tornar as codificações de página de código disponíveis para aplicativos direcionados ao plataforma universal do Windows. |  
  
## <a name="private-apis"></a>APIs privadas  

Essas APIs dão suporte à infraestrutura de produto e não se destinam/não têm suporte para uso diretamente do seu código.  
  
| Nome da API |
| -------- |
| [Classe System .net. Connection](connection.md) |
| [Campo de gravação System .net.\_Connection. m](m_writelist.md) |
| [Classe System .net. ConnectionObject](connectiongroup.md) |
| [Campo de conexão do sistema .net.\_connectionlist. m](m_connectionlist.md) |
| [Classe System .net. CoreResponseData](coreresponsedata.md) |
| [Campo System .net. CoreResponseData.\_m ResponseHeaders](coreresponsedata_m_responseheaders.md) |
| [Campo de StatusCode System .net.\_CoreResponseData. m](coreresponsedata_m_statuscode.md) |
| [System .net. HttpWebRequest. \_Campo de redirecionamento](_autoredirects.md) |
| [System .net. HttpWebRequest. \_Campo CoreResponse](httpwebrequest__coreresponse.md) |
| [System .net. HttpWebRequest. \_Campo HttpResponse](_httpresponse.md) |
| [Campo System .net. ConnectionGroupList. m\_](m_connectiongrouplist.md) |
| [Campo System .net. ServicePointManager.\_s do objectpointtable](s_servicepointtable.md) |
| [Campo System. Windows. Diagnostics. VisualDiagnostics.\_s isDebuggerCheckDisabledForTestPurposes](s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [Classe System. Windows. Forms. Design. DataMemberFieldEditor](datamemberfieldeditor-class.md) |
| [Classe System. Windows. Forms. Design. DataMemberListEditor](datamemberlisteditor-class.md) |
  
## <a name="see-also"></a>Consulte também

- [O .NET Framework e lançamentos fora da banda](../get-started/the-net-framework-and-out-of-band-releases.md)
