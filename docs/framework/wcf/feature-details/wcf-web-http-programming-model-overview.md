---
title: Visão geral de modelo de programação HTTP Web do WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 70d1b76108c9eab0280e6499ab2b4d0c70def853
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2018
---
# <a name="wcf-web-http-programming-model-overview"></a>Visão geral de modelo de programação HTTP Web do WCF
O [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] modelo de programação HTTP WEB fornece os elementos básicos necessários para criar serviços WEB HTTP com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Serviços WEB HTTP são projetados para ser acessado por mais ampla variedade de possíveis clientes, incluindo navegadores da Web e têm os seguintes requisitos exclusivos:  
  
-   **URI de processamento e URIs** URIs desempenham um papel central no design de serviços da WEB HTTP. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usos do modelo de programação HTTP WEB do <xref:System.UriTemplate> e <xref:System.UriTemplateTable> classes para fornecer recursos de processamento do URI.  
  
-   **Suporte para operações GET e POST** serviços WEB HTTP fazem uso do verbo GET para recuperação de dados, além de várias invocar verbos para modificação de dados e invocação remota. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usos do modelo de programação HTTP WEB do <xref:System.ServiceModel.Web.WebGetAttribute> e <xref:System.ServiceModel.Web.WebInvokeAttribute> para associar operações de serviço GET e outros verbos HTTP como PUT, POST e excluir.  
  
-   **Vários formatos de dados** serviços Web estilo processam vários tipos de dados, além de mensagens SOAP. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usos do modelo de programação HTTP WEB do <xref:System.ServiceModel.WebHttpBinding> e <xref:System.ServiceModel.Description.WebHttpBehavior> para dar suporte a vários formatos de dados diferentes, incluindo documentos XML, o objeto de dados JSON e fluxos de conteúdo binário, como imagens, arquivos de vídeo ou um texto sem formatação.  
  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de programação HTTP WEB estende o alcance de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para cenários de rosto estilo da Web que incluem serviços HTTP da WEB, serviços de AJAX e JSON e feeds de agregação (ATOM/RSS). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Serviços de AJAX e JSON, consulte [integração de AJAX e suporte a JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Distribuição, consulte [visão geral de Sindicalização do WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md).  
  
 Não existem restrições adicionais sobre os tipos de dados que podem ser retornados de um serviço da WEB HTTP. Qualquer tipo serializável pode ser retornado de uma operação de serviço da WEB HTTP. Como as operações do serviço da WEB HTTP podem ser invocar um navegador da web que há uma limitação em quais dados de tipos podem ser especificados em uma URL. Para obter mais informações sobre quais tipos são suportados por padrão, consulte o **URLs e parâmetros de cadeia de caracteres de consulta do UriTemplate** seção abaixo. O comportamento padrão pode ser alterado, fornecendo sua própria implementação de T:System.ServiceModel.Dispatcher.QueryStringConverter que especifica como converter os parâmetros especificados em uma URL para o tipo de parâmetro real. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
> [!CAUTION]
>  Serviços criados com o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de programação HTTP WEB não usa mensagens SOAP. Como SOAP não for usado, os recursos de segurança fornecidas por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não pode ser usado. No entanto você pode usar segurança baseada em transporte hospedando o serviço com HTTPS. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] segurança, consulte [visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
> [!WARNING]
>  Instalar a extensão WebDAV para IIS pode fazer com que os serviços da Web HTTP retornar um erro HTTP 405 como o WebDAV tentativas de extensão para manipular todas as solicitações PUT. Para contornar esse problema, você pode desinstalar a extensão WebDAV ou desabilitar a extensão WebDAV para seu site. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [O IIS e WebDav](http://learn.iis.net/page.aspx/357/webdav-for-iis-70/)  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a>URI de processamento com UriTemplate e UriTemplateTable  
 Modelos URI fornecem uma sintaxe eficiente para expressar grandes conjuntos de URIs estruturalmente semelhantes. Por exemplo, o modelo a seguir expressa o conjunto de URIs de todos os três segmentos que começam com "a" e termina com "c" sem considerar o valor do segmento intermediário: um / /c {segmento}  
  
 Este modelo descreve URIs semelhante ao seguinte:  
  
-   um/x/c  
  
-   um/y/c  
  
-   a/z/c  
  
-   E assim por diante.  
  
 Neste modelo, a notação de chave de abertura ("{segmento}") indica um segmento de variável em vez de um valor literal.  
  
 .NET framework fornece uma API para trabalhar com modelos URI chamada <xref:System.UriTemplate>. `UriTemplates` permite que você faça o seguinte:  
  
-   Você pode chamar um do `Bind` métodos com um conjunto de parâmetros para produzir um *totalmente fechada URI* que coincide com o modelo. Isso significa que todas as variáveis dentro do modelo URI são substituídas por valores reais.  
  
-   Você pode chamar `Match`() com um URI, que usa um modelo para dividir um candidato URI em seu constituinte partes e retorna um dicionário que contém as diferentes partes do URI rotulada de acordo com as variáveis no modelo de candidato.  
  
-   `Bind`() e `Match`() são inverte para que você possa chamar `Match`( `Bind`(x)) e retorne o mesmo ambiente em que você iniciou com.  
  
 Há muitas vezes (especialmente no servidor, onde é necessário expedir uma solicitação para uma operação de serviço com base no URI) que você deseja manter o controle de um conjunto de <xref:System.UriTemplate> objetos em uma estrutura de dados independente pode abordar cada independente modelos. <xref:System.UriTemplateTable> representa um conjunto de modelos URI e seleciona a melhor correspondência dada um conjunto de modelos e um URI de candidato. Isso não está afiliado a qualquer pilha de rede específica ([!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] incluído) para que você pode usá-lo sempre que necessário.  
  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de serviço usa <xref:System.UriTemplate> e <xref:System.UriTemplateTable> para associar operações de serviço com um conjunto de URIs descrita por um <xref:System.UriTemplate>. Uma operação de serviço é associada com um <xref:System.UriTemplate>, usando o <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute>. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] <xref:System.UriTemplate> e <xref:System.UriTemplateTable>, consulte [UriTemplate e UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
  
## <a name="webget-and-webinvoke-attributes"></a>Atributos de WebInvoke e WebGet  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Serviços WEB HTTP fazem uso de verbos de recuperação (por exemplo HTTP GET) além de várias invocar verbos (por exemplo, HTTP POST, PUT e DELETE). O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de programação HTTP WEB permite que os desenvolvedores de serviço para controle de ambos o modelo de URI e o verbo associado com suas operações de serviço com o <xref:System.ServiceModel.Web.WebGetAttribute> e <xref:System.ServiceModel.Web.WebInvokeAttribute>. O <xref:System.ServiceModel.Web.WebGetAttribute> e <xref:System.ServiceModel.Web.WebInvokeAttribute> permitem controlar operações individuais como estejam associados a URIs e os métodos HTTP associado com esses URIs. Por exemplo, adicionando <xref:System.ServiceModel.Web.WebGetAttribute> e <xref:System.ServiceModel.Web.WebInvokeAttribute> no código a seguir.  
  
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
  
 Para ver um exemplo completo de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço que usa o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP do modelo de programação WEB, consulte [como: criar um serviço básico do WCF Web HTTP](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a>URLs e os parâmetros de cadeia de caracteres de consulta de UriTemplate  
 Serviços de estilo da Web podem ser chamados em um navegador da Web digitando uma URL que está associada uma operação de serviço. Essas operações de serviço podem levar a parâmetros de cadeia de caracteres de consulta que devem ser especificados em um formulário de cadeia de caracteres dentro de URL. A tabela a seguir mostra os tipos que podem ser transmitidos em uma URL e o formato usado.  
  
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
|<xref:System.Single>|3.402823 E38 de - 3.402823 E38 - (notação exponencial não é necessária)|  
|<xref:System.Double>|-1, 79769313486232E308 - 1, 79769313486232E308 (notação exponencial não é necessária)|  
|<xref:System.Char>|Qualquer caractere único|  
|<xref:System.Decimal>|Qualquer decimal na notação padrão (nenhuma expoente)|  
|<xref:System.Boolean>|VERDADEIRO ou falso (maiusculas de minúsculas)|  
|<xref:System.String>|Qualquer cadeia de caracteres (nula não há suporte para a cadeia de caracteres e nenhuma saída é feito)|  
|<xref:System.DateTime>|DD/MM/AAAA<br /><br /> MM/DD/YYYY HH:MM:SS [AM&#124;PM]<br /><br /> Mês dia/ano<br /><br /> Dia do mês ano hh [AM&#124;PM]|  
|<xref:System.TimeSpan>|DD.HH:MM:SS<br /><br /> Onde DD = dias, HH = horas, MM = minutos, SS = segundos|  
|<xref:System.Guid>|Um GUID, por exemplo:<br /><br /> 936DA01F-9ABD-4d9d-80C7-02AF85C822A8|  
|<xref:System.DateTimeOffset>|DD/MM/AAAA HH MM: SS<br /><br /> Onde DD = dias, HH = horas, MM = minutos, SS = segundos|  
|Enumerações|O valor de enumeração, por exemplo, que define a enumeração conforme mostrado no código a seguir.<br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> Qualquer um dos valores de enumeração individuais (ou seus valores inteiros correspondentes) pode ser especificada na cadeia de caracteres de consulta.|  
|Tipos que têm um `TypeConverterAttribute` que pode converter o tipo em uma representação de cadeia de caracteres.|Depende do conversor de tipo.|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a>Formatos e o modelo de programação WCF WEB HTTP  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de programação HTTP WEB tem novos recursos para trabalhar com vários formatos de dados diferentes. Na camada de associação, o <xref:System.ServiceModel.WebHttpBinding> pode ler e gravar os diferentes tipos de dados a seguir:  
  
-   XML  
  
-   JSON  
  
-   Fluxos binários opacos  
  
 Isso significa que o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de programação HTTP WEB pode lidar com qualquer tipo de dados, mas você pode ser programar <xref:System.IO.Stream>.  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] fornece suporte para dados JSON (AJAX), bem como os feeds de agregação (incluindo ATOM e RSS). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Esses recursos, consulte [WCF Web HTTP formatação](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)[visão geral de Sindicalização do WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md) e [integração de AJAX e suporte a JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).  
  
## <a name="wcf-web-http-programming-model-and-security"></a>Segurança e o modelo de programação WCF WEB HTTP  
 Porque o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não suporta o modelo de programação HTTP WEB WS-* protocolos, a única maneira de proteger um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço da WEB HTTP é para expor o serviço por HTTPS usando SSL. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Configurar o SSL com [!INCLUDE[iisver](../../../../includes/iisver-md.md)], consulte [como implementar o SSL no IIS](http://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a>O modelo de programação do WCF WEB HTTP de solução de problemas  
 Ao chamar WCF WEB HTTP serviços usando um <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> para criar um canal, o <xref:System.ServiceModel.Description.WebHttpBehavior> usa o <xref:System.ServiceModel.EndpointAddress> definir a configuração arquivo, mesmo se outro <xref:System.ServiceModel.EndpointAddress> é passado para o <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>.  
  
## <a name="see-also"></a>Consulte também  
 [Sindicalização do WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)  
 [Modelo de objeto de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 [Modelo de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
