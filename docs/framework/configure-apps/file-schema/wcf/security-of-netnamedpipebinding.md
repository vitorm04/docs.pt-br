---
title: <security> de <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 31ea31ce6880a770c966350cd931e487396c4d63
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736439"
---
# <a name="security-of-netnamedpipebinding"></a>\<> de segurança do \<netNamedPipeBinding >
Define as configurações de segurança para uma associação.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netNamedPipeBinding >** ](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**security >**  
  
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
|modo|Especifica o tipo de segurança que é aplicado a essa associação. Os valores válidos incluem o seguinte:<br /><br /> -Nenhum: isso desabilita a segurança.<br />-Transport: a segurança é fornecida usando a segurança baseada em transporte subjacente. É possível controlar o nível de proteção com esse modo.<br />-O valor padrão é transporte. Este atributo é do tipo <xref:System.ServiceModel.NetNamedPipeSecurityMode>.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|transporte|Define as configurações de segurança para o transporte. Este elemento é do tipo <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|associação|O elemento Binding do [\<netNamedPipeBinding >](netnamedpipebinding.md).|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [Protegendo serviços e clientes](../../../wcf/feature-details/securing-services-and-clients.md)
- [Selecionando um tipo de credencial](../../../wcf/feature-details/selecting-a-credential-type.md)
- [Associações](../../../wcf/bindings.md)
- [Configurando associações fornecidas pelo sistema](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Usando associações para configurar serviços e clientes](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding >](bindings.md)
