---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 91eafa46aa73b5e6d359fcbe48f098f9f8a4d0f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644286"
---
# <a name="exposedmethod"></a>\<exposedMethod>
Representa um método COM+ que está exposto quando a interface em um componente COM+ é exposta como um serviço Web.  
  
 \<system.ServiceModel>  
\<comContracts>  
\<comContract>  
\<métodos >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|name|Uma cadeia de caracteres que contém o método COM+ que está exposto quando a interface em um componente COM+ é exposta como um serviço Web.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<exposedMethods>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethods.md)|Uma coleção de [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementos.|  
  
## <a name="remarks"></a>Comentários  
 A COM+ integration ferramenta de configuração (ComSvcConfig.exe) pode ser usada para adicionar métodos específicos de uma interface COM apareçam no contrato de serviço gerado.  
  
 Por exemplo, você pode usar o comando a seguir para adicionar os três métodos nomeados do `IFinances` interface COM no `ItemOrders`. Componente financeiro ao contrato de serviço gerado.  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 Quando você executa também o ComSvcConfig.exe, em seguida, gera o seguinte contrato de serviço, listando os métodos mencionados anteriormente como [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementos.  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 No momento da inicialização de serviço, o tempo de execução tenta gerar um contrato de serviço ao refletir sobre e adicionar somente os métodos incluídos na lista de [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elementos. Um rastreamento é produzido para cada método de interface que não está incluído no contrato de serviço.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [\<comContracts>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [Integração de aplicativos COM+](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [Como: Definir as configurações de serviço COM+](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
