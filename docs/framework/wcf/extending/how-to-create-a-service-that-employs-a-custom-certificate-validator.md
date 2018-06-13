---
title: Como criar um serviço que utiliza um validador de certificado personalizado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: cc768f5e5086e6eba1ccac9d969eac14e14ceb2f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808137"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a>Como criar um serviço que utiliza um validador de certificado personalizado
Este tópico mostra como implementar um validador de certificado personalizado e como configurar credenciais de cliente ou serviço para substituir a lógica de validação de certificado padrão com o validador de certificado personalizado.  
  
 Se o certificado x. 509 é usado para autenticar um cliente ou serviço, o Windows Communication Foundation (WCF) por padrão usa o repositório de certificados do Windows e a API de criptografia para validar o certificado e certifique-se de que ele é confiável. Às vezes, a funcionalidade de validação do certificado interno não é suficiente e deve ser alterada. O WCF fornece uma maneira fácil de alterar a lógica de validação, permitindo que os usuários adicionem um validador de certificado personalizado. Se um validador de certificado personalizado for especificado, o WCF não usa a lógica de validação do certificado interno mas depende do validador personalizado em vez disso.  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-create-a-custom-certificate-validator"></a>Para criar um validador de certificado personalizado  
  
1.  Definir uma nova classe derivada de <xref:System.IdentityModel.Selectors.X509CertificateValidator>.  
  
2.  Implementar o resumo <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> método. O certificado deve ser validado é passado como um argumento para o método. Se o certificado passado não é válido de acordo com a lógica de validação, este método lança um <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>. Se o certificado é válido, o método retorna ao chamador.  
  
    > [!NOTE]
    >  Para retornar erros de autenticação de volta para o cliente, gere um <xref:System.ServiceModel.FaultException> no método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a>Para especificar um validador de certificado personalizado na configuração do serviço  
  
1.  Adicionar um [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento e um [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) para o [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento.  
  
2.  Adicionar um [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) e defina o `name` de atributo para um valor apropriado.  
  
3.  Adicionar um [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) para o `<behavior>` elemento.  
  
4.  Adicionar um `<clientCertificate>` elemento para o `<serviceCredentials>` elemento.  
  
5.  Adicionar uma [ \<autenticação >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) para o `<clientCertificate>` elemento.  
  
6.  Definir o `customCertificateValidatorType` de atributo para o tipo de validador. O exemplo a seguir define o atributo para o namespace e o nome do tipo.  
  
7.  Definir o `certificateValidationMode` atributo `Custom`.  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <serviceBehaviors>  
        <behavior name="ServiceBehavior">  
         <serviceCredentials>  
          <clientCertificate>  
          <authentication certificateValidationMode="Custom" customCertificateValidatorType="Samples.MyValidator, service" />  
          </clientCertificate>  
         </serviceCredentials>  
        </behavior>  
       </serviceBehaviors>  
      </behaviors>  
    </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a>Para especificar um validador de certificado personalizado usando a configuração no cliente  
  
1.  Adicionar um [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento e um [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) para o [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento.  
  
2.  Adicionar uma [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) elemento.  
  
3.  Adicione um elemento `<behavior>` e defina o atributo `name` para um valor apropriado.  
  
4.  Adicionar um [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elemento.  
  
5.  Adicionar um [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).  
  
6.  Adicionar uma [ \<autenticação >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) conforme mostrado no exemplo a seguir.  
  
7.  Definir o `customCertificateValidatorType` de atributo para o tipo de validador.  
  
8.  Definir o `certificateValidationMode` atributo `Custom`. O exemplo a seguir define o atributo para o namespace e o nome do tipo.  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <endpointBehaviors>  
        <behavior name="clientBehavior">  
         <clientCredentials>  
          <serviceCertificate>  
           <authentication certificateValidationMode="Custom"   
                  customCertificateValidatorType=  
             "Samples.CustomX509CertificateValidator, client"/>  
          </serviceCertificate>  
         </clientCredentials>  
        </behavior>  
       </endpointBehaviors>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a>Para especificar um validador de certificado personalizado usando o código do serviço  
  
1.  Especifique o validador de certificado personalizado no <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> propriedade. Você pode acessar as credenciais de serviço usando o <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> propriedade.  
  
2.  Defina a propriedade <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> como <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a>Para especificar um validador de certificado personalizado usando o código no cliente  
  
1.  Especifique o validador de certificado personalizado usando o <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> propriedade. Você pode acessar as credenciais de cliente usando o <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> propriedade. (A classe cliente gerada pelo [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) sempre deriva o <xref:System.ServiceModel.ClientBase%601> classe.)  
  
2.  Defina a propriedade <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> como <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir mostra uma implementação de um validador de certificado personalizado e seu uso do serviço.  
  
### <a name="code"></a>Código  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>
