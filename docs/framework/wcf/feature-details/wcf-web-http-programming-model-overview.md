---
title: Visão geral de modelo de programação HTTP Web do WCF
ms.date: 03/30/2017
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
ms.openlocfilehash: a6f267232085a46d481199eac83e464f5f774273
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199577"
---
# <a name="wcf-web-http-programming-model-overview"></a>Visão geral de modelo de programação HTTP Web do WCF
O modelo de programação WEB do Windows Communication Foundation (WCF) HTTP fornece os elementos básicos necessários para compilar serviços WEB HTTP com WCF. Serviços WCF WEB HTTP são projetados para ser acessado por mais ampla gama de possíveis clientes, incluindo navegadores da Web e têm os seguintes requisitos exclusivos:  
  
-   **URIs e processamento de URI** URIs desempenham um papel central no design de serviços WEB HTTP. Os usos do modelo de programação WCF WEB HTTP a <xref:System.UriTemplate> e <xref:System.UriTemplateTable> classes para fornecer recursos de processamento do URI.  
  
-   **Suporte para operações GET e POST** serviços WEB HTTP fazem uso do verbo GET para recuperação de dados, além de vários invocar verbos para modificação de dados e invocação remota. Os usos do modelo de programação WCF WEB HTTP a <xref:System.ServiceModel.Web.WebGetAttribute> e <xref:System.ServiceModel.Web.WebInvokeAttribute> para associar operações de serviço com GET e outros verbos HTTP como PUT, POST e excluir.  
  
-   **Vários formatos de dados** serviços no estilo Web processam muitos tipos de dados, além de mensagens SOAP. Os usos do modelo de programação WCF WEB HTTP a <xref:System.ServiceModel.WebHttpBinding> e <xref:System.ServiceModel.Description.WebHttpBehavior> para dar suporte a muitos formatos de dados diferentes, incluindo documentos XML, o objeto de dados JSON e fluxos de conteúdo binário, como imagens, arquivos de vídeo ou texto sem formatação.  
  
 O modelo de programação WCF WEB HTTP amplia o alcance do WCF para cobrir os cenários de estilo da Web que incluem serviços WEB HTTP, os serviços AJAX e JSON e feeds de Sindicalização ATOM/RSS (). Para obter mais informações sobre os serviços AJAX e JSON, consulte [integração de AJAX e suporte a JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md). Para obter mais informações sobre a distribuição, consulte [visão geral de Sindicalização do WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md).  
  
 Não há nenhuma restrição adicional sobre os tipos de dados que podem ser retornados de um serviço WEB HTTP. Qualquer tipo serializável pode ser retornado de uma operação de serviço WEB HTTP. Como operações de serviço WEB HTTP podem ser invocar por um navegador da web que há uma limitação sobre quais tipos podem ser especificados em uma URL de dados. Para obter mais informações sobre quais tipos são suportados por padrão, consulte a **parâmetros de cadeia de caracteres de consulta de UriTemplate e URLs do** seção abaixo. O comportamento padrão pode ser alterado, fornecendo sua própria implementação de T:System.ServiceModel.Dispatcher.QueryStringConverter que especifica como converter os parâmetros especificados em uma URL para o tipo de parâmetro real. Para obter mais informações, consulte <xref:System.ServiceModel.Dispatcher.QueryStringConverter>.  
  
> [!CAUTION]
>  Serviços escritos com o modelo de programação WCF WEB HTTP não usa mensagens SOAP. Como SOAP não é usado, os recursos de segurança fornecidos pelo WCF não podem ser usados. No entanto você pode usar segurança baseada no transporte ao hospedar seu serviço com HTTPS. Para obter mais informações sobre a segurança do WCF, consulte [visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
> [!WARNING]
>  Instalando a extensão WebDAV para IIS pode fazer com que os serviços Web HTTP retornar um erro HTTP 405 como o WebDAV extensão tenta manipular todas as solicitações PUT. Para contornar esse problema, você pode desinstalar a extensão WebDAV ou desabilitar a extensão WebDAV para seu site da web. Para obter mais informações, consulte [IIS e WebDav](https://learn.iis.net/page.aspx/357/webdav-for-iis-70/)  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a>URI de processamento com UriTemplate e UriTemplateTable  
 Os modelos URI fornecem uma sintaxe eficiente para expressar conjuntos grandes de URIs estruturalmente semelhantes. Por exemplo, o modelo a seguir expressa o conjunto de URIs de todos os três segmentos que começam com "a" e terminar com "c" sem levar em consideração o valor do segmento intermediário: um / / c de {segmento}  
  
 Este modelo descreve URIs semelhante ao seguinte:  
  
-   a/x/c  
  
-   a/y/c  
  
-   a/z/c  
  
-   e assim por diante.  
  
 Neste modelo, a notação de chave de abertura ("{segmento}") indica um segmento de variável em vez de um valor literal.  
  
 .NET framework fornece uma API para trabalhar com modelos URI chamado <xref:System.UriTemplate>. `UriTemplates` permite que você faça o seguinte:  
  
-   Você pode chamar um dos `Bind` métodos com um conjunto de parâmetros para produzir uma *totalmente fechados URI* que corresponde ao modelo. Isso significa que todas as variáveis dentro do modelo URI são substituídas por valores reais.  
  
-   Você pode chamar `Match`() com um candidato do URI, que usa um modelo para dividir um candidato a partes de URI em seus constituintes e retorna um dicionário que contém as diferentes partes do URI rotulados de acordo com as variáveis no modelo.  
  
-   `Bind`() e `Match`() são o inverso uma para que você possa chamar `Match`( `Bind`(x)) e volte com o mesmo ambiente que você iniciou com.  
  
 Há muitas vezes (especialmente no servidor, em que é necessário ao expedir uma solicitação para uma operação de serviço com base no URI) que você deseja manter o controle de um conjunto de <xref:System.UriTemplate> objetos em uma estrutura de dados que podem resolver independentemente de cada uma independente modelos. <xref:System.UriTemplateTable> representa um conjunto de modelos URI e seleciona a melhor correspondência, dada um conjunto de modelos e um URI candidato. Isso não está afiliado qualquer pilha de rede específica (incluído ao WCF) para que você pode usá-lo sempre que necessário.  
  
 O modelo de serviço WCF utiliza <xref:System.UriTemplate> e <xref:System.UriTemplateTable> para associar operações de serviço com um conjunto de URIs descrito por um <xref:System.UriTemplate>. Uma operação de serviço é associada com um <xref:System.UriTemplate>, usando o <xref:System.ServiceModel.Web.WebGetAttribute> ou o <xref:System.ServiceModel.Web.WebInvokeAttribute>. Para obter mais informações sobre <xref:System.UriTemplate> e <xref:System.UriTemplateTable>, consulte [UriTemplate e UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
  
## <a name="webget-and-webinvoke-attributes"></a>Atributos de WebInvoke e WebGet  
 Serviços WCF WEB HTTP fazem uso de verbos de recuperação (por exemplo HTTP GET), além de vários invocar verbos (por exemplo, HTTP POST, PUT e DELETE). O modelo de programação WCF WEB HTTP permite que os desenvolvedores de serviço ao controle de ambos os o modelo de URI e o verbo associado com suas operações de serviço com o <xref:System.ServiceModel.Web.WebGetAttribute> e <xref:System.ServiceModel.Web.WebInvokeAttribute>. O <xref:System.ServiceModel.Web.WebGetAttribute> e o <xref:System.ServiceModel.Web.WebInvokeAttribute> permitem controlar operações individuais como estejam associados a URIs e os métodos HTTP associado com esses URIs. Por exemplo, adicionando <xref:System.ServiceModel.Web.WebGetAttribute> e <xref:System.ServiceModel.Web.WebInvokeAttribute> no código a seguir.  
  
```  
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
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> o padrão é POST, mas você pode usá-lo para outros verbos muito.  
  
```  
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
  
 Para ver um exemplo completo de um serviço WCF que usa o modelo de programação WCF WEB HTTP, consulte [como: Criar um serviço de Web HTTP WCF básico](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a>URLs e parâmetros de cadeia de caracteres de consulta de UriTemplate  
 Serviços de estilo da Web podem ser chamados em um navegador da Web, digitando uma URL que está associada uma operação de serviço. Essas operações de serviço podem levar a parâmetros de cadeia de caracteres de consulta que devem ser especificados em um formulário de cadeia de caracteres na URL. A tabela a seguir mostra os tipos que podem ser passados em uma URL e o formato usado.  
  
|Tipo|Formatar|  
|----------|------------|  
|<xref:System.Byte>|0 - 255|  
|<xref:System.SByte>|-128 - 127|  
|<xref:System.Int16>|-32768 - 32767|  
|<xref:System.Int32>|-2,147,483,648 - 2,147,483,647|  
|<xref:System.Int64>|-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807|  
|<xref:System.UInt16>|0 - 65535|  
|<xref:System.UInt32>|0 - 4,294,967,295|  
|<xref:System.UInt64>|0 - 18,446,744,073,709,551,615|  
|<xref:System.Single>|-3.402823e38 - 3.402823e38 (não é necessária notação exponencial)|  
|<xref:System.Double>|-1,79769313486232E308 - 1,79769313486232E308 (não é necessária notação exponencial)|  
|<xref:System.Char>|Qualquer caractere único|  
|<xref:System.Decimal>|Qualquer decimal em notação padrão (nenhum expoente)|  
|<xref:System.Boolean>|VERDADEIRO ou falso (caso kana)|  
|<xref:System.String>|Qualquer cadeia de caracteres (nula não há suporte para a cadeia de caracteres e nenhum escape é feito)|  
|<xref:System.DateTime>|MM/DD/AAAA<br /><br /> MM/DD/AAAA HH: MM SS [AM&AMP;#124;PM]<br /><br /> Mês dia/ano<br /><br /> Dia do mês ano hh: mm ss [AM&#124;PM]|  
|<xref:System.TimeSpan>|DD.HH:MM:SS<br /><br /> Onde DD = HH de dias, horas, MM = minutos, SS = segundos|  
|<xref:System.Guid>|Um GUID, por exemplo:<br /><br /> 936DA01F-9ABD-4d9d-80C7-02AF85C822A8|  
|<xref:System.DateTimeOffset>|MM DE MM/DD/AAAA HH: SS<br /><br /> Onde DD = HH de dias, horas, MM = minutos, SS = segundos|  
|Enumerações|O valor de enumeração, por exemplo, que define a enumeração, conforme mostrado no código a seguir.<br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> Qualquer um dos valores de enumeração individuais (ou seus valores de inteiro correspondente) pode ser especificado na cadeia de caracteres de consulta.|  
|Tipos que têm um `TypeConverterAttribute` que pode converter o tipo de e para uma representação de cadeia de caracteres.|Depende do conversor de tipo.|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a>Formatos e o modelo de programação WCF WEB HTTP  
 O modelo de programação WCF WEB HTTP tem novos recursos para trabalhar com vários formatos de dados diferentes. Na camada de associação, o <xref:System.ServiceModel.WebHttpBinding> pode ler e gravar os diferentes tipos de dados a seguir:  
  
-   XML  
  
-   JSON  
  
-   Fluxos binários opacos  
  
 Isso significa que o modelo de programação WCF WEB HTTP pode lidar com qualquer tipo de dados, mas você pode ser programar <xref:System.IO.Stream>.  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] fornece suporte para dados JSON (AJAX), bem como os feeds de agregação (incluindo ATOM e RSS). Para obter mais informações sobre esses recursos, consulte [WCF Web HTTP formatação](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)[visão geral de Sindicalização do WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md) e [integração AJAX e suporte para JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).  
  
## <a name="wcf-web-http-programming-model-and-security"></a>Segurança e o modelo de programação WCF WEB HTTP  
 Como o modelo de programação HTTP WEB do WCF não oferece suporte a WS-* protocolos, a única maneira de proteger um serviço WCF WEB HTTP é expor o serviço via HTTPS usando SSL. Para obter mais informações sobre como configurar o SSL com [!INCLUDE[iisver](../../../../includes/iisver-md.md)], consulte [como implementar o SSL no IIS](https://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a>O modelo de programação WCF WEB HTTP de solução de problemas  
 Ao chamar o WCF WEB HTTP serviços usando um <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> para criar um canal, o <xref:System.ServiceModel.Description.WebHttpBehavior> usa o <xref:System.ServiceModel.EndpointAddress> definir a configuração arquivo, mesmo se um outro <xref:System.ServiceModel.EndpointAddress> é passado para o <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>.  
  
## <a name="see-also"></a>Consulte também

- [Sindicalização do WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
- [Modelo de objeto de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [Modelo de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
