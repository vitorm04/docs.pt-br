---
title: 'Como: definir o modo de segurança'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
ms.openlocfilehash: 5a4550e4c914dcdbc9908e766c67a2efa53e6e9e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339379"
---
# <a name="how-to-set-the-security-mode"></a>Como: definir o modo de segurança
Segurança do Windows Communication Foundation (WCF) tem três modos de segurança comuns que são encontrados no associações mais predefinidas: "transporte com credencial de mensagem.", a mensagem e transporte Dois modos adicionais são específicos para duas ligações: o modo "somente credenciais transporte" encontrado na <xref:System.ServiceModel.BasicHttpBinding>e "Dois" modo, encontrado no <xref:System.ServiceModel.NetMsmqBinding>. No entanto, este tópico concentra-se em três modos comuns de segurança: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, e <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
 Observe que não todas as associações predefinidas dá suporte a todos os modos. Este tópico define o modo com o <xref:System.ServiceModel.WSHttpBinding> e <xref:System.ServiceModel.NetTcpBinding> classes e demonstra como definir o modo programaticamente e por meio da configuração.  
  
 Para obter mais informações, consulte segurança do WCF, consulte [visão geral de segurança](../../../docs/framework/wcf/feature-details/security-overview.md), [protegendo serviços](../../../docs/framework/wcf/securing-services.md), e [protegendo serviços e clientes](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md). Para obter mais informações sobre o modo de transporte e mensagem, consulte [segurança de transporte](../../../docs/framework/wcf/feature-details/transport-security.md) e [segurança de mensagem](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
### <a name="to-set-the-security-mode-in-code"></a>Para definir o modo de segurança no código  
  
1. Crie uma instância da classe de associação que você está usando. Para obter uma lista de associações predefinidas, consulte [System-Provided associações](../../../docs/framework/wcf/system-provided-bindings.md). Este exemplo cria uma instância da <xref:System.ServiceModel.WSHttpBinding> classe.  
  
2. Defina as `Mode` propriedade do objeto retornado pelo `Security` propriedade.  
  
     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]  
  
     Como alternativa, defina o modo para mensagem, conforme mostrado no código a seguir.  
  
     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]  
  
     Ou defina o modo de transporte com credenciais de mensagem, conforme mostrado no código a seguir.  
  
     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]  
  
3. Você também pode definir o modo no construtor da associação, conforme mostrado no código a seguir.  
  
     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]  
  
## <a name="setting-the-clientcredentialtype-property"></a>Definindo a propriedade ClientCredentialType  
 Definir o modo como um dos três valores determina como você definir o `ClientCredentialType` propriedade. Por exemplo, usando o <xref:System.ServiceModel.WSHttpBinding> classe, definir o modo como `Transport` significa que você deve definir o <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> propriedade do <xref:System.ServiceModel.HttpTransportSecurity> classe para um valor apropriado.  
  
#### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a>Para definir a propriedade ClientCredentialType para o modo de transporte  
  
1. Crie uma instância da associação.  
  
2. Defina a propriedade `Mode` como `Transport`.  
  
3. Defina a propriedade `ClientCredential` com um valor apropriado. O código a seguir define a propriedade como `Windows`.  
  
     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]  
  
#### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a>Para definir a propriedade ClientCredentialType para o modo de mensagem  
  
1. Crie uma instância da associação.  
  
2. Defina a propriedade `Mode` como `Message`.  
  
3. Defina a propriedade `ClientCredential` com um valor apropriado. O código a seguir define a propriedade como `Certificate`.  
  
     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]  
  
#### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a>Para definir a propriedade de modo e ClientCredentialType na configuração  
  
1. Adicionar um elemento de associação apropriado para o [ \<associações >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elemento do arquivo de configuração. O exemplo a seguir adiciona uma [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elemento.  
  
2. Adicionar um `<binding>` elemento e defina seu `name` de atributo para um valor apropriado.  
  
3. Adicionar um `<security>` elemento e defina o `mode` atributo `Message`, `Transport`, ou `TransportWithMessageCredential`.  
  
4. Se o modo é definido como `Transport`, adicione um `<transport>` elemento e defina o `clientCredential` de atributo para um valor apropriado.  
  
     O exemplo a seguir define o modo como "`Transport"`e, em seguida, define o `clientCredentialType` atributo da `<transport>` elemento a ser"`Windows"`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="TransportSecurity">  
        <security mode="Transport" >  
           <transport clientCredentialType = "Windows" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     Como alternativa, defina as `security mode` para "`Message"`, seguido por um `<"message">` elemento. Este exemplo define o `clientCredentialType` para "`Certificate"`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="MessageSecurity">  
        <security mode="Message" >  
           <message clientCredentialType = "Certificate" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     Usando o <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> valor é um caso especial e é explicado abaixo.  
  
### <a name="using-transportwithmessagecredential"></a>Usar TransportWithMessageCredential  
 Ao definir o modo de segurança para `TransportWithMessageCredential`, o transporte determina o mecanismo real que fornece a segurança de nível de transporte. Por exemplo, o protocolo HTTP usa Secure Sockets Layer (SSL) sobre HTTP (HTTPS). Portanto, definir a `ClientCredentialType` propriedade de qualquer objeto de segurança de transporte (como <xref:System.ServiceModel.HttpTransportSecurity>) será ignorado.  Em outras palavras, você só pode definir a `ClientCredentialType` do objeto de segurança de mensagem (para o `WSHttpBinding` associação, o <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> objeto).  
  
 Para obter mais informações, confira [Como: Usar a segurança de transporte e as credenciais de mensagem](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md).  
  
## <a name="see-also"></a>Consulte também

- [Como: Configurar uma porta com um certificado SSL](../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Como: Usar a segurança de transporte e as credenciais de mensagem](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)
- [Segurança de transporte](../../../docs/framework/wcf/feature-details/transport-security.md)
- [Segurança de mensagem](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [Visão geral de segurança](../../../docs/framework/wcf/feature-details/security-overview.md)
- [Associações fornecidas pelo sistema](../../../docs/framework/wcf/system-provided-bindings.md)
- [\<security>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [\<security>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [\<security>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
