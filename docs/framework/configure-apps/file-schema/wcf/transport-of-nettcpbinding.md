---
title: '&lt;transporte&gt; de &lt;netTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ad2271b86d37d9063ac54d9a4e45681d132eb1d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="lttransportgt-of-ltnettcpbindinggt"></a>&lt;transporte&gt; de &lt;netTcpBinding&gt;
Define o tipo de requisitos de segurança de nível de mensagem para um ponto de extremidade configurado com o [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 \<system.ServiceModel>  
\<bindings>  
\<netTcpBinding>  
\<associação >  
\<security>  
\<transporte >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<netTcpBinding>  
    <binding>  
        <security  
         mode="None|Transport|Message|TransportWithMessageCredential">  
            <transport clientCredentialType="None|Windows|Certificate"  
             protectionLevel="None|Sign|EncryptAndSign"             sslProtocols="Tls|Tls11|Tls12">  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</netTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os elementos pai de atributos e elementos filho  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|clientCredentialType|Opcional. Especifica o tipo de credencial a ser usada ao executar a autenticação de cliente usando a segurança de transporte.<br /><br /> -O valor padrão é `Windows`.<br />-Este atributo é do tipo <xref:System.ServiceModel.TcpClientCredentialType>.|  
|protectionLevel|Opcional. Define a segurança no nível do transporte TCP. Assinatura de mensagens reduz o risco de um terceiro que viole a mensagem enquanto eles estão sendo transferidos. A criptografia fornece privacidade de nível de dados durante o transporte.<br /><br /> O valor padrão é `EncryptAndSign`.|  
|sslProtocols|Um valor de sinalizador de enumeração de SslProtocols que especifica quais SslProtocols têm suporte. O padrão é Tls &#124; Tls11 &#124; Tls12.|  
|policyEnforcement|Esta enumeração Especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> devem ser impostas.<br /><br /> 1.  Nunca – a política é aplicada nunca (proteção estendida é desabilitada).<br />2.  WhenSupported – a política será aplicada somente se o cliente oferece suporte à proteção estendida.<br />3.  Sempre – a política sempre é aplicada. Os clientes que não oferecem suporte a proteção estendida falhará ao autenticar.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Nenhum|O cliente é anônimo. Isso requer um certificado para o serviço.|  
|Windows|Especifica a autenticação do Windows do cliente usando o SP negociação (Kerberos negociação).|  
|certificado|O cliente é autenticado usando um certificado. Isso usa a negociação SSL e requer um certificado para o serviço.|  
  
## <a name="protectionlevel-attribute"></a>Atributo de protectionLevel  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Nenhum|Sem proteção.|  
|Logon|As mensagens são assinadas.|  
|EncryptAndSign|-Mensagens são criptografadas e assinadas.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Especifica os recursos de segurança de [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).|  
  
## <a name="remarks"></a>Comentários  
 Use a segurança de transporte para integridade e confidencialidade da mensagem SOAP e de autenticação mútua. Se este modo de segurança é selecionado em uma associação, a pilha de canais é configurada por meio de um transporte seguro e as mensagens SOAP são protegidas usando a segurança de transporte, como SSL ou do Windows (negociação) sobre TCP.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.TcpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<binding>](../../../../../docs/framework/misc/binding.md)
