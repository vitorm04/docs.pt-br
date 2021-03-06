---
title: Como criar um serviço que utiliza um validador de certificado personalizado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: af1bb9b2ff793f6e6854c1b253dd445a35a5076f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185570"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a>Como criar um serviço que utiliza um validador de certificado personalizado
Este tópico mostra como implementar um validador de certificado personalizado e como configurar credenciais de cliente ou serviço para substituir a lógica de validação de certificado padrão pelo validador de certificado personalizado.  
  
 Se o certificado X.509 for usado para autenticar um cliente ou serviço, o Windows Communication Foundation (WCF) por padrão usará a loja de certificados Windows e a API Crypto para validar o certificado e garantir que ele seja confiável. Às vezes, a funcionalidade de validação de certificado incorporada não é suficiente e deve ser alterada. O WCF fornece uma maneira fácil de alterar a lógica de validação, permitindo que os usuários adicionem um validador de certificado personalizado. Se um validador de certificado personalizado for especificado, o WCF não usará a lógica de validação de certificado incorporada, mas depende do validador personalizado.  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-create-a-custom-certificate-validator"></a>Para criar um validador de certificado personalizado  
  
1. Defina uma nova <xref:System.IdentityModel.Selectors.X509CertificateValidator>classe derivada de .  
  
2. Implementar o <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> método abstrato. O certificado que deve ser validado é passado como argumento para o método. Se o certificado aprovado não for válido de acordo <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>com a lógica de validação, este método lança um . Se o certificado for válido, o método retorna ao chamador.  
  
    > [!NOTE]
    > Para retornar erros de autenticação de volta para o cliente, gere um <xref:System.ServiceModel.FaultException> no método <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a>Para especificar um validador de certificado personalizado na configuração de serviço  
  
1. Adicione [ \<](../../configure-apps/file-schema/wcf/behaviors.md) um elemento>comportamentos e um [ \<>de serviçosComportamento ao](../../configure-apps/file-schema/wcf/servicebehaviors.md) [ \<elemento system.serviceModel>.](../../configure-apps/file-schema/wcf/system-servicemodel.md)  
  
2. Adicione [ \<](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) um comportamento>`name` e defina o atributo como um valor apropriado.  
  
3. Adicione um [ \<serviceCredentials](../../configure-apps/file-schema/wcf/servicecredentials.md) `<behavior>`>ao elemento.  
  
4. Adicione `<clientCertificate>` um elemento `<serviceCredentials>` ao elemento.  
  
5. Adicione uma [ \<>de autenticação](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) ao `<clientCertificate>` elemento.  
  
6. Defina `customCertificateValidatorType` o atributo para o tipo validador. O exemplo a seguir define o atributo para o namespace e nome do tipo.  
  
7. Defina `certificateValidationMode` o `Custom`atributo para .  
  
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
  
1. Adicione [ \<](../../configure-apps/file-schema/wcf/behaviors.md) um elemento>comportamentos e um [ \<>de serviçosComportamento ao](../../configure-apps/file-schema/wcf/servicebehaviors.md) [ \<elemento system.serviceModel>.](../../configure-apps/file-schema/wcf/system-servicemodel.md)  
  
2. Adicione um [ \<elemento>de comportamento de ponto final.](../../configure-apps/file-schema/wcf/endpointbehaviors.md)  
  
3. Adicione um elemento `<behavior>` e defina o atributo `name` para um valor apropriado.  
  
4. Adicione um [ \<elemento de>clientCredentials.](../../configure-apps/file-schema/wcf/clientcredentials.md)  
  
5. Adicionar um [ \<serviçoCertificado>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).  
  
6. Adicione uma [ \<autenticação>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) como mostrado no exemplo a seguir.  
  
7. Defina `customCertificateValidatorType` o atributo para o tipo validador.  
  
8. Defina `certificateValidationMode` o `Custom`atributo para . O exemplo a seguir define o atributo para o namespace e nome do tipo.  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a>Para especificar um validador de certificado personalizado usando código no serviço  
  
1. Especifique o validador de certificado personalizado na <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> propriedade. Você pode acessar as <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> credenciais de serviço usando a propriedade.  
  
2. Defina a propriedade <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> como <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a>Para especificar um validador de certificado personalizado usando código no cliente  
  
1. Especifique o validador de certificado personalizado usando a <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> propriedade. Você pode acessar as <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> credenciais do cliente usando a propriedade. (A classe cliente gerada pelo [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) sempre deriva da <xref:System.ServiceModel.ClientBase%601> classe.)  
  
2. Defina a propriedade <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> como <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 A amostra a seguir mostra a implementação de um validador de certificado personalizado e seu uso no serviço.  
  
### <a name="code"></a>Código  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
