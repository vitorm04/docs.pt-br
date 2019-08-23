---
title: <comContracts>
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: d061d48374a8745dc61e1ca156e4fcbbccee5ef7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919482"
---
# <a name="comcontracts"></a>\<comContracts>
A `comContracts` seção de configuração contém elementos que permitem especificar várias propriedades de um contrato de serviço de integração com+.  
  
## <a name="specifying-namespace-and-contract"></a>Especificando o namespace e o contrato  
 Os contratos do serviço de `http://tempuri.org` integração com+ estão atualmente restritos ao namespace e o nome do contrato é derivado da interface com de suporte. No entanto, você pode especificar alternativas usando a `comContracts` seção no arquivo de configuração.  
  
 Por exemplo, você pode usar a configuração a seguir para especificar o namespace e o nome do contrato do contrato de serviço, bem como uma opção para impor o uso em associações de sessão.  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 Quando o serviço é inicializado, os namespaces e os nomes de contrato especificados são aplicados às descrições de serviço geradas.  
  
 Quando esta seção estiver vazia, a inicialização do serviço aplicará um namespace padrão e o nome do contrato extraído da ID de interface COM de suporte.  
  
 Além disso, você pode usar o [ \<elemento ExposedMethod >](exposedmethod.md) para especificar métodos com+ que são expostos quando a interface em um componente com+ é exposta como um serviço Web. Você também pode usar o [ \<> persistableTypes](persistabletypes.md) para especificar tipos persistentes usados na integração. Por fim, você pode usar o elemento [ \<UserDefinedType >](userdefinedtype.md) para incluir os UDT (tipos definidos pelo usuário) que devem ser incluídos no contrato de serviço.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<exposedMethod>](exposedmethod.md)
- [\<persistableTypes>](persistabletypes.md)
- [\<userDefinedType>](userdefinedtype.md)
- [\<comContract>](comcontract.md)
- [Integração de aplicativos COM+](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [Como: Definir configurações de serviço COM+](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
