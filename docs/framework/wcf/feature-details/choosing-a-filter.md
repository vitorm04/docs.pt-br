---
title: Escolhendo um filtro
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: bc3bba9a2b00b35f3e0cff1786ea98cfa881f311
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43743132"
---
# <a name="choosing-a-filter"></a>Escolhendo um filtro
Ao configurar o serviço de roteamento, é importante selecionar os filtros de mensagem correta e configurá-los para que você possa fazer as correspondências exatas nas mensagens recebidas. Se os filtros que você seleciona são excessivamente amplas em suas correspondências ou estão configurados incorretamente, mensagens são roteadas incorretamente. Se os filtros são muito restritivos, você não pode ter nenhuma rota válida disponível para algumas de suas mensagens.  
  
## <a name="filter-types"></a>Tipos de filtro  
 Ao selecionar os filtros que são usados pelo serviço de roteamento, é importante que você compreenda o funcionamento de cada filtro, bem como quais informações estão disponíveis como parte das mensagens de entrada. Por exemplo, se todas as mensagens são recebidas ao longo do mesmo ponto de extremidade, os filtros de endereço e EndpointName não são úteis porque todas as mensagens coincidam com estes filtros.  
  
### <a name="action"></a>Ação  
 O filtro de ação inspeciona o <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> propriedade. Se o conteúdo do cabeçalho da ação na mensagem corresponde ao valor de dados do filtro especificado na configuração do filtro e, em seguida, retorna esse filtro `true`. O exemplo a seguir define uma `FilterElement` que usa o filtro de ação para corresponder as mensagens com um cabeçalho de ação que contém um valor de "http://namespace/contract/operation/".  
  
```xml  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />  
```  
  
```csharp  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
```  
  
 Esse filtro deve ser usado ao rotear mensagens que contêm um cabeçalho de ação exclusivo.  
  
### <a name="endpointaddress"></a>EndpointAddress  
 O filtro EndpointAddress inspeciona o EndpointAddress que a mensagem foi recebida no. Se o endereço que a mensagem chega ao exatamente corresponde ao endereço de filtro especificado na configuração do filtro e, em seguida, retorna esse filtro `true`. O exemplo a seguir define uma `FilterElement` que usa o filtro de endereço para correspondência de todas as mensagens endereçadas a "http://\<nome do host > / vdir/s.svc/b".  
  
```xml  
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  É importante observar que a parte do nome de host de um endereço pode diferir com base em se o cliente usa o nome de domínio totalmente qualificado, o nome NetBIOS, o endereço IP ou outro nome. Como os valores de diferentes podem referir-se para o mesmo host, o comportamento padrão para essa comparação é não usar a parte do nome de host do endereço ao executar correspondências.  
>   
>  Esse comportamento pode ser modificado para permitir a comparação avaliar o nome do host ao configurar o serviço de roteamento por meio de programação.  
  
 Esse filtro deve ser usado quando as mensagens de entrada endereçadas para um endereço exclusivo.  
  
### <a name="endpointaddressprefix"></a>EndpointAddressPrefix  
 O filtro EndpointAddressPrefix é semelhante ao filtro EndpointAddress. O filtro EndpointAddressPrefix inspeciona o EndpointAddress que a mensagem foi recebida no. No entanto o filtro EndpointAddressPrefix atua como um caractere curinga por correspondência de endereços que começam com o valor especificado na configuração de filtro. O exemplo a seguir define uma `FilterElement` que usa o filtro de EndpointAddressPrefix para corresponder a todas as mensagens endereçadas a "http://\<nome do host > / vdir *".  
  
```xml  
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />  
```  
  
```csharp  
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  É importante observar que a parte do nome de host de um endereço pode diferir com base em se o cliente usa o nome de domínio totalmente qualificado, o nome NetBIOS, o endereço IP ou outro nome. Como os valores de diferentes podem referir-se para o mesmo host, o comportamento padrão para essa comparação é não usar a parte do nome de host do endereço ao executar correspondências.  
  
 Esse filtro deve ser usado ao rotear mensagens de entrada que compartilham um prefixo de endereço comum.  
  
### <a name="and"></a>AND  
 O filtro AND não filtra diretamente em um valor dentro de uma mensagem, mas permite que você combine os dois outros filtros para criar uma `AND` condição em que ambos os filtros devem corresponder a mensagem antes que o filtro e é avaliada como `true`. Isso permite que você crie filtros complexos que correspondem somente se correspondem a todos os filtros de subpropriedades. O exemplo a seguir define um filtro de endereço e um filtro de ação e, em seguida, define um filtro e que é avaliada uma mensagem com base nos filtros de endereço e a ação. Se o endereço e os filtros de ação corresponderem, o filtro AND retornará `true`.  
  
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
  
 Esse filtro deve ser usado quando é necessário combinar a lógica de vários filtros para determinar quando uma correspondência deve ser feita. Por exemplo, se você tiver vários destinos que devem receber somente determinadas combinações de ações e mensagens para endereços específicos, você pode usar um filtro AND para combinar os filtros de ação e o endereço necessário.  
  
### <a name="custom"></a>Personalizado  
 Ao selecionar o tipo de filtro personalizado, você deve fornecer um valor de customType que contém o tipo do assembly que contém o **MessageFilter** implementação a ser usado para esse filtro. Além disso, filterData deve conter todos os valores que o filtro personalizado pode exigir de sua avaliação de mensagens. O exemplo a seguir define uma `FilterElement` que usa o `CustomAssembly.MyCustomMsgFilter` implementação de MessageFilter.  
  
```xml  
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />  
```  
  
```csharp  
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");  
```  
  
 Se você precisa executar lógica correspondente personalizada em relação a uma mensagem que não é coberta pelos filtros fornecidos com [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], você deve criar um filtro personalizado que é uma implementação do **MessageFilter** classe. Por exemplo, você pode criar um filtro personalizado, que compara um campo na mensagem de entrada em relação a uma lista de valores conhecidos fornecido para o filtro como configuração, ou que faz o hash de um elemento de mensagem específica e, em seguida, examina esse valor para determinar se o filtro deve retornar `true` ou `false`.  
  
### <a name="endpointname"></a>EndpointName  
 O filtro EndpointName inspeciona o nome do ponto de extremidade que recebeu a mensagem. O exemplo a seguir define uma `FilterElement` que usa o filtro de EndpointName para rotear mensagens recebidas em "SvcEndpoint".  
  
```xml  
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />  
```  
  
```csharp  
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");  
```  
  
 Esse filtro é útil quando o serviço de roteamento expõe mais de um ponto de extremidade de serviço nomeado. Por exemplo, você pode expor os dois pontos de extremidade usados pelo serviço de roteamento para receber mensagens. um é usado por clientes de prioridade que exigem processamento de suas mensagens, enquanto outro ponto de extremidade em tempo real recebe mensagens que não são tempo minúsculas.  
  
 Embora muitas vezes você pode usar completo endereço de correspondência para determinar qual ponto de extremidade foi recebida uma mensagem, usando o nome do ponto de extremidade definido em vez disso, é um atalho conveniente que geralmente é menos sujeita a erros, especialmente ao configurar um serviço de roteamento usando uma configuração arquivo (em que os nomes de ponto de extremidade são um atributo necessário).  
  
### <a name="matchall"></a>MatchAll  
 O filtro de MatchAll corresponde a qualquer mensagem recebida. É útil se você sempre deve rotear todas as mensagens recebidas para um ponto de extremidade específico, como um serviço de registro em log que armazena uma cópia de todas as mensagens recebidas. O exemplo a seguir define uma `FilterElement` que usa o filtro de MatchAll.  
  
```xml  
<filter name="matchAll1" filterType="MatchAll" />  
```  
  
```csharp  
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();  
```  
  
### <a name="xpath"></a>XPath  
 O filtro XPath permite que você especifique uma consulta XPath que é usada para inspecionar um elemento específico dentro da mensagem. A filtragem de XPath é uma opção de filtragem poderosa que permite que você inspecione diretamente qualquer entrada endereçável de XML dentro da mensagem; No entanto, ele exige que você tenha conhecimento específico da estrutura das mensagens que você está recebendo. O exemplo a seguir define uma `FilterElement` que usa o filtro XPath para inspecionar a mensagem para um elemento denominado "element" dentro do namespace referenciado pelo prefixo de namespace "ns".  
  
```xml  
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />  
```  
  
```csharp  
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");  
```  
  
 Esse filtro é útil se você souber que as mensagens que você está recebendo contêm um valor específico. Por exemplo, se você estiver hospedando as duas versões do mesmo serviço e você souber que as mensagens endereçadas para a versão mais recente do serviço contenham um valor exclusivo em um cabeçalho personalizado, você pode criar um filtro que usa o XPath para navegar para esse cabeçalho e compara a valor de pré-instalação ENT no cabeçalho para outro fornecido na configuração de filtro para determinar se o filtro corresponde.  
  
 Como as consultas XPath geralmente contêm namespaces exclusivos, que geralmente são longos ou valores de cadeia de caracteres complexa, o filtro XPath permite que você use a tabela de namespace para definir os prefixos exclusivos para seus namespaces. Para obter mais informações sobre a tabela de namespace, consulte [filtros de mensagem](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
 Para obter mais informações sobre a criação de consultas XPath, consulte [sintaxe XPath](https://go.microsoft.com/fwlink/?LinkId=164592).  
  
## <a name="see-also"></a>Consulte também  
 [Filtros de mensagem](../../../../docs/framework/wcf/feature-details/message-filters.md)  
 [Como usar filtros](../../../../docs/framework/wcf/feature-details/how-to-use-filters.md)
