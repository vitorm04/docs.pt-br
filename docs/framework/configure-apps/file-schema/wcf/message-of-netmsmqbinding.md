---
title: '&lt;mensagem&gt; de &lt;netMsmqBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f3b03fcce02c51563ed006e62a3f77f76bede777
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmessagegt-of-ltnetmsmqbindinggt"></a>&lt;mensagem&gt; de &lt;netMsmqBinding&gt;
Define as configurações de segurança de mensagem SOAP neste `netMsmqBinding` associação.  
  
 \<sistema. ServiceModel >  
\<associações >  
\<netMsmqBinding >  
\<associação >  
\<segurança >  
\<mensagem >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<netMsmqBinding>  
    <binding>  
      <security>  
         <message   
                      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
    </security>  
</netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|algorithmSuite|Define a mensagem de algoritmos de criptografia e a disposição de chave que são usados para atingir a segurança baseada em mensagem para mensagens enviadas pelo transporte MSMQ.<br /><br /> O valor padrão é `Aes256`. Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|  
|clientCredentialType|Especifica o tipo de credencial a ser usada ao executar a autenticação de cliente para mensagens enviadas por meio do transporte MSMQ. Os valores válidos incluem o seguinte:<br /><br /> -Nenhum: Isso permite que o serviço interaja com clientes anônimos. O serviço, nem o cliente requer uma credencial.<br />-Windows: Isso permite que as trocas SOAP estar sob o contexto autenticado de uma credencial do Windows. Isso sempre realiza a autenticação Kerberos.<br />-Nome de usuário: Isso permite que o serviço exigir que o cliente seja autenticado usando uma credencial de nome de usuário. A credencial nesse caso deve ser especificado usando o `clientCredentials` comportamento **cuidado:** [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] não oferece suporte para enviar uma senha digest ou derivação de chaves usando a senha e essas chaves para segurança de mensagem.   Portanto, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] impõe que o exchange é protegido ao usar credenciais de nome de usuário. Esse modo exige que o certificado de serviço seja especificada no lado cliente usando `clientCredential` comportamento e `serviceCertificate`. <br /><br /> -O certificado: Isso permite que o serviço exigir que o cliente seja autenticado usando um certificado. A credencial do cliente nesse caso deve ser especificado usando o `clientCredentials` comportamento. A credencial de serviço nesse caso deve ser especificado usando o `clientCredentials` comportamento especificando o `serviceCertificate`.<br />-CardSpace: Isso permite que o serviço exigir que o cliente seja autenticado usando um CardSpace. O `serviceCertiifcate` devem ser provisionados no `clientCredential` comportamento.<br /><br /> O valor padrão é `Windows`. Esse atributo é do tipo <xref:System.ServiceModel.MessageCredentialType>.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Define as configurações de segurança para uma associação.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>  
 <xref:System.ServiceModel.MessageSecurityOverMsmq>  
 [Filas no WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
