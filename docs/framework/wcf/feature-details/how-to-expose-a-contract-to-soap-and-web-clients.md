---
title: Como expor um contrato para clientes SOAP e da Web
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
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c04da670c84aaecf3587e6620c70e94c6b7350e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a>Como expor um contrato para clientes SOAP e da Web
Por padrão, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] disponibiliza pontos de extremidade apenas para clientes SOAP. Em [como: criar um serviço básico do WCF Web HTTP](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md), um ponto de extremidade é disponibilizado para clientes SOAP não. Pode haver momentos quando você deseja disponibilizar o mesmo contrato de duas maneiras, como um ponto de extremidade da Web e como um ponto de extremidade SOAP. Este tópico mostra um exemplo de como fazer isso.  
  
### <a name="to-define-the-service-contract"></a>Para definir o contrato de serviço  
  
1.  Definir um contrato de serviço usando uma interface marcada com o <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> e <xref:System.ServiceModel.Web.WebGetAttribute> atributos, como mostrado no código a seguir.  
  
     [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
     [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Por padrão <xref:System.ServiceModel.Web.WebInvokeAttribute> mapeia chamadas POST para a operação. No entanto, você pode especificar o método para mapear para a operação especificando um "método =" parâmetro. <xref:System.ServiceModel.Web.WebGetAttribute> não tem um parâmetro "method=" e só mapeia chamadas GET para a operação de serviço.  
  
2.  Implemente o contrato de serviço, conforme mostrado no código a seguir.  
  
     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]  
  
### <a name="to-host-the-service"></a>Para hospedar o serviço  
  
1.  Criar um <xref:System.ServiceModel.ServiceHost> do objeto, como mostrado no código a seguir.  
  
     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]  
  
2.  Adicionar um <xref:System.ServiceModel.Description.ServiceEndpoint> com <xref:System.ServiceModel.BasicHttpBinding> para o ponto de extremidade SOAP, conforme mostrado no código a seguir.  
  
     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]  
  
3.  Adicionar um <xref:System.ServiceModel.Description.ServiceEndpoint> com <xref:System.ServiceModel.WebHttpBinding> para o ponto de extremidade SOAP não e adicione o <xref:System.ServiceModel.Description.WebHttpBehavior> ao ponto de extremidade, conforme mostrado no código a seguir.  
  
     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]  
  
4.  Chamar `Open()` em um <xref:System.ServiceModel.ServiceHost> instância para abrir o host de serviço, conforme mostrado no código a seguir.  
  
     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]  
  
### <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>Para chamar operações de serviço mapeadas para GET no Internet Explorer  
  
1.  Abra o Internet Explorer e digite "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" e pressione ENTER. A URL contém o endereço básico do serviço ("http://localhost:8000/"), o endereço relativo do ponto de extremidade (""), a operação de serviço a ser chamada ("EchoWithGet") e um ponto de interrogação seguido por uma lista de parâmetros nomeados separados por um E comercial (&).  
  
### <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a>Para chamar operações de serviço no ponto de extremidade da Web no código  
  
1.  Criar uma instância de <xref:System.ServiceModel.Web.WebChannelFactory%601> dentro de um `using` bloquear, conforme mostrado no código a seguir.  
  
     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]  
  
> [!NOTE]
>  `Close()`é chamado automaticamente no canal no final de `using` bloco.  
  
1.  Criar o canal e chamar o serviço, conforme mostrado no código a seguir.  
  
     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]  
  
### <a name="to-call-service-operations-on-the-soap-endpoint"></a>Para chamar operações de serviço no ponto de extremidade SOAP  
  
1.  Criar uma instância de <xref:System.ServiceModel.ChannelFactory> dentro de um `using` bloquear, conforme mostrado no código a seguir.  
  
     [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
     [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]  
  
2.  Criar o canal e chamar o serviço, conforme mostrado no código a seguir.  
  
     [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
     [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]  
  
### <a name="to-close-the-service-host"></a>Para fechar o host de serviço  
  
1.  Feche o host de serviço, conforme mostrado no código a seguir.  
  
     [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
     [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]  
  
## <a name="example"></a>Exemplo  
 Este é o código completo listando deste tópico.  
  
 [!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
 [!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Ao compilar Service.cs, fazer referência a System.ServiceModel.dll e System.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Web.WebServiceHost>  
 <xref:System.ServiceModel.ChannelFactory>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [Modelo de programação WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
