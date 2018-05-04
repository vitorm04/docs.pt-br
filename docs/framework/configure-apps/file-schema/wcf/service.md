---
title: '&lt;Serviço&gt;'
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: a73e4699e0998338f09e1ed0504f5b1cfd73b225
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltservicegt"></a>&lt;Serviço&gt;
O `service` elemento contém as configurações para um serviço do Windows Communication Foundation (WCF). Ele também contém pontos de extremidade que expõem o serviço.  
  
 \<system.ServiceModel>  
\<Serviços >  
\<serviço >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<service behaviorConfiguration=String"  
        name="String"  
</service>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|behaviorConfiguration|Uma cadeia de caracteres que contém o nome do comportamento do comportamento a ser usado para instanciar o serviço. O nome do comportamento deve estar no escopo no ponto em que o serviço está definido. O valor padrão é uma cadeia de caracteres vazia.|  
|name|Necessário um atributo de cadeia de caracteres que especifica o tipo de serviço a ser instanciado. Essa configuração deve serão iguais a um tipo válido. O formato deve ser `Namespace.Class.`|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|Uma coleção de `endpoint` elementos que expõem este serviço.|  
|[\<host >](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|Especifica o host desta instância de serviço. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.HostElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Serviços >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|O elemento raiz de todos os elementos de configuração do WCF.|  
  
## <a name="remarks"></a>Comentários  
 Os serviços são definidos no `services` seção do arquivo de configuração. Um assembly pode conter qualquer número de serviços. Cada serviço tem seu próprio `service` seção de configuração. Esta seção e seu conteúdo definem o contrato de serviço, o comportamento e os pontos de extremidade do serviço em questão.  
  
 O `behaviorConfiguration` elemento também é opcional. Ele identifica o comportamento de serviço usa. O comportamento especificado neste atributo deve vincular a um comportamento no escopo no mesmo arquivo de configuração.  
  
 Cada serviço expõe um ou mais pontos de extremidade, que tem seu próprio endereço e associação. Todas as associações usadas no arquivo de configuração devem ser definidas no escopo do arquivo. Associação são vinculados aos pontos de extremidade pela combinação dos atributos `name` e `bindingConfiguration`. O `name` atributo descreve a seção a associação é definida no. O `bindingConfiguration` atributo define qual configuração dentro da seção de associação é usada. Uma seção de associação pode definir várias configurações.  
  
## <a name="example"></a>Exemplo  
 Este é um exemplo de uma configuração de serviço.  
  
```xml  
<service behaviorConfiguration="testChannelBehavior"   
     name="HelloWorld">  
     <endpoint   
        address="/HelloWorld2/"  
        name="test"  
        bindingNamespace="http://www.cohowinery.com/"  
        binding="basicHttpBinding"  
        contract="IHelloWorld" />  
</service>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.ServiceElement>  
 [Configurando serviços](../../../../../docs/framework/wcf/configuring-services.md)
