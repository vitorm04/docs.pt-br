---
title: '&lt;transporte&gt; de &lt;netNamedPipeBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7698e280aeae29e11a7f1eba0137d83b3015d525
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="lttransportgt-of-ltnetnamedpipebindinggt"></a>&lt;transporte&gt; de &lt;netNamedPipeBinding&gt;
Define as configurações de segurança de transporte para um pipe nomeado.  
  
 \<sistema. ServiceModel >  
\<associações >  
\<netNamedPipeBinding >  
\<associação >  
\<segurança >  
\<transporte >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<netNamedPipeBinding>  
   <binding>  
      <security mode="None/Transport">  
            <transport protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|protectionLevel|Define o nível de proteção de pipe nomeado. Assinatura de mensagens reduz o risco de um terceiro que viole a mensagem enquanto eles estão sendo transferidos. A criptografia fornece privacidade de nível de dados durante o transporte. Os valores válidos incluem o seguinte:<br /><br /> -Nenhum: Sem proteção.<br />-Sign: Mensagens são assinadas.<br />-EncryptAndSign: Mensagens são criptografadas e assinadas.<br /><br /> O valor padrão é EncryptAndSign.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|Define as configurações de segurança para uma associação.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
