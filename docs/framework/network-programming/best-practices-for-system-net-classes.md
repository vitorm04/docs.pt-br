---
title: "Melhores práticas para classes System.Net"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sending data, best practices
- requesting data from Internet, best practices
- WebRequest class, best practices
- data requests, best practices
- WebResponse class, best practices
- best practices, data requests
- receiving data, best practices
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 90722abbdb4568be115c0ac77007d5f18984df6f
ms.sourcegitcommit: 32172ca05d5dcce7ef3d327b9c8639c736e0fe2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2018
---
# <a name="best-practices-for-systemnet-classes"></a>Melhores práticas para classes System.Net
As seguintes recomendações ajudarão você a usar as classes contidas em <xref:System.Net> para seu melhor proveito:  
  
-   Para práticas recomendadas de segurança de camada de transporte (TLS), consulte [segurança de camada de transporte (TLS) práticas recomendadas com o .NET Framework](tls.md).

-   Use <xref:System.Net.WebRequest> e <xref:System.Net.WebResponse> sempre que possível, em vez da conversão de tipo para classes descendentes. Os aplicativos que usam **WebRequest** e **WebResponse** podem aproveitar os novos protocolos da Internet sem a necessidade de alterações de código extensas.  
  
-   Ao escrever aplicativos ASP.NET executados em um servidor usando as classes **System.Net**, geralmente é melhor, de um ponto de vista de desempenho, usar os métodos assíncronos para <xref:System.Net.WebRequest.GetResponse%2A> e <xref:System.Net.WebResponse.GetResponseStream%2A>.  
  
-   O número de conexões abertas para um recurso da Internet pode ter um impacto significativo no desempenho da rede e na taxa de transferência. **System.Net** usa duas conexões por aplicativo e host, por padrão. A configuração da propriedade <xref:System.Net.ServicePoint.ConnectionLimit%2A> no <xref:System.Net.ServicePoint> para o aplicativo pode aumentar esse número para um host específico. A configuração da propriedade <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> pode aumentar esse padrão para todos os hosts.  
  
-   Ao gravar protocolos no nível do soquete, tente usar <xref:System.Net.Sockets.TcpClient> ou <xref:System.Net.Sockets.UdpClient> sempre que possível, em vez de gravar diretamente em um <xref:System.Net.Sockets.Socket>. Essas duas classes de cliente encapsulam a criação de soquetes TCP e UDP sem a necessidade de lidar com os detalhes da conexão.  
  
-   Ao acessar sites que exigem credenciais, use a classe <xref:System.Net.CredentialCache> para criar um cache de credenciais, em vez de fornecê-las com cada solicitação. A classe **CredentialCache** procura o cache para localizar as credenciais apropriadas a serem apresentadas com uma solicitação, liberando-o da responsabilidade de criar e apresentar credenciais baseadas na URL.  
  
## <a name="see-also"></a>Consulte também  
 [Programação de rede no .NET Framework](../../../docs/framework/network-programming/index.md)
