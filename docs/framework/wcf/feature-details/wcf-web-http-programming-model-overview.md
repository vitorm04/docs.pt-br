---
title: Visão geral de modelo de programação HTTP Web do WCF
ms.date: 03/30/2017
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
ms.openlocfilehash: 9f2350b58e3cb33613ebc8e2c3cda1e234bcde25
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291741"
---
# <a name="wcf-web-http-programming-model-overview"></a>Visão geral de modelo de programação HTTP Web do WCF
O modelo de programação WEB HTTP da Windows Communication Foundation (WCF) fornece os elementos básicos necessários para construir serviços WEB HTTP com WCF. Os serviços WCF WEB HTTP foram projetados para serem acessados pela mais ampla gama de clientes possíveis, incluindo navegadores da Web e têm os seguintes requisitos exclusivos:  
  
- **Processamento de URIs e URI** As URIs desempenham um papel central no projeto dos serviços WEB HTTP. O modelo de programação WEB <xref:System.UriTemplate> HTTP <xref:System.UriTemplateTable> do WCF usa as classes e as classes para fornecer recursos de processamento uri.  
  
- **Suporte para operações GET e POST** Os serviços WEB HTTP fazem uso do verbo GET para recuperação de dados, além de vários verbos de invocação para modificação de dados e invocação remota. O modelo de programação WCF <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> WEB HTTP usa o e para associar operações de serviço com verbos GET e outros verbos HTTP como PUT, POST e DELETE.  
  
- **Vários formatos de dados** Os serviços estilo Web processam muitos tipos de dados, além de mensagens SOAP. O modelo de programação HTTP <xref:System.ServiceModel.WebHttpBinding> do <xref:System.ServiceModel.Description.WebHttpBehavior> WCF WEB usa o e para suportar muitos formatos de dados diferentes, incluindo documentos XML, objeto de dados JSON e fluxos de conteúdo binário, como imagens, arquivos de vídeo ou texto simples.  
  
 O modelo de programação WCF WEB HTTP amplia o alcance do WCF para cobrir cenários no estilo Web que incluem serviços WEB HTTP, serviços AJAX e JSON e feeds de Syndication (ATOM/RSS). Para obter mais informações sobre os serviços AJAX e JSON, consulte [a Integração AJAX e o Suporte JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md). Para obter mais informações sobre o Sindicato, consulte [WCF Syndication Overview](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md).  
  
 Não há restrições extras sobre os tipos de dados que podem ser devolvidos de um serviço WEB HTTP. Qualquer tipo serializável pode ser devolvido a partir de uma operação de serviço WEB HTTP. Como as operações de serviço WEB HTTP podem ser invocadas por um navegador da Web, há uma limitação sobre quais tipos de dados podem ser especificados em uma URL. Para obter mais informações sobre quais tipos são suportados por padrão, consulte a seção **UriTemplate Query String Parameters and URLs** abaixo. O comportamento padrão pode ser alterado fornecendo seu próprio T:System.ServiceModel.Dispatcher.QueryStringConverter implementação que especifica como converter os parâmetros especificados em uma URL para o tipo de parâmetro real. Para obter mais informações, consulte <xref:System.ServiceModel.Dispatcher.QueryStringConverter>.  
  
> [!CAUTION]
> Os serviços escritos com o modelo de programação WCF WEB HTTP não usam mensagens SOAP. Como o SOAP não é usado, os recursos de segurança fornecidos pelo WCF não podem ser usados. Você pode, no entanto, usar a segurança baseada em transporte hospedando seu serviço com HTTPS. Para obter mais informações sobre a segurança do WCF, consulte [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
> [!WARNING]
> A instalação da extensão WebDAV para IIS pode fazer com que os serviços Web HTTP retornem um erro HTTP 405 à medida que a extensão WebDAV tenta lidar com todas as solicitações PUT. Para contornar esse problema, você pode desinstalar a extensão do WebDAV ou desativar a extensão WebDAV para o seu site. Para obter mais informações, consulte [IIS e WebDav](https://learn.iis.net/page.aspx/357/webdav-for-iis-70/)  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a>Processamento uri com UriTemplate e UriTemplateTable  
 Os modelos URI fornecem uma sintaxe eficiente para expressar grandes conjuntos de URIs estruturalmente semelhantes. Por exemplo, o modelo a seguir expressa o conjunto de todas as URIs de três segmentos que começam com "a" e terminam com "c" sem considerar o valor do segmento intermediário: a/{segment}/c  
  
 Este modelo descreve URIs como o seguinte:  
  
- a/x/c  
  
- a/y/c  
  
- a/z/c  
  
- e assim por diante.  
  
 Neste modelo, a notação da cinta encaracolada ("{segment}") indica um segmento variável em vez de um valor literal.  
  
 .NET Framework fornece uma API para <xref:System.UriTemplate>trabalhar com modelos URI chamados . `UriTemplates`permitir que você faça o seguinte:  
  
- Você pode chamar `Bind` um dos métodos com um conjunto de parâmetros para produzir um *URI totalmente fechado* que corresponda ao modelo. Isso significa que todas as variáveis dentro do modelo URI são substituídas por valores reais.  
  
- Você pode `Match`ligar () com um URI candidato, que usa um modelo para dividir um URI candidato em suas partes constituintes e retorna um dicionário que contém as diferentes partes do URI rotuladas de acordo com as variáveis no modelo.  
  
- `Bind`() `Match`e () são inversos para `Match` `Bind`que você possa chamar ( ( x ) e voltar com o mesmo ambiente que você começou.  
  
 Há muitas vezes (especialmente no servidor, onde é necessário enviar uma solicitação para uma operação de serviço com <xref:System.UriTemplate> base no URI) que você deseja acompanhar um conjunto de objetos em uma estrutura de dados que pode abordar independentemente cada um dos modelos contidos. <xref:System.UriTemplateTable>representa um conjunto de modelos URI e seleciona a melhor correspondência dado um conjunto de modelos e um URI candidato. Isso não está afiliado a nenhuma pilha de rede específica (WCF incluída) para que você possa usá-la sempre que necessário.  
  
 O WCF Service Model <xref:System.UriTemplate> <xref:System.UriTemplateTable> faz uso e associa operações de <xref:System.UriTemplate>serviço a um conjunto de URIs descritos por a . Uma operação de serviço <xref:System.UriTemplate>está associada <xref:System.ServiceModel.Web.WebGetAttribute> a <xref:System.ServiceModel.Web.WebInvokeAttribute>um , usando o ou o . Para obter <xref:System.UriTemplate> mais <xref:System.UriTemplateTable>informações sobre e , consulte [UriTemplate e UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
  
## <a name="webget-and-webinvoke-attributes"></a>Atributos WebGet e WebInvoke  
 Os serviços WCF WEB HTTP fazem uso de verbos de recuperação (por exemplo, HTTP GET) além de vários verbos de invocação (por exemplo, HTTP POST, PUT e DELETE). O modelo de programação WCF WEB HTTP permite que os desenvolvedores de serviços <xref:System.ServiceModel.Web.WebGetAttribute> controlem o modelo uri e o verbo associados às suas operações de serviço com o e <xref:System.ServiceModel.Web.WebInvokeAttribute>. O <xref:System.ServiceModel.Web.WebGetAttribute> e <xref:System.ServiceModel.Web.WebInvokeAttribute> permitir que você controle como as operações individuais ficam vinculadas às URIs e aos métodos HTTP associados a essas URIs. Por exemplo, <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> adicionando e no código a seguir.  
  
```csharp
[ServiceContract]  
interface ICustomer  
{  
  //"View It"  
  
  [WebGet]  
  Customer GetCustomer():  
  
  //"Do It"  
    [WebInvoke]  
  Customer UpdateCustomerName( string id,
                               string newName );  
}  
```  
  
 O código anterior permite que você faça as seguintes solicitações HTTP.  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>padrão para POST, mas você pode usá-lo para outros verbos também.  
  
```csharp
[ServiceContract]  
interface ICustomer  
{  
  //"View It" -> HTTP GET  
    [WebGet( UriTemplate="customers/{id}" )]  
  Customer GetCustomer( string id ):  
  
  //"Do It" -> HTTP PUT  
  [WebInvoke( UriTemplate="customers/{id}", Method="PUT" )]  
  Customer UpdateCustomer( string id, Customer newCustomer );  
}  
```  
  
 Para ver uma amostra completa de um serviço WCF que usa o modelo de programação WCF WEB HTTP, consulte [Como: Criar um serviço básico wcf web http](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a>Parâmetros e URLs de seqüeique de consulta de uritemplate  
 Serviços no estilo Web podem ser chamados de um navegador da Web digitando uma URL associada a uma operação de serviço. Essas operações de serviço podem ter parâmetros de seqüência de consulta que devem ser especificados em um formulário de seqüência dentro da URL. A tabela a seguir mostra os tipos que podem ser passados dentro de uma URL e o formato usado.  
  
|Type|Formatar|  
|----------|------------|  
|<xref:System.Byte>|0 - 255|  
|<xref:System.SByte>|-128 - 127|  
|<xref:System.Int16>|-32768 - 32767|  
|<xref:System.Int32>|-2,147,483,648 - 2,147,483,647|  
|<xref:System.Int64>|-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807|  
|<xref:System.UInt16>|0 - 65535|  
|<xref:System.UInt32>|0 - 4,294,967,295|  
|<xref:System.UInt64>|0 - 18,446,744,073,709,551,615|  
|<xref:System.Single>|-3.402823e38 - 3.402823e38 (notação expoente não é necessária)|  
|<xref:System.Double>|-1.79769313486232e308 - 1.79769313486232e308 (notação expoente não é necessária)|  
|<xref:System.Char>|Qualquer caractere único|  
|<xref:System.Decimal>|Qualquer decimal na notação padrão (sem expoente)|  
|<xref:System.Boolean>|Verdadeiro ou Falso (caso insensível)|  
|<xref:System.String>|Qualquer string (seqüência nula não é suportada e nenhuma fuga é feita)|  
|<xref:System.DateTime>|MM/DD/AAAA<br /><br /> MM/DD/YYYY HH:MM:SS [AM&#124;PM]<br /><br /> Mês Do Dia<br /><br /> Mês do Dia HH:MM:SS [AM&#124;PM]|  
|<xref:System.TimeSpan>|Dd. HH:MM:SS<br /><br /> Onde DD = Dias, HH = Horas, MM = minutos, SS = Segundos|  
|<xref:System.Guid>|Um GUID, por exemplo:<br /><br /> 936DA01F-9ABD-4d9d-80C7-02AF85C822A8|  
|<xref:System.DateTimeOffset>|MM/DD/YYYY HH:MM:SS MM:SS<br /><br /> Onde DD = Dias, HH = Horas, MM = minutos, SS = Segundos|  
|Enumerações|O valor de enumeração, por exemplo, define a enumeração como mostrado no código a seguir.<br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> Qualquer um dos valores de enumeração individual (ou seus valores inteiros correspondentes) pode ser especificado na seqüência de consultas.|  
|Tipos que `TypeConverterAttribute` têm um que pode converter o tipo para e a partir de uma representação de strings.|Depende do Tipo Conversor.|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a>Formatos e o Modelo de Programação HTTP da Web WCF  
 O modelo de programação WCF WEB HTTP tem novos recursos para trabalhar com muitos formatos de dados diferentes. Na camada de <xref:System.ServiceModel.WebHttpBinding> vinculação, o pode ler e gravar os seguintes tipos de dados:  
  
- XML  
  
- JSON  
  
- Fluxos binários opacos  
  
 Isso significa que o modelo de programação WCF WEB HTTP pode lidar <xref:System.IO.Stream>com qualquer tipo de dados, mas, você pode estar programando contra .  
  
 O .NET Framework 3.5 fornece suporte para dados JSON (AJAX), bem como feeds de sindicância (incluindo ATOM e RSS). Para obter mais informações sobre esses recursos, consulte [WCF Web HTTP Formatting,](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md) [WCF Syndication Overview](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)e [AJAX Integration and JSON Support](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).  
  
## <a name="wcf-web-http-programming-model-and-security"></a>WCF WEB HTTP Modelo de Programação e Segurança  

Como o modelo de programação WCF WEB HTTP não suporta os protocolos WS-*, a única maneira de garantir um serviço WEB HTTP WCF é expor o serviço através do HTTPS usando O SSL. Para obter mais informações sobre como configurar o SSL com o IIS 7.0, consulte [Como implementar o SSL no IIS](https://support.microsoft.com/help/299875/how-to-implement-ssl-in-iis).
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a>Solução de problemas do modelo de programação HTTP da Web WCF  
 Ao ligar para os serviços WCF WEB HTTP usando <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> um para criar <xref:System.ServiceModel.EndpointAddress> um canal, <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>ele <xref:System.ServiceModel.Description.WebHttpBehavior> usa o <xref:System.ServiceModel.EndpointAddress> conjunto no arquivo de configuração mesmo se um diferente for passado para o .  
  
## <a name="see-also"></a>Confira também

- [Sindicalização do WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
- [Modelo de objeto de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [Modelo de programação WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
