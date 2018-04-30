---
title: Práticas recomendadas para segurança no WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- best practices [WCF], security
ms.assetid: 3639de41-1fa7-4875-a1d7-f393e4c8bd69
caps.latest.revision: 19
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 0545ff40247b7ff86cb6227fa8cf4af8666c3629
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="best-practices-for-security-in-wcf"></a>Práticas recomendadas para segurança no WCF
As seções a seguir listam as práticas recomendadas a serem considerados durante a criação de aplicativos seguros usando [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Para obter mais informações sobre segurança, consulte [considerações de segurança](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md), [considerações de segurança para dados](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md), e [considerações de segurança com metadados](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md).  
  
## <a name="identify-services-performing-windows-authentication-with-spns"></a>Identificar os serviços para executar a autenticação do Windows com os SPNs  
 Os serviços podem ser identificados com nomes principais de usuário (UPNs) ou nomes principais de serviço (SPNs). Serviços executados em contas de computador como serviço de rede tem uma identidade SPN correspondente para o computador que está sendo executado. Serviços executados em contas de usuário tem uma identidade UPN correspondente para o usuário que está sendo executado, embora o `setspn` ferramenta pode ser usada para atribuir um SPN para a conta de usuário. Configurar um serviço para que ele possa ser identificado por meio de SPN e configurar os clientes que se conectar ao serviço para usar esse SPN pode fazer certas ataques mais difícil. Essas diretrizes se aplicam às associações usando Kerberos ou SSPI negociação.  Os clientes ainda devem especificar um SPN no caso onde SSPI reverterá para NTLM.  
  
## <a name="verify-service-identities-in-wsdl"></a>Verificar as identidades de serviço em WSDL  
 O WS-SecurityPolicy permite que os serviços publicar informações sobre suas próprias identidades nos metadados. Quando recuperados por meio de `svcutil` ou outros métodos, como <xref:System.ServiceModel.Description.WsdlImporter>, essas informações de identidade são convertidas para as propriedades de identidade do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endereços de ponto de extremidade de serviço. Os clientes que não verificam se essas identidades de serviço estão corretas e válido efetivamente ignoram a autenticação de serviço. Um serviço mal-intencionado pode explorar esses clientes para executar o encaminhamento de credenciais e outros ataques "man no meio" alterando a identidade declarada em seu WSDL.  
  
## <a name="use-x509-certificates-instead-of-ntlm"></a>Use X509 certificados em vez de NTLM  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oferece dois mecanismos para autenticação de ponto a ponto: X509 certificados (usados pelo canal de ponto a ponto) e autenticação do Windows em que uma negociação de SSPI fazer downgrade do Kerberos para NTLM.  Autenticação baseada em certificado usando tamanhos de chave de 1024 bits ou mais é preferencial para NTLM por vários motivos:  
  
-   a disponibilidade de autenticação mútua,  
  
-   o uso de algoritmos de criptografia mais fortes, e  
  
-   a maior dificuldade de utilizando encaminhados X509 credenciais.  
  
 Para obter uma visão geral do NTLM ataques de encaminhamento, vá para [ http://msdn.microsoft.com/msdnmag/issues/06/09/SecureByDesign/default.aspx ](http://go.microsoft.com/fwlink/?LinkId=109571).  
  
## <a name="always-revert-after-impersonation"></a>Reverter sempre depois de representação  
 Ao usar APIs que permitem a representação de um cliente, certifique-se de reverter para a identidade original. Por exemplo, ao usar o <xref:System.Security.Principal.WindowsIdentity> e <xref:System.Security.Principal.WindowsImpersonationContext>, usar o c# `using` instrução ou o Visual Basic`Using` instrução, conforme mostrado no código a seguir. O <xref:System.Security.Principal.WindowsImpersonationContext> classe implementa o <xref:System.IDisposable> interface e, portanto, o common language runtime (CLR) é revertida automaticamente para a identidade original depois que o código deixa o `using` bloco.  
  
 [!code-csharp[c_SecurityBestPractices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securitybestpractices/cs/source.cs#1)]
 [!code-vb[c_SecurityBestPractices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securitybestpractices/vb/source.vb#1)]  
  
## <a name="impersonate-only-as-needed"></a>Representar apenas conforme necessário  
 Usando o <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> método o <xref:System.Security.Principal.WindowsIdentity> classe, é possível usar a representação em um escopo muito controlado. Isso é diferente de usar o <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> propriedade do <xref:System.ServiceModel.OperationBehaviorAttribute>, que permite a representação para o escopo da operação inteira. Sempre que possível, controlar o escopo da representação usando o mais preciso <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> método.  
  
## <a name="obtain-metadata-from-trusted-sources"></a>Obter metadados de fontes confiáveis  
 Certifique-se de que você confia na origem dos metadados e certifique-se de que ninguém tenha violado os metadados. Metadados recuperados usando o protocolo HTTP é enviado em texto não criptografado e podem ser violados. Se o serviço usa o <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> e <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> propriedades, use a URL fornecida pelo criador do serviço para baixar os dados usando o protocolo HTTPS.  
  
## <a name="publish-metadata-using-security"></a>Publicar usando a segurança de metadados  
 Para evitar a violação com metadados de um serviço publicado, proteger o ponto de extremidade de troca de metadados com transporte ou segurança em nível de mensagem. Para obter mais informações, consulte [pontos de extremidade de metadados de publicação](../../../../docs/framework/wcf/publishing-metadata-endpoints.md) e [como: publicar metadados para um serviço usando código](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
## <a name="ensure-use-of-local-issuer"></a>Certifique-se de uso do emissor Local  
 Se um endereço do emissor e a associação especificadas para uma associação de determinado, o emissor local não é usado para pontos de extremidade que utilizam essa associação. Clientes que pretende usar sempre o emissor local devem garantir que eles não usam essa associação ou que eles modificarem a associação, de modo que o endereço do emissor é nulo.  
  
## <a name="saml-token-size-quotas"></a>Cotas de tamanho de Token SAML  
 Quando os tokens de segurança asserções Markup Language (SAML) são serializados em mensagens, quando eles são emitidos por um Token de segurança Service (STS) ou quando os clientes apresentação-los para serviços como parte da autenticação, a cota de tamanho máximo da mensagem deve ser suficientemente grande para acomodar o token SAML e as outras partes da mensagem. Em casos normais, as cotas de tamanho de mensagem padrão são suficientes. No entanto, nos casos em que um token SAML é grande porque ele contém centenas de declarações, as cotas devem ser aumentadas para acomodar o token serializado. Para obter mais informações sobre cotas, consulte [considerações de segurança para dados](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
## <a name="set-securitybindingelementincludetimestamp-to-true-on-custom-bindings"></a>Defina SecurityBindingElement.IncludeTimestamp como True em associações personalizadas  
 Quando você cria uma associação personalizada, você deve definir <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> para `true`. Caso contrário, se <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> é definido como `false`, e o cliente está usando um token com chave assimétrico como X509 certificado, a mensagem não será assinada.  
  
## <a name="see-also"></a>Consulte também  
 [Considerações sobre segurança](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Considerações sobre segurança para dados](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 [Considerações de segurança com metadados](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
