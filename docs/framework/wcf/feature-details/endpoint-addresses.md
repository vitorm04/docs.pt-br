---
title: "Endereços do ponto de extremidade"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- addresses [WCF]
- Windows Communication Foundation [WCF], addresses
- WCF [WCF], addresses
ms.assetid: 13f269e3-ebb1-433c-86cf-54fbd866a627
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 94610842cd801a54bba0266a4f658d8a4bb60dcd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-addresses"></a>Endereços do ponto de extremidade
Cada ponto de extremidade tem um endereço associado a ele, que é usado para localizar e identificar o ponto de extremidade. Esse endereço consiste principalmente de um URI Uniform Resource Identifier (), que especifica o local do ponto de extremidade. O endereço do ponto de extremidade é representado no [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] modelo de programação com o <xref:System.ServiceModel.EndpointAddress> classe, que contém um recurso opcional <xref:System.ServiceModel.EndpointAddress.Identity%2A> propriedade que permite a autenticação do ponto de extremidade por outros pontos de extremidade que trocam mensagens com ele e um conjunto de opcional <xref:System.ServiceModel.EndpointAddress.Headers%2A> propriedades que definem outros cabeçalhos SOAP necessários para acessar o serviço. Os cabeçalhos opcionais fornecem adicionais e informações de endereçamento para identificar ou interagir com o ponto de extremidade de serviço mais detalhadas. O endereço de um ponto de extremidade é representado na transmissão como uma referência de ponto de extremidade WS-Addressing (EPR).  
  
## <a name="uri-structure-of-an-address"></a>Estrutura de um endereço de URI  
 O endereço de URI para a maioria dos transportes tem quatro partes. Por exemplo, as quatro partes do URI http://www.fabrikam.com:322/mathservice.svc/secureEndpoint podem ser especificadas da seguinte maneira:  
  
-   Esquema: http:  
  
-   Máquina: www.fabrikam.com  
  
-   (opcional) Porta: 322  
  
-   Caminho: /mathservice.svc/secureEndpoint  
  
## <a name="defining-an-address-for-a-service"></a>Definir um endereço para um serviço  
 O endereço de ponto de extremidade para um serviço pode ser especificado imperativa usando código ou declarativamente por meio de configuração. Definir pontos de extremidade no código geralmente não é prático porque as associações e os endereços para um serviço implantado normalmente são diferentes daqueles usados enquanto o serviço está sendo desenvolvido. Geralmente, é mais prático definir pontos de extremidade de serviço usando a configuração em vez do código. Informações sem o código de endereçamento e manter a associação permite que a alteração sem precisar recompilar ou reimplantar o aplicativo.  
  
### <a name="defining-an-address-in-configuration"></a>Definindo um endereço na configuração  
 Para definir um ponto de extremidade em um arquivo de configuração, use o [ \<ponto de extremidade >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elemento. Para obter detalhes e um exemplo, consulte [especificando um endereço de ponto de extremidade](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
### <a name="defining-an-address-in-code"></a>Definindo um endereço no código  
 Um endereço de ponto de extremidade pode ser criado em código com o <xref:System.ServiceModel.EndpointAddress> classe. Para obter detalhes e um exemplo, consulte [especificando um endereço de ponto de extremidade](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
### <a name="endpoints-in-wsdl"></a>Pontos de extremidade no WSDL  
 Um endereço de ponto de extremidade também pode ser representado em WSDL como um elemento WS-Addressing EPR dentro do ponto de extremidade correspondente `wsdl:port` elemento. O EPR contém o endereço do ponto de extremidade, bem como as propriedades do endereço. Para obter detalhes e um exemplo, consulte [especificando um endereço de ponto de extremidade](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
## <a name="multiple-iis-binding-support-in-net-framework-35"></a>Vários IIS associação suporte no .NET Framework 3.5  
 Provedores de serviços de Internet geralmente hospedam vários aplicativos no mesmo servidor e no site para aumentar a densidade do site e o custo total de propriedade. Normalmente, esses aplicativos são associados a endereços base diferentes. Um site de serviços de informações da Internet (IIS) pode conter vários aplicativos. Os aplicativos em um site podem ser acessados por meio de um ou mais associações de IIS.  
  
 Associações do IIS fornecem duas informações: um protocolo de associação e informações de associação. O protocolo de associação define o esquema durante o qual a comunicação ocorre, e informações de associação são as informações usadas para acessar o site.  
  
 O exemplo a seguir mostra os componentes que podem estar presentes em uma associação do IIS:  
  
-   Associação de protocolo: HTTP  
  
-   Informações de associação: Endereço IP, porta, o cabeçalho de Host  
  
 O IIS pode especificar várias associações para cada site, o que resulta em vários endereços de base para cada esquema. Antes de [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não oferecia suporte a vários endereços para um esquema e, se eles forem especificados, gerou um <xref:System.ArgumentException> durante a ativação.  
  
 O [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] permite que provedores de serviços de Internet hospedar vários aplicativos com diferentes endereços base para o mesmo esquema no mesmo site.  
  
 Por exemplo, um site pode conter os seguintes endereços de base:  
  
-   http://Payroll.myorg.com/Service.svc  
  
-   http://Shipping.myorg.com/Service.svc  
  
 Com [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], você especificar um filtro de prefixo no nível do AppDomain no arquivo de configuração. Você pode fazer isso a [ \<baseAddressPrefixFilters >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) elemento, que contém uma lista de prefixos. Os endereços base entrados fornecidos pelo IIS, são filtrados com base na lista de prefixo opcional. Por padrão, quando um prefixo não for especificado, todos os endereços são passados. Especificando os resultados de prefixo apenas o endereço base correspondente para esse esquema deverá ser passado.  
  
 Este é um exemplo de código de configuração que usa os filtros de prefixo.  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://payroll.myorg.com:8000"/>  
        <add prefix="http://shipping.myorg.com:8000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 No exemplo anterior, net.tcp://payroll.myorg.com: 8000 e http://shipping.myorg.com:8000 são os endereços base apenas, para seus respectivos esquemas, que são passados.  
  
 O `baseAddressPrefixFilter` não dá suporte a curingas.  
  
 Os endereços de base fornecidos pelo IIS podem ter endereços associados a outros esquemas não está presentes na `baseAddressPrefixFilters` lista. Esses endereços não serão filtrados.  
  
## <a name="multiple-iis-binding-support-in-net-framework-4-and-later"></a>Vários IIS suporte a associação no .NET Framework 4 e posterior  
 A partir do .NET 4, você pode habilitar o suporte para várias associações do IIS sem a necessidade de selecionar um único endereço de base, definindo <xref:System.ServiceModel.ServiceHostingEnvironment>do <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> definição como true. Esse suporte é limitado a esquemas de protocolo HTTP.  
  
 A seguir está um exemplo de código de configuração que usa multipleSiteBindingsEnabled [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md).  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment multipleSiteBindingsEnabled="true" >  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 As configurações de baseAddressPrefixFilters são ignoradas, para HTTP e protocolos não HTTP, quando várias associações de site estão habilitadas para usar essa configuração.  
  
 Para obter detalhes e exemplos, consulte [dando suporte a várias associações de Site IIS](../../../../docs/framework/wcf/feature-details/supporting-multiple-iis-site-bindings.md) e <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A>.  
  
## <a name="extending-addressing-in-wcf-services"></a>Estendendo o endereçamento nos serviços do WCF  
 O modelo de endereçamento padrão de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services usa o endereço de ponto de extremidade URI para as seguintes finalidades:  
  
-   Para especificar o endereço de escuta do serviço, o local em que o ponto de extremidade de escuta para mensagens,  
  
-   Para especificar o filtro de endereço SOAP, o endereço de um ponto de extremidade espera como um cabeçalho SOAP.  
  
 Os valores para cada um desses fins podem ser especificados separadamente, permitindo que várias extensões de endereçamento que abrange útil cenários:  
  
-   Intermediários SOAP: uma mensagem enviada por um cliente atravessa um ou mais serviços adicionais que processam a mensagem antes de atingir seu destino final. Intermediários SOAP podem executar várias tarefas, como a validação de armazenamento em cache, roteamento, balanceamento de carga ou esquema nas mensagens. Este cenário é feito enviando mensagens para um endereço físico separado (`via`) que tem como alvo o intermediário em vez de apenas para um endereço lógico (`wsa:To`) que tem como alvo o destino final.  
  
-   O endereço de escuta do ponto de extremidade é um URI privado e é definido como um valor diferente de seu `listenURI` propriedade.  
  
 O transporte de endereço que o `via` Especifica o local para o qual uma mensagem deve ser enviada inicialmente até chegar a um outro endereço remoto especificado pelo `to` parâmetro em que o serviço está localizado. Na maioria dos cenários de Internet, o `via` URI é igual a <xref:System.ServiceModel.EndpointAddress.Uri%2A> propriedade final `to` endereço do serviço. Você só distinguir entre esses dois endereços quando você deve fazer o roteamento manual.  
  
### <a name="addressing-headers"></a>Cabeçalhos de endereçamento  
 Um ponto de extremidade pode ser tratado por um ou mais cabeçalhos SOAP, além de seu URI básico. Um conjunto de cenários em que isso é útil é um conjunto de cenários de intermediários SOAP em que um ponto de extremidade exige que os clientes do ponto de extremidade incluir cabeçalhos de SOAP direcionados a intermediários.  
  
 Você pode definir cabeçalhos de endereço personalizado de duas maneiras: usando a configuração ou código:  
  
-   No código, crie os cabeçalhos de endereço personalizado usando o <xref:System.ServiceModel.Channels.AddressHeader> classe e, em seguida, usada na construção de um <xref:System.ServiceModel.EndpointAddress>.  
  
-   Na configuração, personalizada [ \<cabeçalhos >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) são especificados como filhos do [ \<ponto de extremidade >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) elemento.  
  
 Configuração geralmente é preferível para o código, que permite a você alterar os cabeçalhos após a implantação.  
  
### <a name="custom-listening-addresses"></a>Endereços de escutando personalizados  
 Você pode definir o endereço de escuta para um valor diferente de URI do ponto de extremidade. Isso é útil em cenários intermediários onde o endereço SOAP a ser exposto é que um público SOAP intermediário, enquanto o endereço onde o ponto de extremidade de escuta, na verdade, é um endereço de rede privada.  
  
 Você pode especificar um endereço de escutando personalizado usando a configuração ou código:  
  
-   No código, especifique um endereço de escutando personalizado adicionando um <xref:System.ServiceModel.Description.ClientViaBehavior> classe à coleção de comportamento do ponto de extremidade.  
  
-   Em configuração, especifique um endereço de escutando personalizado com o `ListenUri` atributo do serviço [ \<ponto de extremidade >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) elemento.  
  
### <a name="custom-soap-address-filter"></a>Filtro de endereço SOAP personalizado  
 O <xref:System.ServiceModel.EndpointAddress.Uri%2A> é usada em conjunto com nenhum <xref:System.ServiceModel.EndpointAddress.Headers%2A> propriedade para definir o filtro de endereço de um ponto de extremidade SOAP (<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A>). Por padrão, esse filtro verifica se uma mensagem de entrada tem um `To` cabeçalho da mensagem que coincide com o ponto de extremidade do URI e que todos os cabeçalhos de ponto de extremidade necessários estão presentes na mensagem.  
  
 Em alguns cenários, um ponto de extremidade recebe todas as mensagens que chegam no transporte subjacente e não apenas aquelas com apropriada `To` cabeçalho. Para habilitar isso, o usuário pode usar o <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> classe.  
  
## <a name="see-also"></a>Consulte também  
 [Especificando um endereço do ponto de extremidade](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
 [Autenticação e identidade de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
