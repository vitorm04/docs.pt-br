---
title: Escolhendo um filtro
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: 91b3802217a920ef3eeeccb5c4f85c66afee2430
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494121"
---
# <a name="choosing-a-filter"></a>Escolhendo um filtro
Ao configurar o serviço de roteamento, é importante selecionar filtros de mensagem correto e configurá-los para permitir que você faça correspondências exatas contra as mensagens recebidas. Se os filtros que você seleciona são demasiadamente amplos em suas correspondências ou estão configurados incorretamente, as mensagens são roteadas incorretamente. Se os filtros são muito restritivos, talvez você não tenha nenhuma rota válida disponível para algumas das suas mensagens.  
  
## <a name="filter-types"></a>Tipos de filtro  
 Ao selecionar os filtros que são usados pelo serviço de roteamento, é importante entender como cada filtro funciona, bem como quais informações estão disponíveis como parte das mensagens de entrada. Por exemplo, se todas as mensagens são recebidas pela mesmo ponto de extremidade, os filtros de endereço e EndpointName não são úteis porque esses filtros correspondem a todas as mensagens.  
  
### <a name="action"></a>Ação  
 O filtro de ação inspeciona o <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> propriedade. Se o conteúdo do cabeçalho de ação na mensagem corresponde ao valor de dados do filtro especificado na configuração do filtro, esse filtro retorna `true`. O exemplo a seguir define uma `FilterElement` que usa o filtro de ação para corresponder as mensagens com um cabeçalho de ação que contém um valor de "http://namespace/contract/operation/".  
  
```xml  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />  
```  
  
```csharp  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
```  
  
 Este filtro deve ser usado quando o roteamento de mensagens que contêm um cabeçalho de ação exclusivo.  
  
### <a name="endpointaddress"></a>EndpointAddress  
 O filtro EndpointAddress inspeciona o EndpointAddress que a mensagem foi recebida. Se o endereço que a mensagem chegar ao exatamente corresponde ao endereço de filtro especificado na configuração do filtro, esse filtro retorna `true`. O exemplo a seguir define uma `FilterElement` que usa o filtro de endereço para correspondência de todas as mensagens destinadas a "http://\<hostname > / vdir/s.svc/b".  
  
```xml  
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  É importante observar que a parte do nome de host de um endereço pode ser diferente com base em se o cliente usa o nome de domínio totalmente qualificado, o nome NetBIOS, o endereço IP ou outro nome. Porque valores diferentes podem referir-se para o mesmo host, o comportamento padrão para essa comparação é não usar a parte do nome de host do endereço ao executar correspondências.  
>   
>  Esse comportamento pode ser modificado para permitir que a comparação avaliar o nome do host ao configurar o serviço de roteamento por meio de programação.  
  
 O filtro deve ser usado quando as mensagens de entrada são enviadas a um endereço exclusivo.  
  
### <a name="endpointaddressprefix"></a>EndpointAddressPrefix  
 O filtro de EndpointAddressPrefix é semelhante ao filtro EndpointAddress. O filtro EndpointAddressPrefix inspeciona o EndpointAddress que a mensagem foi recebida. No entanto o filtro EndpointAddressPrefix atua como um curinga correspondendo endereços que começam com o valor especificado na configuração do filtro. O exemplo a seguir define uma `FilterElement` que usa o filtro de EndpointAddressPrefix para corresponder a todas as mensagens destinadas a "http://\<hostname > / vdir *".  
  
```xml  
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />  
```  
  
```csharp  
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  É importante observar que a parte do nome de host de um endereço pode ser diferente com base em se o cliente usa o nome de domínio totalmente qualificado, o nome NetBIOS, o endereço IP ou outro nome. Porque valores diferentes podem referir-se para o mesmo host, o comportamento padrão para essa comparação é não usar a parte do nome de host do endereço ao executar correspondências.  
  
 O filtro deve ser usado ao rotear mensagens de entrada que compartilham um prefixo de endereço comum.  
  
### <a name="and"></a>AND  
 O filtro e não filtra diretamente em um valor dentro de uma mensagem, mas permite que você combine os dois outros filtros para criar um `AND` condição em que ambos os filtros devem corresponder a mensagem antes do filtro e é avaliada como `true`. Isso permite que você crie filtros complexos que correspondem somente se correspondem a todos os filtros de subtipo. O exemplo a seguir define um filtro de ação e um filtro de endereço e, em seguida, define um filtro e que é avaliada uma mensagem com o endereço e a ação de filtros. Se o endereço e os filtros de ação corresponderem, o filtro e retornará `true`.  
  
```xml  
<filter name="address1" filterType="AddressPrefix" filterData="http://host/vdir"/>  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/"/>  
<filter name="and1" filterType="And" filter1="address1" filter2="action1" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
StrictAndMessageFilter and1=new StrictAndMessageFilter(address1, action1);  
```  
  
 O filtro deve ser usado quando você precisar combinar a lógica de vários filtros para determinar quando uma correspondência deve ser feita. Por exemplo, se você tiver vários destinos que devem receber apenas algumas combinações de ações e mensagens para endereços específicos, você pode usar um filtro e combinar os filtros de ação e o endereço necessário.  
  
### <a name="custom"></a>Personalizado  
 Ao selecionar o tipo de filtro personalizado, você deve fornecer um valor de customType que contém o tipo do assembly que contém o **MessageFilter** implementação a ser usado para esse filtro. Além disso, filterData deve conter valores que o filtro personalizado pode exigir de sua avaliação de mensagens. O exemplo a seguir define uma `FilterElement` que usa o `CustomAssembly.MyCustomMsgFilter` MessageFilter implementação.  
  
```xml  
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />  
```  
  
```csharp  
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");  
```  
  
 Se você precisa executar lógica personalizada de correspondência em relação a uma mensagem que não é coberta por filtros fornecidos com [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], você deve criar um filtro personalizado que é uma implementação do **MessageFilter** classe. Por exemplo, você pode criar um filtro personalizado, que compara um campo na mensagem de entrada em uma lista de valores conhecidos, fornecido para o filtro de configuração, ou que realiza hash de um elemento de mensagem específica e, em seguida, examina esse valor para determinar se o filtro deve retornar `true` ou `false`.  
  
### <a name="endpointname"></a>EndpointName  
 O filtro EndpointName verifica se o nome do ponto de extremidade que recebeu a mensagem. O exemplo a seguir define um `FilterElement` que usa o filtro de EndpointName para rotear mensagens recebidas em "SvcEndpoint".  
  
```xml  
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />  
```  
  
```csharp  
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");  
```  
  
 Esse filtro é útil quando o serviço de roteamento expõe mais de um ponto de extremidade de serviço nomeado. Por exemplo, você poderá expor dois pontos de extremidade que usa o serviço de roteamento para receber mensagens. um é usado por clientes de prioridade que necessitam de tempo real de processamento de suas mensagens, enquanto o outro ponto de extremidade recebe mensagens que não são tempo sensível.  
  
 Embora muitas vezes você pode usar completo endereço de correspondência para determinar qual ponto de extremidade foi recebida uma mensagem, usando o nome do ponto de extremidade definido em vez disso, é um atalho prático que geralmente é menos propenso, especialmente ao configurar um serviço de roteamento de mensagens usando uma configuração arquivo (em que os nomes de ponto de extremidade são um atributo necessário).  
  
### <a name="matchall"></a>MatchAll  
 O filtro MatchAll faz a correspondência de qualquer mensagem recebida. É útil se você sempre deve rotear todas as mensagens recebidas para um ponto de extremidade específico, como um serviço de registro em log que armazena uma cópia de todas as mensagens recebidas. O exemplo a seguir define um `FilterElement` que usa o filtro de MatchAll.  
  
```xml  
<filter name="matchAll1" filterType="MatchAll" />  
```  
  
```csharp  
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();  
```  
  
### <a name="xpath"></a>XPath  
 O filtro XPath permite que você especifique uma consulta XPath que é usada para inspecionar um elemento específico dentro da mensagem. A filtragem de XPath é uma opção de filtragem avançada que permite que você inspecione diretamente qualquer entrada endereçável XML dentro da mensagem; No entanto, ele exige que você tenha conhecimento específico da estrutura de mensagens que você está recebendo. O exemplo a seguir define um `FilterElement` que usa o filtro XPath para inspecionar a mensagem para um elemento denominado "element" dentro do namespace referenciado pelo prefixo de namespace "ns".  
  
```xml  
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />  
```  
  
```csharp  
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");  
```  
  
 Esse filtro é útil se você souber que as mensagens que você está recebendo contêm um valor específico. Por exemplo, se você estiver hospedando as duas versões do mesmo serviço e você souber que as mensagens destinadas para a versão mais recente do serviço contém um valor exclusivo em um cabeçalho personalizado, você pode criar um filtro que usa o XPath para navegar para esse cabeçalho e compara a valor de pré-instalação ENT no cabeçalho para outro dado na configuração de filtro para determinar se o filtro corresponde.  
  
 Como as consultas XPath geralmente contêm namespaces exclusivos, que geralmente são longos ou valores de cadeia de caracteres complexa, o filtro XPath permite que você use a tabela de namespace para definir os prefixos exclusivos para seus namespaces. Para obter mais informações sobre a tabela de namespace, consulte [filtros de mensagem](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
 Para obter mais informações sobre como criar consultas XPath, consulte [sintaxe XPath](http://go.microsoft.com/fwlink/?LinkId=164592).  
  
## <a name="see-also"></a>Consulte também  
 [Filtros de mensagem](../../../../docs/framework/wcf/feature-details/message-filters.md)  
 [Como usar filtros](../../../../docs/framework/wcf/feature-details/how-to-use-filters.md)
