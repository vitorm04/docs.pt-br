---
title: "Como fazer a autenticação com um nome de usuário e senha"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1554e8594a611aa75876d14ee7ad0689932372e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a>Como fazer a autenticação com um nome de usuário e senha
Este tópico demonstra como habilitar um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service para autenticar um cliente com um nome de usuário de domínio de Windows e uma senha. Ele pressupõe que você tenha um trabalho, o serviço WCF auto-hospedado. Para obter um exemplo de criação de um consulte da serviço WCF auto-hospedado básico, [Tutorial de Introdução](../../../../docs/framework/wcf/getting-started-tutorial.md). Este tópico pressupõe que o serviço está configurado no código. Se você quiser ver um exemplo de como configurar um serviço semelhante usando um arquivo de configuração consulte [nome de usuário de segurança de mensagem](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
  
 Para configurar um serviço para autenticar os clientes usando o uso de nome de usuário e senhas do domínio do Windows a <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> e defina seu `Security.Mode` propriedade `Message`. Além disso, você deve especificar um X509 certificado que será usado para criptografar o nome de usuário e a senha que são enviadas para o serviço do cliente.  
  
 No cliente, você deve solicitar o nome de usuário e a senha do usuário e especificar as credenciais do usuário no proxy do cliente WCF.  
  
### <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a>Para configurar um serviço WCF para autenticar usando a senha e nome de usuário de domínio Windows.  
  
1.  Criar uma instância do <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, definir o modo de segurança da associação com `SecurityMode.Message`, defina o `ClientCredentialType` da associação com `MessageCredentialType.UserName`e adicione um ponto de extremidade de serviço usando a associação configurada para o host de serviço, conforme mostrado no código a seguir:  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2.  Especifique o certificado do servidor usado para criptografar o nome de usuário e informações de senha enviadas eletronicamente. Esse código deve seguir imediatamente o código acima. O exemplo a seguir usa o certificado que é criado pelo arquivo bat do [nome de usuário de segurança de mensagem](../../../../docs/framework/wcf/samples/message-security-user-name.md) exemplo:  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     Você pode usar seu próprio certificado, basta modificar o código para fazer referência ao certificado. Para obter mais informações sobre como criar e usar certificados, consulte [trabalhar com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md). Verifique se o certificado está no repositório de certificados de pessoas confiáveis para a máquina Local. Você pode fazer isso executando mmc.exe e selecionando o **arquivo**, **Adicionar/Remover Snap-in...**  item de menu. No **adicionar ou Remover Snap-ins** caixa de diálogo, selecione o **snap-in de certificados** e clique em **adicionar**. Na caixa de diálogo Snap-in certificados, selecione **conta de computador**. Por padrão, o certificado gerado a partir do exemplo de nome de usuário de segurança de mensagem será localizado na pasta pessoal/certificados.  Ele será listado como "localhost" em emitido para a coluna na janela do MMC. Arrastar e soltar o certificado para o **pessoas confiáveis** pasta. Isso permitirá que o WCF tratar o certificado como um certificado confiável ao executar a autenticação.  
  
### <a name="to-call-the-service-passing-username-and-password"></a>Para chamar o serviço, passando o nome de usuário e senha  
  
1.  O aplicativo cliente deve solicitar ao usuário seu nome de usuário e senha. O código a seguir solicita ao usuário para o nome de usuário e senha.  
  
    > [!WARNING]
    >  Esse código não deve ser usado na produção, como a senha é exibida ao que está sendo inserido.  
  
    ```  
    public static void GetPassword(out string username, out string password)  
            {  
                Console.WriteLine("Provide a valid machine or domain account. [domain\\user]");  
                Console.WriteLine("   Enter username:");  
                username = Console.ReadLine();  
                Console.WriteLine("   Enter password:");  
                password = Console.ReadLine();             
                return;  
            }  
    ```  
  
2.  Crie uma instância do proxy do cliente especificando as credenciais do cliente conforme mostrado no código a seguir:  
  
    ```  
    string username;  
    string password;  
  
    // Instantiate the proxy  
    Service1Client proxy = new Service1Client();  
  
    // Prompt the user for username & password  
    GetPassword(out username, out password);  
  
    // Set the user’s credentials on the proxy  
    proxy.ClientCredentials.UserName.UserName = username;  
    proxy.ClientCredentials.UserName.Password = password;  
  
    // Treat the test certificate as trusted  
    proxy.ClientCredentials.ServiceCertificate.Authentication.CertificateValidationMode = System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust;  
    // Call the service operation using the proxy  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.SecurityMode>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>  
 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>  
 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>  
 [Segurança de transporte com autenticação básica](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 [Segurança de aplicativos distribuídos](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
