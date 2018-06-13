---
title: '&lt;clientCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: 5e2dc6c2737b06d76bad6cfc51531b9ca9e02ca5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753229"
---
# <a name="ltclientcredentialsgt"></a>&lt;clientCredentials&gt;
Especifica as credenciais usadas para autenticar o cliente para um serviço.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<endpointBehaviors>  
\<comportamento >  
\<clientCredentials>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<clientCredentials type="String"  
      supportInteractive="Boolean" >  
   <clientCertificate>  
   </clientCertificate>  
   <digest>  
   </digest>  
   <isuedToken>  
   </isuedToken>  
   <peer>  
   </peer>  
   <serviceCertificate>  
   </serviceCertificate>  
   <windowsAuthentication>  
   </windowsAuthentication>  
</clientCredentials>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`supportInteractive`|Um valor booleano que especifica se um usuário interativo pode estar envolvido na seleção de uma credencial de cliente em tempo de execução. O valor padrão é `true`.|  
|`type`|Uma cadeia de caracteres que especifica o tipo deste elemento de configuração.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|Especifica o certificado usado para autenticar o cliente para o serviço. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.|  
|[\<httpDigest >](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|Especifica um digest usado para autenticar o cliente para o serviço. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.|  
|[\<issuedToken >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|Especifica um tipo de token personalizado usado para autenticar o cliente para um Token STS (serviço seguro). Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.|  
|[\<par >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|Especifica uma credencial de ponto a ponto atual. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerCredentialElement>.|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|Especifica o certificado usado para autenticar o serviço para o cliente e fornece uma estrutura para definir opções de certificado. Esse certificado deve ser fornecida fora de banda do serviço ao cliente. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.|  
|[\<Windows >](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|Especifica uma credencial do Windows. O padrão é a credencial do thread atual. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WindowsClientElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<comportamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica um comportamento de ponto de extremidade.|  
  
## <a name="remarks"></a>Comentários  
 As credenciais do cliente são usadas para autenticar o cliente para serviços em casos em que a autenticação mútua é necessária. Esta seção de configuração também pode ser usada para especificar os certificados de serviço para cenários em que o cliente deve proteger as mensagens para um serviço com o certificado do serviço.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 [Comportamentos de segurança](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Protegendo clientes](../../../../../docs/framework/wcf/securing-clients.md)
