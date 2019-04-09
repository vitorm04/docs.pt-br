---
title: <httpDigest> Elemento
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 914711e4d6c3dbb1ccc741af1b3abd6b8de716a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165315"
---
# <a name="httpdigest-element"></a>\<httpDigest > elemento
Especifica um resumo de tipo de credencial usada para autenticar o cliente a um serviço.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<endpointBehaviors>  
\<behavior>  
\<clientCredentials>  
\<httpDigest>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`impersonationLevel`|Define a preferência de representação que o cliente se comunica com o servidor. O modo de representação que o cliente seleciona não é imposto no servidor. Os valores válidos incluem o seguinte:<br /><br /> -Identificação: O servidor pode obter a identidade e os privilégios do cliente, mas não pode representar o cliente.<br />-Representação: O servidor pode representar o contexto de segurança do cliente no sistema local.<br />-Delegação: O servidor pode representar o contexto de segurança do cliente em sistemas remotos.<br />-Anônimo: O servidor não pode representar ou identificar o cliente.<br />-None: Não há um nível de representação atribuído.<br /><br /> O padrão é a identificação. Esse atributo é do tipo <xref:System.Security.Principal.TokenImpersonationLevel>.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Especifica as credenciais usadas para autenticar um cliente para um serviço.|  
  
## <a name="remarks"></a>Comentários  
 Um resumo é um hash determinado por meio de um algoritmo e um conjunto de entradas. O autenticador e o autenticado concordem com um algoritmo e os dados usados como entradas do exchange. O cliente pode calcular o hash e enviá-lo para o serviço. O serviço também calcula o hash e compara os valores. Uma correspondência valida o cliente.  
  
 Esse recurso deve ser habilitado com o Active Directory no Windows e serviços de informações da Internet (IIS). Para obter mais informações, consulte [a autenticação Digest no IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [Comportamentos de segurança](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Protegendo clientes](../../../../../docs/framework/wcf/securing-clients.md)
- [Trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
