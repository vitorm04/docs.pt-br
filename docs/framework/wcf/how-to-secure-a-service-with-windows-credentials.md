---
title: "Como proteger um serviço com credenciais Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
caps.latest.revision: 
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 6a5225f25ca921407d64f579bbc7c204917ff260
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a>Como proteger um serviço com credenciais Windows
Este tópico mostra como habilitar a segurança de transporte em um [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] serviço que reside em um domínio do Windows e é chamado pelos clientes no mesmo domínio. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Nesse cenário, consulte [segurança de transporte com autenticação do Windows](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md). Para um aplicativo de exemplo, consulte o [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) exemplo.  
  
 Este tópico pressupõe que você tem uma interface de contrato existente e implementação já definida e adiciona o logon que. Você também pode modificar um cliente e serviço existente.  
  
 Você pode proteger um serviço com credenciais do Windows completamente no código. Como alternativa, você pode omitir parte do código usando um arquivo de configuração. Este tópico mostra duas formas. Certifique-se de que você usar apenas uma das maneiras, não ambos.  
  
 Os três primeiros procedimentos mostram como proteger o serviço usando o código. O quarto e quinto procedimento mostra como fazer isso com um arquivo de configuração.  
  
## <a name="using-code"></a>Usando código  
 O código completo para o serviço e o cliente está na seção de exemplo no final deste tópico.  
  
 O primeiro procedimento orienta a criação e configuração de um <xref:System.ServiceModel.WSHttpBinding> classe no código. A associação usa o transporte HTTP. A mesma associação é usada no cliente.  
  
#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a>Para criar um WSHttpBinding que usa credenciais do Windows e segurança de mensagem  
  
1.  Esse código de procedimento é inserido no início do `Run` método o `Test` classe no código de serviço na seção de exemplo.  
  
2.  Crie uma instância da classe <xref:System.ServiceModel.WSHttpBinding>.  
  
3.  Definir o <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> propriedade o <xref:System.ServiceModel.WSHttpSecurity> de classe para <xref:System.ServiceModel.SecurityMode.Message>.  
  
4.  Definir o <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> propriedade o <xref:System.ServiceModel.MessageSecurityOverHttp> de classe para <xref:System.ServiceModel.MessageCredentialType.Windows>.  
  
5.  O código para esse procedimento é o seguinte:  
  
     [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
     [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]  
  
### <a name="using-the-binding-in-a-service"></a>Usando a associação em um serviço  
 Este é o segundo procedimento que mostra como usar a associação em um serviço auto-hospedado. [!INCLUDE[crabout](../../../includes/crabout-md.md)]hospedagem de serviços consulte [serviços de hospedagem](../../../docs/framework/wcf/hosting-services.md).  
  
##### <a name="to-use-a-binding-in-a-service"></a>Para usar uma associação em um serviço  
  
1.  Inserir este código de procedimento após o código do procedimento anterior.  
  
2.  Criar um <xref:System.Type> variável chamada `contractType` e atribua-o tipo da interface (`ICalculator`). Ao usar [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], use o `GetType` operador; ao usar o c#, use o `typeof` palavra-chave.  
  
3.  Crie um segundo `Type` variável chamada `serviceType` e atribua-o tipo do contrato implementado (`Calculator`).  
  
4.  Criar uma instância do <xref:System.Uri> classe denominada `baseAddress` com o endereço base do serviço. O endereço base deve ter um esquema que corresponde o transporte. Nesse caso, o esquema de transporte é HTTP, e o endereço inclui especiais "Localhost" identificador de recurso uniforme (URI) e uma porta de número (8036), bem como um endereço base do ponto de extremidade ("serviceModelSamples /): http://localhost:8036 serviceModelSamples /.  
  
5.  Criar uma instância do <xref:System.ServiceModel.ServiceHost> classe com o `serviceType` e `baseAddress` variáveis.  
  
6.  Adicionar um ponto de extremidade para o serviço usando o `contractType`, associação e um nome de ponto de extremidade (secureCalculator). Um cliente deverá concatenar o endereço base e o nome do ponto de extremidade ao iniciar uma chamada para o serviço.  
  
7.  Chamar o <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> método para iniciar o serviço. O código para esse procedimento é mostrado aqui:  
  
     [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
     [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]  
  
### <a name="using-the-binding-in-a-client"></a>Usando a associação em um cliente  
 Este procedimento mostra como gerar um proxy que se comunica com o serviço. O proxy será gerado com o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) que usa os metadados de serviço para criar o proxy.  
  
 Esse procedimento também cria uma instância do <xref:System.ServiceModel.WSHttpBinding> de classe para se comunicar com o serviço e, em seguida, chama o serviço.  
  
 Este exemplo usa apenas o código para criar o cliente. Como alternativa, você pode usar um arquivo de configuração, que é mostrado na seção a seguir esse procedimento.  
  
##### <a name="to-use-a-binding-in-a-client-with-code"></a>Para usar uma associação em um cliente com o código  
  
1.  Use a ferramenta SvcUtil.exe para gerar o código de proxy de metadados do serviço. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Como: criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). O código de proxy gerado herda o <xref:System.ServiceModel.ClientBase%601> classe, que garante que cada cliente tem a necessário construtores, métodos e propriedades para se comunicar com um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço. Neste exemplo, o código gerado inclui o `CalculatorClient` de classe que implementa o `ICalculator` interface, habilitando a compatibilidade com o código de serviço.  
  
2.  Esse código de procedimento é inserido no início de `Main` método do programa cliente.  
  
3.  Criar uma instância do <xref:System.ServiceModel.WSHttpBinding> de classe e defina o modo de segurança `Message` e seu tipo de credencial de cliente `Windows`. O exemplo de nomes de variável `clientBinding`.  
  
4.  Criar uma instância do <xref:System.ServiceModel.EndpointAddress> classe denominada `serviceAddress`. Inicialize a instância com o endereço base concatenado com o nome do ponto de extremidade.  
  
5.  Criar uma instância da classe cliente gerada com o `serviceAddress` e `clientBinding` variáveis.  
  
6.  Chamar o <xref:System.ServiceModel.ClientBase%601.Open%2A> método, conforme mostrado no código a seguir.  
  
7.  Chamar o serviço e exibir os resultados.  
  
     [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
     [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]  
  
## <a name="using-the-configuration-file"></a>Usando o arquivo de configuração  
 Em vez de criar a associação com o código de procedimento, você pode usar o seguinte código mostrado na seção de associações de arquivo de configuração.  
  
 Se você ainda não tiver um serviço definido, consulte [Projetando e Implementando serviços](../../../docs/framework/wcf/designing-and-implementing-services.md), e [Configurando os serviços de](../../../docs/framework/wcf/configuring-services.md).  
  
 **Observação** este código de configuração é usado em arquivos de configuração do serviço e o cliente.  
  
#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a>Para ativar a segurança de transferência em um serviço em um domínio do Windows usando a configuração  
  
1.  Adicionar um [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elemento para o [ \<associações >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) seção do elemento do arquivo de configuração.  
  
2.  Adicionar um <`binding`> elemento para o <`WSHttpBinding`> elemento e defina o `configurationName` de atributo para um valor apropriado para seu aplicativo.  
  
3.  Adicionar um <`security`> elemento e defina o `mode` a mensagem de atributo.  
  
4.  Adicionar um <`message`> elemento e defina o `clientCredentialType` atributo Windows.  
  
5.  No arquivo de configuração do serviço, substitua o `<bindings>` seção com o código a seguir. Se você não tiver um arquivo de configuração de serviço, consulte [usando associações para configurar os serviços e clientes](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
    ```xml  
    <bindings>  
      <wsHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    ```  
  
### <a name="using-the-binding-in-a-client"></a>Usando a associação em um cliente  
 Este procedimento mostra como gerar dois arquivos: um proxy que se comunica com o serviço e um arquivo de configuração. Ele também descreve alterações para o programa cliente, que é o terceiro arquivo usado no cliente.  
  
##### <a name="to-use-a-binding-in-a-client-with-configuration"></a>Para usar uma associação em um cliente com a configuração  
  
1.  Use a ferramenta SvcUtil.exe para gerar o arquivo de código e configuração de proxy de metadados do serviço. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Como: criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  Substitua o [ \<associações >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) seção do arquivo de configuração gerado com o código de configuração da seção anterior.  
  
3.  Código procedural é inserido no início de `Main` método do programa cliente.  
  
4.  Crie uma instância da classe cliente gerada passando o nome da associação no arquivo de configuração como um parâmetro de entrada.  
  
5.  Chamar o <xref:System.ServiceModel.ClientBase%601.Open%2A> método, conforme mostrado no código a seguir.  
  
6.  Chamar o serviço e exibir os resultados.  
  
     [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]  
  
 [!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)] 
 [!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]      
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.WSHttpBinding>  
 [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Como criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [Protegendo serviços](../../../docs/framework/wcf/securing-services.md)  
 [Visão geral de segurança](../../../docs/framework/wcf/feature-details/security-overview.md)
