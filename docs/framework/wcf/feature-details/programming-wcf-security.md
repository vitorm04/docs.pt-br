---
title: Programação de segurança do WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
ms.openlocfilehash: 1e82fbb266d3789a8d34109c66d9ee1d8a93c70c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463818"
---
# <a name="programming-wcf-security"></a>Programação de segurança do WCF
Este tópico descreve as tarefas fundamentais de programação usadas para criar um aplicativo seguro da Windows Communication Foundation (WCF). Este tópico abrange apenas autenticação, confidencialidade e integridade, coletivamente conhecida como *segurança de transferência.* Este tópico não abrange a autorização (o controle do acesso a recursos ou serviços); para obter informações sobre autorização, consulte [Autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
> [!NOTE]
> Para uma introdução valiosa aos conceitos de segurança, especialmente no que diz respeito ao WCF, consulte o conjunto de tutoriais de padrões e práticas sobre MSDN em [Cenários, Padrões e Orientação de Implementação para Aprimoramentos de Serviços Web (WSE) 3.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff648183(v=pandp.10)).  
  
 A programação da segurança do WCF é baseada em três etapas que configuram o seguinte: o modo de segurança, um tipo de credencial do cliente e os valores de credencial. Você pode executar essas etapas através de código ou configuração.  
  
## <a name="setting-the-security-mode"></a>Configuração do modo de segurança  
 A seguir, explica maquetes gerais para programação com o modo de segurança no WCF:  
  
1. Selecione uma das vinculações predefinidas apropriadas aos requisitos do aplicativo. Para obter uma lista das opções de vinculação, consulte [Vinculações fornecidas pelo sistema](../../../../docs/framework/wcf/system-provided-bindings.md). Por padrão, quase todas as vinculações têm a segurança ativada. A única exceção é a <xref:System.ServiceModel.BasicHttpBinding> classe (usando configuração, o [ \<>básicoHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)).  
  
     A vinculação selecionada determina o transporte. Por exemplo, <xref:System.ServiceModel.WSHttpBinding> usa HTTP como transporte; <xref:System.ServiceModel.NetTcpBinding> usa TCP.  
  
2. Selecione um dos modos de segurança para a vinculação. Observe que a vinculação selecionada determina as opções de modo disponíveis. Por exemplo, <xref:System.ServiceModel.WSDualHttpBinding> o não permite segurança de transporte (não é uma opção). Da mesma forma, nem o <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nem o permite a segurança da <xref:System.ServiceModel.NetNamedPipeBinding> mensagem.  
  
     Você tem três opções:  
  
    1. `Transport`  
  
         A segurança de transporte depende do mecanismo que a vinculação selecionada usa. Por exemplo, se `WSHttpBinding` você estiver usando, então o mecanismo de segurança é Secure Sockets Layer (SSL) (também o mecanismo para o protocolo HTTPS). De um modo geral, a principal vantagem da segurança do transporte é que ele oferece um bom throughput, não importa qual transporte você esteja usando. No entanto, ele tem duas limitações: A primeira é que o mecanismo de transporte dita o tipo de credencial usado para autenticar um usuário. Isso é uma desvantagem apenas se um serviço precisar interoperar com outros serviços que exigem diferentes tipos de credenciais. A segunda é que, como a segurança não é aplicada no nível da mensagem, a segurança é implementada de forma hop-by-hop em vez de de ponta a ponta. Esta última limitação é um problema apenas se o caminho de mensagem entre cliente e serviço incluir intermediários. Para obter mais informações sobre qual transporte usar, consulte [Escolhendo um Transporte](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Para obter mais informações sobre o uso da segurança de transporte, consulte [Visão geral da segurança do transporte](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).  
  
    2. `Message`  
  
         A segurança das mensagens significa que cada mensagem inclui os cabeçalhos e dados necessários para manter a mensagem segura. Como a composição dos cabeçalhos varia, você pode incluir qualquer número de credenciais. Isso se torna um fator se você estiver interoperando com outros serviços que exigem um tipo de credencial específico que um mecanismo de transporte não pode fornecer, ou se a mensagem deve ser usada com mais de um serviço, onde cada serviço exige um tipo de credencial diferente.  
  
         Para obter mais informações, consulte [Segurança de mensagens](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
    3. `TransportWithMessageCredential`  
  
         Essa escolha usa a camada de transporte para garantir a transferência de mensagens, enquanto cada mensagem inclui as credenciais ricas que outros serviços precisam. Isso combina a vantagem de desempenho da segurança de transporte com as ricas credenciais de vantagem da segurança de mensagens. Isto está disponível com <xref:System.ServiceModel.BasicHttpBinding> <xref:System.ServiceModel.WSFederationHttpBinding>as <xref:System.ServiceModel.NetPeerTcpBinding>seguintes ligações: , , e <xref:System.ServiceModel.WSHttpBinding>.  
  
3. Se você decidir usar a segurança de transporte para HTTP (em outras palavras, HTTPS), você também deve configurar o host com um certificado SSL e ativar o SSL em uma porta. Para obter mais informações, consulte [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
4. Se você estiver <xref:System.ServiceModel.WSHttpBinding> usando o e não precisar estabelecer <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> uma `false`sessão segura, defina a propriedade como .  
  
     Uma sessão segura ocorre quando um cliente e um serviço criam um canal usando uma chave simétrica (cliente e servidor usam a mesma chave para o período de uma conversa, até que a caixa de diálogo seja fechada).  
  
## <a name="setting-the-client-credential-type"></a>Configuração do tipo de credencial do cliente  
 Selecione um tipo de credencial do cliente conforme apropriado. Para obter mais informações, consulte [Selecionando um tipo de credencial](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md). Os seguintes tipos de credenciais do cliente estão disponíveis:  
  
- `Windows`  
  
- `Certificate`  
  
- `Digest`  
  
- `Basic`  
  
- `UserName`  
  
- `NTLM`  
  
- `IssuedToken`  
  
 Dependendo de como você definir o modo, você deve definir o tipo de credencial. Por exemplo, se você `wsHttpBinding`tiver selecionado o , e tiver definido o `clientCredentialType` modo como "Mensagem", então `None`você `Windows` `UserName`também `Certificate`pode `IssuedToken`definir o atributo do elemento Mensagem para um dos seguintes valores: , , , , e , como mostrado no exemplo de configuração a seguir.  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>
  </wsHttpBinding>
</bindings>  
</system.serviceModel>  
```  
  
 Ou em código:  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a>Definindo valores de credencial de serviço  
 Depois de selecionar um tipo de credencial do cliente, você deve definir as credenciais reais para o serviço e o cliente usarem. No serviço, as credenciais <xref:System.ServiceModel.Description.ServiceCredentials> são definidas <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> usando a <xref:System.ServiceModel.ServiceHostBase> classe e devolvidas pela propriedade da classe. A vinculação em uso implica o tipo de credencial de serviço, o modo de segurança escolhido e o tipo de credencial do cliente. O código a seguir define um certificado para uma credencial de serviço.  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a>Definindo valores de credencial do cliente  
 No cliente, defina os valores <xref:System.ServiceModel.Description.ClientCredentials> de credencial <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> do cliente <xref:System.ServiceModel.ClientBase%601> usando a classe e devolvido pela propriedade da classe. O código a seguir define um certificado como credencial em um cliente usando o protocolo TCP.  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a>Confira também

- [Programação básica do WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [Cenários comuns de segurança](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
