---
title: "Criando serviços interoperáveis de perfil básico de WS-I 1.1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6bef68c8ba433e902cfd50e59a3b343e3af08cd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a>Criando serviços interoperáveis de perfil básico de WS-I 1.1
Para configurar um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ponto de extremidade de serviço para interoperabilidade com [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] clientes de serviço Web:  
  
-   Use o <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> tipo como o tipo de associação para o ponto de extremidade de serviço.  
  
-   Não use o retorno de chamada e os recursos de contrato de sessão ou comportamentos de transação em seu ponto de extremidade de serviço  
  
 Opcionalmente, você pode habilitar o suporte para HTTPS e autenticação de cliente de nível de transporte na associação.  
  
 Os seguintes recursos do <xref:System.ServiceModel.BasicHttpBinding> classe exigem a funcionalidade além do WS-I Basic Profile 1.1:  
  
-   Codificação de mensagens do mecanismo de otimização de transmissão (MTOM) de mensagem controlado pelo <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> propriedade. Deixe essa propriedade em seu valor padrão, que é <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> para não usar MTOM.  
  
-   Segurança controlada pelo <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> valor fornece suporte do WS-Security compatível com WS-I Basic Profile 1.0 de segurança. Deixe essa propriedade em seu valor padrão, que é <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> para não usar WS-Security.  
  
 Para tornar os metadados para um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço disponível para [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], use as ferramentas de geração de cliente de serviço Web: [Web Services Description Language Tool (Wsdl.exe)](http://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88), [(ferramenta de descoberta de serviços Web Disco.exe)](http://msdn.microsoft.com/library/acd88078-c581-42bc-94ca-6633e2851979)e o `Add Web Reference` recurso no [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]; você deve habilitar a publicação de metadados. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Publicar pontos de extremidade de metadados](../../../docs/framework/wcf/publishing-metadata-endpoints.md).  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo de código a seguir demonstra como adicionar um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ponto de extremidade que é compatível com [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] clientes de serviço em código e, opcionalmente, em um arquivo de configuração da Web.  
  
### <a name="code"></a>Código  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Interoperabilidade com serviços Web do ASP.NET](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
