---
title: <windows>do <clientCredentials> elemento
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: e9f0ed9879cc42ea25b83e6b626139a40a593112
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940304"
---
# <a name="windows-of-clientcredentials-element"></a>\<> do Windows \<do elemento > ClientCredentials
Especifica as configurações para uma credencial do Windows a ser usada para representar o cliente.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<endpointBehaviors>  
\<> de comportamento  
\<clientCredentials>  
\<windows>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|Define a preferência de representação que o cliente se comunica com o servidor. O modo de representação que o cliente seleciona não é imposto no servidor. Os valores válidos incluem o seguinte:<br /><br /> ID O servidor pode obter a identidade e os privilégios do cliente, mas não pode representar o cliente.<br />Representação O servidor pode representar o contexto de segurança do cliente no sistema local.<br />Delegação O servidor pode representar o contexto de segurança do cliente em sistemas remotos.<br />Modo O servidor não pode representar ou identificar o cliente.<br />None Não há um nível de representação atribuído.<br /><br /> O padrão é identificação. Esse atributo é do tipo <xref:System.Security.Principal.TokenImpersonationLevel>.|  
|`allowNtlm`|Definir essa propriedade como `true` permite que a autenticação faça downgrade para NTLM se o Kerberos não estiver disponível.<br /><br /> Definir essa propriedade como `false` faz com que o Windows Communication Foundation (WCF) faça um melhor esforço para gerar uma exceção se o NTLM for usado. Observe que a definição dessa propriedade `false` como pode não impedir que credenciais NTLM sejam enviadas pela conexão.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|Especifica as credenciais usadas para autenticar o cliente para o serviço.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [Protegendo clientes](../../../wcf/securing-clients.md)
- [Trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md)
- [Protegendo serviços e clientes](../../../wcf/feature-details/securing-services-and-clients.md)
