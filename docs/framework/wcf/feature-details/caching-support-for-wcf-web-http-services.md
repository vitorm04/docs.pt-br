---
title: Cache com suporte para serviços HTTP Web do WCF
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 655e8807a78d542cd7fa586eca3750507891f74b
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988768"
---
# <a name="caching-support-for-wcf-web-http-services"></a>Cache com suporte para serviços HTTP Web do WCF
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]permite que você use o mecanismo de cache declarativo já disponível em ASP.NET em seus serviços HTTP Web WCF. Isso permite que você armazene em cache as respostas de suas operações de serviço HTTP Web do WCF. Quando um usuário envia um HTTP GET para seu serviço configurado para caching, o ASP.NET envia de volta a resposta armazenada em cache e o método de serviço não é chamado. Quando o cache expira, na próxima vez que um usuário envia um HTTP GET, seu método de serviço é chamado e a resposta é armazenada novamente em cache. Para obter mais informações sobre o cache ASP.NET, consulte [visão geral do cache de ASP.net](https://go.microsoft.com/fwlink/?LinkId=152534)  
  
## <a name="basic-web-http-service-caching"></a>Cache de serviço HTTP básico da Web  
 Para habilitar o Caching de serviço http Web, primeiro você deve habilitar a compatibilidade <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> ASP.NET aplicando o <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> à <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> configuração <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>de serviço para ou.  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]apresenta um novo atributo chamado <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> que permite especificar um nome de perfil de cache. Esse atributo é aplicado a uma operação de serviço. O exemplo a seguir aplica <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> o a um serviço para habilitar a compatibilidade de ASP.net e configura `GetCustomer` a operação para cache. O <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> atributo especifica um perfil de cache que contém as configurações de cache a serem usadas.  
  
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
  
 Você também deve ativar o modo de compatibilidade ASP.NET no arquivo Web. config, conforme mostrado no exemplo a seguir.  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
> Se o modo de compatibilidade ASP.net não estiver ativado e <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> o for usado, uma exceção será lançada.  
  
 O nome do perfil de cache especificado <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> pelo identifica um perfil de cache que é adicionado ao seu arquivo de configuração Web. config. O perfil de cache é definido com em um`outputCacheSetting`elemento < >, conforme mostrado no exemplo de configuração a seguir.  
  
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
  
 Esse é o mesmo elemento de configuração que está disponível para aplicativos ASP.NET. Para obter mais informações sobre perfis de cache ASP.NET <xref:System.Web.Configuration.OutputCacheProfile>, consulte. Para os serviços http da Web, os atributos mais importantes no perfil de cache `cacheDuration` são `varyByParam`: e. Ambos os atributos são necessários. `cacheDuration`define a quantidade de tempo que uma resposta deve ser armazenada em cache em segundos. `varyByParam`permite que você especifique um parâmetro de cadeia de caracteres de consulta que é usado para armazenar em cache as respostas. Todas as solicitações feitas com diferentes valores de parâmetros de cadeia de caracteres de consulta são armazenadas em cache separadamente. Por exemplo, depois que uma solicitação inicial é feita `http://MyServer/MyHttpService/MyOperation?param=10`para, todas as solicitações subsequentes feitas com o mesmo URI retornariam a resposta armazenada em cache (desde que a duração do cache não tenha decorrido). Respostas para uma solicitação semelhante que é a mesma, mas que tem um valor diferente para o parâmetro de cadeia de caracteres de consulta de parâmetro são armazenadas em cache separadamente. Se você não quiser esse comportamento de cache separado, defina `varyByParam` como "None".  
  
## <a name="sql-cache-dependency"></a>Dependência de cache do SQL  
 As respostas do serviço HTTP da Web também podem ser armazenadas em cache com uma dependência de cache do SQL. Se o serviço HTTP Web do WCF depende dos dados armazenados em um banco de dado SQL, talvez você queira armazenar em cache a resposta do serviço e invalidar a resposta armazenada em cache quando os dados na tabela do SQL Database forem alterados. Esse comportamento é configurado completamente dentro do arquivo Web. config. Você deve primeiro definir uma cadeia de conexão no elemento`connectionStrings`< >.  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 Em seguida, você deve habilitar a dependência de cache`caching`do SQL dentro de um`system.web`elemento < > dentro do elemento < >, conforme mostrado no exemplo de configuração a seguir.  
  
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
  
 Aqui, a dependência do cache SQL está habilitada e um tempo de sondagem de 1000 milissegundos está definido. Cada vez que o tempo de sondagem decorre, a tabela do banco de dados é verificada quanto a atualizações. Se forem detectadas alterações, o conteúdo do cache será removido e na próxima vez que a operação de serviço for invocada, uma nova resposta será armazenada em cache. Dentro do elemento`sqlCacheDependency`< > Adicione os bancos de dados e referencie as cadeias de conexão dentro`databases`do elemento < >, conforme mostrado no exemplo a seguir.  
  
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
  
 Em seguida, você deve definir as configurações de cache de`caching`saída dentro do elemento < >, conforme mostrado no exemplo a seguir.  
  
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
  
 Aqui, a duração do cache é definida como 60 `varyByParam` segundos, é definida como `sqlDependency` None e é definida como uma lista delimitada por ponto e vírgula de pares de nome de banco de dados/tabela separados por dois-pontos. Quando os dados `MyTable` no são alterados, a resposta armazenada em cache para a operação de serviço é removida e quando a operação é invocada, uma nova resposta é gerada (chamando a operação de serviço), armazenada em cache e retornada ao cliente.  
  
> [!IMPORTANT]
> Para que o ASP.NET acesse um banco de dados SQL, você deve usar a [ferramenta de registro do ASP.NET SQL Server](https://go.microsoft.com/fwlink/?LinkId=152536). Além disso, você deve permitir o acesso apropriado à conta de usuário ao banco de dados e à tabela. Para obter mais informações, consulte Acessando [SQL Server de um aplicativo Web](https://go.microsoft.com/fwlink/?LinkId=178988).  
  
## <a name="conditional-http-get-based-caching"></a>Cache baseado em HTTP GET condicional  
 Em cenários de HTTP da Web, uma GET HTTP condicional é frequentemente usada pelos serviços para implementar o cache HTTP inteligente, conforme descrito na [especificação http](https://go.microsoft.com/fwlink/?LinkId=165800). Para fazer isso, o serviço deve definir o valor do cabeçalho ETag na resposta HTTP. Ele também deve verificar o cabeçalho If-None-Match na solicitação HTTP para ver se qualquer ETag especificado corresponde ao ETag atual.  
  
 Para solicitações GET e Head, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> usa um valor ETag e o verifica em relação ao cabeçalho If-None-Match da solicitação. Se o cabeçalho estiver presente e houver uma correspondência, um <xref:System.ServiceModel.Web.WebFaultException> com um código de status http 304 (não modificado) será gerado e um cabeçalho ETag será adicionado à resposta com a ETag correspondente.  
  
 Uma sobrecarga do <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> método usa uma data da última modificação e a verifica no cabeçalho If-Modified-Since da solicitação. Se o cabeçalho estiver presente e o recurso não tiver sido modificado desde, um <xref:System.ServiceModel.Web.WebFaultException> com um código de status http 304 (não modificado) será gerado.  
  
 Para solicitações put, post e Delete, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> o usa o valor de eTag atual de um recurso. Se o valor de ETag atual for nulo, o método verificará se o cabeçalho If-None-Match tem um valor de "*".  Se o valor de ETag atual não for um valor padrão, o método verificará o valor de ETag atual em relação ao cabeçalho If-Match da solicitação. Em ambos os casos, o método gera <xref:System.ServiceModel.Web.WebFaultException> um com um código de status http 412 (falha na pré-condição) se o cabeçalho esperado não estiver presente na solicitação ou se seu valor não atender à verificação condicional e definir o cabeçalho ETag da resposta para a ETag atual valor.  
  
 Os métodos e o <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> método garantem que o valor de eTag definido no cabeçalho de resposta seja um ETag válido de acordo com a especificação http. `CheckConditional` Isso inclui o circundar o valor de ETag entre aspas duplas se elas ainda não estiverem presentes e escapar corretamente quaisquer caracteres de aspas duplas internas. Não há suporte para a comparação de ETag fraco.  
  
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
  
## <a name="security-considerations"></a>Considerações sobre segurança  
 As solicitações que exigem autorização não devem ter suas respostas armazenadas em cache, pois a autorização não é executada quando a resposta é servida do cache.  Armazenar essas respostas em cache introduziria uma séria vulnerabilidade de segurança.  Normalmente, as solicitações que exigem autorização fornecem dados específicos do usuário e, portanto, o armazenamento em cache do lado do servidor não é ainda benéfico.  Nessas situações, o armazenamento em cache do lado do cliente ou simplesmente não o armazenamento em cache será mais apropriado.
