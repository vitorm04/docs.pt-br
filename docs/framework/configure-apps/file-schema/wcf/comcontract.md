---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: 5d6bfb1e4aa1651cd8c3a869f681d71cfb15725c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751876"
---
# <a name="comcontract"></a>\<comContract>
Especifica um contrato de serviço de integração COM+.  
  
 \<system.ServiceModel>  
\<comContracts>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<comContracts>
  <comContract contract="String"
               namespace="String"
               name="String"
               requireSession="Boolean">
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
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
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
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

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<comContracts>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [Integração de aplicativos COM+](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [Como: Definir as configurações de serviço COM+](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
