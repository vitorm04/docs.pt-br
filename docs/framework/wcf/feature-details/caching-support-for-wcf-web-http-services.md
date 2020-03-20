---
title: Cache com suporte para serviços HTTP Web do WCF
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 63c83cc1af9a3ccfdbdd79f8d0480e6c29eaf2f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185425"
---
# <a name="caching-support-for-wcf-web-http-services"></a>Cache com suporte para serviços HTTP Web do WCF

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]permite que você use o mecanismo de cache declarativo já disponível em ASP.NET em seus serviços WCF Web HTTP. Isso permite que você faça cache de respostas de suas operações de serviço WCF Web HTTP. Quando um usuário envia um HTTP GET para o seu serviço configurado para cache, ASP.NET envia de volta a resposta armazenada em cache e o método de serviço não é chamado. Quando o cache expira, na próxima vez que um usuário enviar um HTTP GET, seu método de serviço é chamado e a resposta é novamente armazenada em cache. Para obter mais informações sobre ASP.NET cache, consulte [ASP.NET Visão Geral do Cache](https://docs.microsoft.com/previous-versions/aspnet/ms178597(v=vs.100)).  
  
## <a name="basic-web-http-service-caching"></a>Caching básico do serviço WEB HTTP  

  Para habilitar o cache de serviço WEB HTTP, você <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> deve primeiro <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> habilitar ASP.NET compatibilidade aplicando a configuração de serviço para ou <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.  
  
 .NET Framework 4 introduz um <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> novo atributo chamado que permite especificar um nome de perfil de cache. Este atributo é aplicado a uma operação de serviço. O exemplo a <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> seguir aplica-se a um serviço `GetCustomer` para habilitar ASP.NET compatibilidade e configura a operação para cache. O <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> atributo especifica um perfil de cache que contém as configurações de cache a serem usadas.  
  
```csharp
[ServiceContract]
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]
public class Service
{
    [WebGet(UriTemplate = "{id}")]
    [AspNetCacheProfile("CacheFor60Seconds")]
    public Customer GetCustomer(string id)
    {
        // ...
    }
}
```  
  
Também ative ASP.NET modo de compatibilidade no arquivo Web.config, conforme mostrado no exemplo a seguir.  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
> Se ASP.NET modo de compatibilidade não <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> estiver ligado e for usado, uma exceção será lançada.  
  
 O nome do perfil <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> de cache especificado pelo identifica um perfil de cache adicionado ao seu arquivo de configuração Web.config. O perfil de cache é `outputCacheSetting` definido com um elemento <> como mostrado no exemplo de configuração a seguir.  
  
```xml
<!-- ...  -->
<system.web>  
   <caching>  
      <outputCacheSettings>  
         <outputCacheProfiles>  
            <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable"/>  
         </outputCacheProfiles>  
      </outputCacheSettings>  
   </caching>  
   <!-- ... -->  
</system.web>  
```  
  
 Este é o mesmo elemento de configuração que está disponível para ASP.NET aplicativos. Para obter mais informações sobre <xref:System.Web.Configuration.OutputCacheProfile>ASP.NET perfis de cache, consulte . Para os serviços Web HTTP, os atributos mais importantes no perfil de cache são: `cacheDuration` e `varyByParam`. Ambos os atributos são necessários. `cacheDuration`define a quantidade de tempo que uma resposta deve ser armazenada em cache em segundos. `varyByParam`permite especificar um parâmetro de seqüência de consultas que é usado para cache de respostas. Todas as solicitações feitas com diferentes valores de parâmetro de seqüência de consulta são armazenadas em cache separadamente. Por exemplo, uma vez que `http://MyServer/MyHttpService/MyOperation?param=10`uma solicitação inicial seja feita para , todas as solicitações subseqüentes feitas com o mesmo URI seriam devolvidas a resposta em cache (desde que a duração do cache não tenha transcorrido). As respostas para uma solicitação semelhante que é a mesma, mas tem um valor diferente para o parâmetro de seqüência de string de consulta de parâmetros, são armazenadas separadamente. Se você não quiser esse comportamento `varyByParam` de cache separado, defina como "nenhum".  
  
## <a name="sql-cache-dependency"></a>Dependência de cache SQL  

  As respostas do serviço Web HTTP também podem ser armazenadas em cache com uma dependência de cache SQL. Se o serviço WCF Web HTTP depender dos dados armazenados em um banco de dados SQL, você pode querer fazer um cache da resposta do serviço e invalidar a resposta armazenada em cache quando os dados na tabela de banco de dados SQL forem alterados. Esse comportamento é configurado completamente dentro do arquivo Web.config. Primeiro, defina uma seqüência de conexão no elemento> <. `connectionStrings`  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 Em seguida, você deve ativar a `caching` dependência de cache `system.web` SQL dentro de um elemento <> dentro do elemento> <, conforme mostrado no exemplo de configuração a seguir.  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>
    </sqlCacheDependency>
    <!-- ... -->
  </caching>
  <!-- ... -->
</system.web>
```  
  
 Aqui, a dependência do cache SQL está ativada e um tempo de votação de 1000 milissegundos é definido. Cada vez que o tempo de votação é decorrido, a tabela do banco de dados é verificada para atualizações. Se for detectada a deserção, o conteúdo do cache será removido e, na próxima vez que a operação do serviço for invocada, uma nova resposta será armazenada em cache. Dentro do `sqlCacheDependency` elemento <> adicionar as bases de `databases` dados e referenciar as strings de conexão dentro do elemento> <como mostrado no exemplo a seguir.  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>  
    </sqlCacheDependency>  
    <!-- ... -->  
  </caching>  
  <!-- ... -->  
</system.web>  
```  
  
 Em seguida, você deve configurar as `caching` configurações de cache de saída dentro do elemento> <, conforme mostrado no exemplo a seguir.  
  
```xml
<system.web>
  <caching>  
    <!-- ...  -->
    <outputCacheSettings>
      <outputCacheProfiles>
        <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable" />
      </outputCacheProfiles>
    </outputCacheSettings>
  </caching>
  <!-- ... -->
</system.web>
```  
  
 Aqui, a duração do cache `varyByParam` é definida como `sqlDependency` 60 segundos, não é definida como nenhuma e é definida como uma lista delimitada de nomes de banco de dados/pares de tabela separados por pontos. Quando os `MyTable` dados são alterados, a resposta armazenada em cache para a operação do serviço é removida e, quando a operação é invocada, uma nova resposta é gerada (ligando para a operação do serviço), armazenada em cache e devolvida ao cliente.  
  
> [!IMPORTANT]
> Para ASP.NET acessar um banco de dados SQL, você deve usar a [ferramenta de registro de servidor sql ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90)). Além disso, você deve permitir o acesso apropriado da conta de usuário ao banco de dados e à tabela. Para obter mais informações, consulte [Acessando o SQL Server a partir de um aplicativo web](https://docs.microsoft.com/previous-versions/aspnet/ht43wsex(v=vs.100)).  
  
## <a name="conditional-http-get-based-caching"></a>Cache conditional HTTP GET baseado  

  Em cenários Web HTTP, um HTTP GET condicional é frequentemente usado por serviços para implementar cache HTTP inteligente conforme descrito na [Especificação HTTP](https://www.w3.org/Protocols/rfc2616/rfc2616.html). Para isso, o serviço deve definir o valor do cabeçalho ETag na resposta HTTP. Ele também deve verificar o cabeçalho If-None-Match na solicitação HTTP para ver se algum dos ETag especificados corresponde ao ETag atual.  
  
 Para solicitações GET <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> e HEAD, pega um valor eTag e verifica-o no cabeçalho If-None-Match da solicitação. Se o cabeçalho estiver presente <xref:System.ServiceModel.Web.WebFaultException> e houver uma correspondência, um com um código de status HTTP 304 (Não Modificado) será lançado e um cabeçalho ETag será adicionado à resposta com o ETag correspondente.  
  
 Uma sobrecarga <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> do método pega uma última data modificada e verifica-a com o cabeçalho If-Modified-Since da solicitação. Se o cabeçalho estiver presente e o <xref:System.ServiceModel.Web.WebFaultException> recurso não tiver sido modificado desde então, um com um código de status HTTP 304 (Não Modificado) será lançado.  
  
 Para solicitações PUT, POST <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> e DELETE, leva o valor atual do ETag de um recurso. Se o valor atual do ETag for nulo, o método verificará se o cabeçalho If-None-Match tem um valor de "*".  Se o valor eTag atual não for um valor padrão, então o método verificará o valor atual do ETag em relação ao cabeçalho If-Match da solicitação. Em ambos os casos, <xref:System.ServiceModel.Web.WebFaultException> o método lança um com um código de status HTTP 412 (Falha na pré-condição) se o cabeçalho esperado não estiver presente na solicitação ou seu valor não satisfaça a verificação condicional e define o cabeçalho ETag da resposta ao valor ETag atual.  
  
 Tanto `CheckConditional` os métodos <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> quanto o método garantem que o valor ETag definido no cabeçalho de resposta seja um ETag válido de acordo com a especificação HTTP. Isso inclui cercar o valor do ETag em cotações duplas se eles ainda não estiverem presentes e escapar adequadamente de quaisquer caracteres internos de aspas duplas. A comparação fraca do ETag não é suportada.  
  
 O exemplo a seguir mostra como usar esses métodos.  
  
```csharp
[WebGet(UriTemplate = "{id}"), Description("Returns the specified customer from customers collection. Returns NotFound if there is no such customer. Supports conditional GET.")]
public Customer GetCustomer(string id)
{
    lock (writeLock)
    {
        // return NotFound if there is no item with the specified id.
        object itemEtag = customerEtags[id];
        if (itemEtag == null)
        {
            throw new WebFaultException(HttpStatusCode.NotFound);
        }
  
        // return NotModified if the client did a conditional GET and the customer item has not changed
        // since when the client last retrieved it
        WebOperationContext.Current.IncomingRequest.CheckConditionalRetrieve((long)itemEtag);
        Customer result = this.customers[id] as Customer;

        // set the customer etag before returning the result
        WebOperationContext.Current.OutgoingResponse.SetETag((long)itemEtag);
        return result;
    }
}
```  
  
## <a name="security-considerations"></a>Considerações de segurança  
 As solicitações que requerem autorização não devem ter suas respostas armazenadas em cache, pois a autorização não é realizada quando a resposta é atendida a partir do cache.  Cache tais respostas introduziria uma séria vulnerabilidade de segurança.  Normalmente, solicitações que requerem autorização fornecem dados específicos do usuário e, portanto, o cache do lado do servidor nem sequer é benéfico.  Em tais situações, o cache do lado do cliente ou simplesmente não cache em tudo será mais apropriado.
