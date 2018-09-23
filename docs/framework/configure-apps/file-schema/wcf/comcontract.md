---
title: '&lt;comContract&gt;'
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: e2addbada7f55076ae919d93c897991a7ec0fcd8
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46703402"
---
# <a name="ltcomcontractgt"></a>&lt;comContract&gt;
Especifica um contrato de serviço de integração COM+.  
  
 \<system.ServiceModel>  
\<comContracts>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<comContracts>  
  <comContract  
      contract="string"  
      namespace="string"  
      name="string"  
      requireSession="Boolean">  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
      <userDefinedTypes>  
         <userDefinedType name="string"  
            typeLibID="string"  
            typeLibVersion="string"  
            typeDefID="string">  
         </userDefinedType>  
      </userDefinedTypes>  
      <persistableTypes>  
         <persistableType id="string"  
            name="string">  
         </persistableType>  
      </persistableTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|contrato|Uma cadeia de caracteres que contém o tipo de contrato.|  
|name|Uma cadeia de caracteres que contém o nome do contrato.|  
|namespace|Uma cadeia de caracteres que contém o namespace de contrato.|  
|requiresSession|Um valor booliano que especifica se o contrato só pode ser usado em associações de sessão. Quando o serviço é inicializado, o integration runtime garante que essa configuração é consistente com o tipo de associação a ser usada. Uma exceção será gerada se um ou mais das associações para o contrato estão em conflito. Se essa propriedade for `false`e um canal unidirecional está em uso e houver [parâmetros out], também será gerada uma exceção.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|persistableTypes|Todos os tipos persistentes.|  
|userDefinedTypes|Uma coleção de usuário definidos UDTS (tipos) que deve ser incluído no contrato de serviço.|  
|exposedMethods|Uma coleção de métodos COM+ que são expostos quando a interface em um componente COM+ é exposta como um serviço Web.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|comContracts|Contém uma coleção de `comContract` elementos.|  
  
## <a name="remarks"></a>Comentários  
 Contratos de serviço de integração COM+ são atualmente restritos ao `http://tempuri.org` namespace, e o nome do contrato é derivado da interface COM suporte. No entanto, você pode especificar alternativas usando o `comContracts` seção, bem como o `comContract` elemento no arquivo de configuração. Por exemplo, você pode usar a configuração a seguir para especificar o namespace, nome do contrato e tipos definidos pelo usuário a serem incluídos, bem como outras configurações para um contrato de serviço.  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
      <exposedMethods>  
         <exposedMethod name="BuyStock" />  
         <exposedMethod name="SellStock" />  
         <exposedMethod name="ExecuteTransaction" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
 Quando o serviço é inicializado, os namespaces especificados e os nomes de contrato são aplicados as descrições de serviço gerado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [\<comContracts>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [Integração de aplicativos COM+](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Como definir configurações de serviço COM+](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
