---
title: <serviceDebug>
ms.date: 03/30/2017
ms.assetid: 6d7ea986-f232-49fe-842c-f934d9966889
ms.openlocfilehash: 7b7526dbcbd1948d3d8a27d146efd0462fefaca5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788434"
---
# <a name="servicedebug"></a>\<serviceDebug>
Especifica os recursos de informações de depuração e ajuda para um serviço do Windows Communication Foundation (WCF).  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors>  
\<behavior>  
\<serviceDebug>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<serviceDebug httpHelpPageBinding="String"
              httpHelpPageBindingConfiguration="String"
              httpHelpPageEnabled="Boolean"
              httpHelpPageUrl="Uri"
              httpsHelpPageBinding="String"
              httpsHelpPageBindingConfiguration="String"
              httpsHelpPageEnabled="Boolean"
              httpsHelpPageUrl="Uri"
              includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|httpHelpPageBinding|Um valor de cadeia de caracteres que especifica o tipo de associação a ser usada quando HTTP é utilizado para acessar a página de Ajuda do serviço.<br /><br /> Somente associações com elementos de associação interna que dão suporte a <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> terão suporte. Além disso, o <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> propriedade da associação deve ser <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.|  
|httpHelpPageBindingConfiguration|Uma cadeia de caracteres que especifica o nome da associação que é especificado no `httpHelpPageBinding` atributo, o que faz referência às informações de configuração adicionais desta associação. O mesmo nome deve ser definido no `<bindings>` seção.|  
|httpHelpPageEnabled|Um valor booliano que controla se WCF publica uma página de ajuda HTML no endereço especificado pelo `httpHelpPageUrl` atributo. O padrão é `true`.<br /><br /> Você pode definir essa propriedade `false` para desabilitar a publicação de uma página de ajuda HTML visível para navegadores HTML.<br /><br /> Para garantir que a Ajuda HTML a página for publicada no local controlado pela `httpHelpPageUrl` atributo, você deve definir esse atributo para `true`. Além disso, uma das seguintes condições deve também ser atendida:<br /><br /> -O `httpHelpPageUrl` atributo é um endereço absoluto que dá suporte ao esquema de protocolo HTTP.<br />-Há um endereço base para o serviço que dá suporte ao esquema de protocolo HTTP.<br /><br /> Embora uma exceção é lançada se um endereço absoluto que não oferece suporte para o esquema de protocolo HTTP é atribuído para o `httpHelpPageUrl` de atributo, qualquer outro cenário no qual nenhum dos critérios anteriores for atendida resulta em nenhuma exceção e nenhuma página de ajuda HTML.|  
|httpHelpPageUrl|Um URI que especifica a URL relativa ou absoluta baseada em HTTP, de HTML personalizado ajudar o usuário vê de arquivo quando o ponto de extremidade é exibido usando um navegador HTML.<br /><br /> Você pode usar esse atributo para habilitar o uso de um arquivo de ajuda HTML personalizado que é retornado por uma solicitação HTTP/Get, por exemplo, em um navegador HTML. O local do arquivo de ajuda HTML é resolvido da seguinte maneira.<br /><br /> 1.  Se o valor desse atributo é um endereço relativo, o local do arquivo de ajuda HTML é o valor do endereço base serviço que dá suporte a solicitações HTTP, além desse valor de propriedade.<br />2.  Se o valor desse atributo é um endereço absoluto e dá suporte a solicitações HTTP, o local do arquivo de ajuda HTML é o valor dessa propriedade.<br />3.  Se o valor desse atributo é absoluto, mas não oferece suporte a solicitações HTTP, uma exceção é lançada.<br /><br /> Esse atributo é válido somente quando o `httpHelpPageEnabled` atributo é `true`.|  
|httpsHelpPageBinding|Um valor de cadeia de caracteres que especifica o tipo de associação a ser usada quando HTTPS é utilizado para acessar a página de Ajuda do serviço.<br /><br /> Somente associações com elementos de associação interna que dão suporte a <xref:System.ServiceModel.Channels.IReplyChannel> terão suporte. Além disso, o <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> propriedade da associação deve ser <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.|  
|httpsHelpPageBindingConfiguration|Uma cadeia de caracteres que especifica o nome da associação que é especificado no `httpsHelpPageBinding` atributo, o que faz referência às informações de configuração adicionais desta associação. O mesmo nome deve ser definido no `<bindings>` seção.|  
|httpsHelpPageEnabled|Um valor booliano que controla se WCF publica uma página de ajuda HTML no endereço especificado pelo `httpsHelpPageUrl` atributo. O padrão é `true`.<br /><br /> Você pode definir essa propriedade `false` para desabilitar a publicação de uma página de ajuda HTML visível para navegadores HTML.<br /><br /> Para garantir que a Ajuda HTML a página for publicada no local controlado pela `httpsHelpPageUrl` atributo, você deve definir esse atributo para `true`. Além disso, uma das seguintes condições deve também ser atendida:<br /><br /> -O `httpsHelpPageUrl` atributo é um endereço absoluto que dá suporte ao esquema de protocolo HTTPS.<br />-Há um endereço base para o serviço que dá suporte ao esquema de protocolo HTTPS.<br /><br /> Embora uma exceção é lançada se um endereço absoluto que não oferece suporte para o esquema de protocolo HTTPS for atribuído ao `httpsHelpPageUrl` de atributo, qualquer outro cenário no qual nenhum dos critérios anteriores for atendida resulta em nenhuma exceção e nenhuma página de ajuda HTML.|  
|httpsHelpPageUrl|Um URI que especifica a URL relativa ou absoluta baseada em HTTPS, de HTML personalizado ajudar o usuário vê de arquivo quando o ponto de extremidade é exibido usando um navegador HTML.<br /><br /> Você pode usar esse atributo para habilitar o uso de um arquivo de ajuda HTML personalizado que é retornado por uma solicitação HTTPS/Get, por exemplo, em um navegador HTML. O local do arquivo de ajuda HTML é resolvido da seguinte maneira:<br /><br /> -Se o valor dessa propriedade é um endereço relativo, o local do arquivo de ajuda HTML é o valor o endereço base do serviço que dá suporte a solicitações HTTPS, mais o valor dessa propriedade.<br />-Se o valor dessa propriedade é um endereço absoluto e dá suporte a solicitações HTTPS, o local do arquivo de ajuda HTML é o valor dessa propriedade.<br />-Se o valor dessa propriedade é absoluto, mas não oferece suporte a solicitações HTTPS, uma exceção é lançada.<br /><br /> Esse atributo é válido somente quando o `httpHelpPageEnabled` atributo é `true`.|  
|includeExceptionDetailInFaults|Um valor que especifica se é necessário incluir informações de exceção gerenciada nos detalhes das falhas SOAP retornadas para o cliente para fins de depuração. O padrão é `false`.<br /><br /> Se você definir esse atributo como `true`, você pode habilitar o fluxo de informações de exceção gerenciada para o cliente para fins de depuração, bem como a publicação de arquivos HTML com informações aos usuários que navegam o serviço em navegadores da Web. **Cuidado:**  Retornando informações de exceção gerenciada para os clientes podem ser um risco à segurança. Isso ocorre porque os detalhes da exceção expõem informações sobre a implementação de serviço interno que pode ser usada por clientes não autorizados.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica um elemento de comportamento.|  
  
## <a name="remarks"></a>Comentários  
 Definindo `includeExceptionDetailInFaults` à `true` permite que o serviço retornar qualquer exceção que é lançada pelo código do aplicativo, mesmo se a exceção não é declarada usando a <xref:System.ServiceModel.FaultContractAttribute>. Essa configuração é útil ao depurar casos em que o servidor está lançando uma exceção inesperada. Ao usar esse atributo, um formato serializado da exceção desconhecida é retornado e você pode examinar para obter mais detalhes da exceção.  
  
> [!CAUTION]
>  Retornando informações de exceção gerenciada para os clientes podem ser um risco à segurança porque os detalhes da exceção expõem informações sobre a implementação de serviço interno que pode ser usada por clientes não autorizados. Devido a problemas de segurança envolvida, é altamente recomendável que você fazer isso somente nos cenários de depuração controlados. Você deve definir `includeExceptionDetailInFaults` para `false` ao implantar seu aplicativo.  
  
 Para obter detalhes sobre os problemas de segurança relacionados à exceção gerenciada, consulte [especificação e tratamento de falhas em contratos e serviços](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). Para obter um exemplo de código, consulte [comportamento de depuração de serviço](../../../../../docs/framework/wcf/samples/service-debug-behavior.md).  
  
 Você também pode definir `httpsHelpPageEnabled` e `httpsHelpPageUrl` para habilitar ou desabilitar a página de Ajuda. Cada serviço, opcionalmente, pode expor uma página de Ajuda que contém informações sobre o serviço, incluindo o ponto de extremidade para obter o WSDL para o serviço. Isso pode ser habilitado configurando `httpHelpPageEnabled` para `true`. Isso permite que a página de ajuda a ser retornado para uma solicitação GET para o endereço base do serviço. Você pode alterar esse endereço, definindo o `httpHelpPageUrl` atributo. Além disso, você pode fazer isso segura usando HTTPS em vez de HTTP.  
  
 Opcional `httpHelpPageBinding` e `httpHelpPageBinding` atributos permitem que você configure as ligações usadas para acessar a página da web do serviço. Se não forem especificadas, as associações padrão (`HttpTransportBindingElement`, no caso de HTTP e `HttpsTransportBindingElement`, no caso HTTPS) são usados para acesso de página de ajuda de serviço conforme apropriado. Observe que você não pode usar esses atributos com associações do WCF internas. Somente associações com elementos de associação interna que suportam xref:System.ServiceModel.Channels.IReplyChannel > terá suporte. Além disso, o <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> propriedade da associação deve ser <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.ServiceDebugElement>
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
- [Especificando e lidando com falhas em contratos e serviços](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [Tratamento de exceções e falhas](../../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)
- [Comportamento de depuração de serviço](../../../../../docs/framework/wcf/samples/service-debug-behavior.md)
