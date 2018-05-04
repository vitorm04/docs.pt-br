---
title: '&lt;windows&gt; do elemento &lt;clientCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: 9badcfafff4bc09a16b0b9a565a9ea5c01e26bb5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltwindowsgt-of-ltclientcredentialsgt-element"></a>&lt;windows&gt; do elemento &lt;clientCredentials&gt;
Especifica as configurações para uma credencial do Windows a ser usado para representar o cliente.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<endpointBehaviors>  
\<comportamento >  
\<clientCredentials>  
\<Windows >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<windows   
    allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"  
        allowNtlm="Boolean"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|Define a preferência de representação que o cliente se comunica com o servidor. O modo de representação que o cliente seleciona não é imposto no servidor. Os valores válidos incluem o seguinte:<br /><br /> -Identificação: O servidor pode obter a identidade e os privilégios do cliente, mas não é possível representar o cliente.<br />-Representação: O servidor pode representar o contexto de segurança do cliente no sistema local.<br />-Delegação: O servidor pode representar o contexto de segurança do cliente em sistemas remotos.<br />-Anônima: O servidor não pode representar ou identificar o cliente.<br />-Nenhum: Um nível de representação não está atribuído.<br /><br /> O padrão é a identificação. Esse atributo é do tipo <xref:System.Security.Principal.TokenImpersonationLevel>.|  
|`allowNtlm`|Definir essa propriedade como `true` permite que a autenticação rebaixar para NTLM se Kerberos não estiver disponível.<br /><br /> Definir essa propriedade como `false` faz com que o Windows Communication Foundation (WCF) para fazer um esforço para lançar uma exceção se NTLM é usado. Observe que a definição dessa propriedade `false` talvez não impeçam que as credenciais do NTLM seja enviado pela conexão.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Especifica as credenciais usadas para autenticar o cliente para o serviço.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.WindowsClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 [Protegendo clientes](../../../../../docs/framework/wcf/securing-clients.md)  
 [Trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
