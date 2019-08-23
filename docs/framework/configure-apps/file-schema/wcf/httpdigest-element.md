---
title: Elemento <httpDigest>
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 2ceefdd7fab82025e89ad08d8423d57524c2e4d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925557"
---
# <a name="httpdigest-element"></a>\<Elemento de > httpDigest
Especifica uma credencial de tipo Digest usada ao autenticar o cliente para um serviço.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<endpointBehaviors>  
\<> de comportamento  
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
|`impersonationLevel`|Define a preferência de representação que o cliente se comunica com o servidor. O modo de representação que o cliente seleciona não é imposto no servidor. Os valores válidos incluem o seguinte:<br /><br /> ID O servidor pode obter a identidade e os privilégios do cliente, mas não pode representar o cliente.<br />Representação O servidor pode representar o contexto de segurança do cliente no sistema local.<br />Delegação O servidor pode representar o contexto de segurança do cliente em sistemas remotos.<br />Modo O servidor não pode representar ou identificar o cliente.<br />None Não há um nível de representação atribuído.<br /><br /> O padrão é identificação. Esse atributo é do tipo <xref:System.Security.Principal.TokenImpersonationLevel>.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|Especifica as credenciais usadas para autenticar um cliente para um serviço.|  
  
## <a name="remarks"></a>Comentários  
 Um resumo é um hash determinado pelo uso de um algoritmo e um conjunto de entradas. O autenticador e o concorda autenticado sobre um algoritmo e trocam os dados usados como entradas. O cliente pode calcular o hash e enviá-lo para o serviço. O serviço também calcula o hash e compara os valores. Uma correspondência valida o cliente.  
  
 Esse recurso deve ser habilitado com Active Directory no Windows e no Serviços de Informações da Internet (IIS). Para obter mais informações, consulte [autenticação Digest no IIS 6,0](https://go.microsoft.com/fwlink/?LinkId=88443).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [Comportamentos de segurança](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Protegendo clientes](../../../wcf/securing-clients.md)
- [Trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md)
- [Protegendo serviços e clientes](../../../wcf/feature-details/securing-services-and-clients.md)
