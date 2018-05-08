---
title: Cache com suporte para serviços HTTP Web do WCF
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 8272ece5fcaf395b0ec8191afae8eabc998c7f8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="caching-support-for-wcf-web-http-services"></a>Cache com suporte para serviços HTTP Web do WCF
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] permite que você use o mecanismo de cache declarativo já disponível em ASP.NET em seus serviços WCF Web HTTP. Isso permite que você para respostas de cache de suas operações de serviço WCF Web HTTP. Quando um usuário envia um HTTP GET para o serviço que está configurado para armazenar em cache, ASP.NET envia a resposta armazenada em cache e o método de serviço não for chamado. Quando o cache expira, na próxima vez que um usuário envia um HTTP GET é chamado o método de serviço e uma vez é armazenado em cache a resposta. Para obter mais informações sobre o cache do ASP.NET, consulte [visão geral de cache do ASP.NET](http://go.microsoft.com/fwlink/?LinkId=152534)  
  
## <a name="basic-web-http-service-caching"></a>Cache de serviço do Web básico HTTP  
 Para habilitar o HTTP WEB do serviço de cache, você deve primeiro habilitar compatibilidade com ASP.NET aplicando o <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> à configuração de serviço <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> para <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> ou <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] apresenta um novo atributo chamado <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> que permite que você especifique um nome de perfil de cache. Esse atributo é aplicado a uma operação de serviço. O exemplo a seguir se aplica a <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> a um serviço para habilitar a compatibilidade com ASP.NET e configura o `GetCustomer` operação para armazenar em cache. O <!--zz<xref:System.ServiceModel.Activation.AspNetCacheProfileAttribute>--> `System.ServiceModel.Activation.AspNetCacheProfileAttribute` atributo especifica um perfil de cache que contém as configurações de cache a ser usado.  
  
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
>  Se o modo de compatibilidade ASP.NET não está ativado e o <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> é usada uma exceção será lançada.  
  
 O nome do perfil de cache especificado pelo <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifica um perfil de cache que é adicionado ao seu arquivo de configuração Web. config. O perfil de cache é definido com em um <`outputCacheSetting`> elemento conforme mostrado no exemplo de configuração a seguir.  
  
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
  
 Este é o mesmo elemento de configuração que está disponível para aplicativos ASP.NET. Para obter mais informações sobre perfis de cache do ASP.NET, consulte <xref:System.Web.Configuration.OutputCacheProfile>. Para serviços da Web HTTP, os atributos mais importantes no perfil de cache são: `cacheDuration` e `varyByParam`. Ambos os atributos são necessários. `cacheDuration` Define a quantidade de tempo que uma resposta deve ser armazenada em cache em segundos. `varyByParam` permite que você especifique um parâmetro de cadeia de caracteres de consulta que é usada para respostas de cache. Todas as solicitações feitas com valores de parâmetro de cadeia de caracteres de consulta diferentes são armazenadas em cache separadamente. Por exemplo, quando uma solicitação inicial é feita para http://MyServer/MyHttpService/MyOperation?param=10 todas as solicitações subsequentes feitas com o mesmo URI seriam retornadas a resposta armazenada em cache (desde que a duração do cache não tiver decorrido). As respostas para uma solicitação semelhante que é o mesmo, mas tem um valor diferente para o parâmetro de cadeia de caracteres de consulta de parâmetro são armazenadas separadamente. Se você não quiser que esse comportamento de cache separado, defina `varyByParam` para "none".  
  
## <a name="sql-cache-dependency"></a>Dependência de Cache do SQL  
 Respostas de serviço da Web HTTP podem também ser armazenados em cache com uma dependência de cache SQL. Se seu serviço WCF Web HTTP depende de dados armazenados em um banco de dados SQL, convém resposta do serviço de cache e invalidar a resposta em cache quando as alterações da tabela de banco de dados de dados no SQL. Esse comportamento é totalmente configurado no arquivo Web. config. Você deve primeiro definir uma cadeia de caracteres de conexão no <`connectionStrings`> elemento.  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 Em seguida, você deve habilitar a dependência de cache SQL dentro de um <`caching`> elemento dentro a <`system.web`> elemento conforme mostrado no exemplo de configuração a seguir.  
  
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
  
 Aqui a dependência de cache SQL está habilitada e uma hora de sondagem de 1000 milissegundos é definida. Cada vez que o tempo de pesquisa decorrido a tabela de banco de dados é verificado para atualizações. Se forem detectadas alterações, o conteúdo do cache é removido e na próxima vez em que a operação de serviço é invocado uma nova resposta é armazenado em cache. Dentro de <`sqlCacheDependency`> elemento adicionar os bancos de dados e fazer referência as cadeias de caracteres de conexão dentro de <`databases`> elemento conforme mostrado no exemplo a seguir.  
  
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
  
 Em seguida, você deve configurar as definições de cache de saída dentro de <`caching`> elemento conforme mostrado no exemplo a seguir.  
  
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
  
 Aqui a duração do cache é definida como 60 segundos, `varyByParam` está definida como none e `sqlDependency` é definido como uma lista delimitada por ponto e vírgula de pares de nome/tabela de banco de dados separados por vírgulas. Quando dados em `MyTable` é alterado a resposta armazenada em cache para a operação de serviço é removida e quando a operação é chamada uma nova resposta é gerada (chamando a operação de serviço), armazenados em cache e retornada ao cliente.  
  
> [!IMPORTANT]
>  Para o ASP.NET acessar um banco de dados SQL, você deve usar o [ferramenta de registro do ASP.NET SQL Server](http://go.microsoft.com/fwlink/?LinkId=152536). Além disso, você deve permitir o acesso de conta de usuário apropriado para o banco de dados e a tabela. Para obter mais informações, consulte [acessando o SQL Server de um aplicativo Web](http://go.microsoft.com/fwlink/?LinkId=178988).  
  
## <a name="conditional-http-get-based-caching"></a>HTTP condicional obter com base em cache  
 Em cenários de Web HTTP um HTTP GET condicional é geralmente usado pelos serviços para implementar cache inteligente de HTTP conforme descrito no [especificação HTTP](http://go.microsoft.com/fwlink/?LinkId=165800). Para fazer isso o serviço deve definir o valor de cabeçalho ETag na resposta HTTP. Ele também deve verificar o cabeçalho If-None-Match na solicitação HTTP para ver se qualquer uma da ETag especificado corresponde o ETag atual.  
  
 Para solicitações GET e HEAD, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> tem um valor de ETag e a compara com o cabeçalho If-None-Match da solicitação. Se o cabeçalho estiver presente e houver uma correspondência, um <xref:System.ServiceModel.Web.WebFaultException> com um HTTP 304 (não modificado) do código de status é gerado e um cabeçalho ETag é adicionado à resposta com o ETag correspondente.  
  
 Uma sobrecarga do <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> método leva a uma data da última modificação e a compara com o cabeçalho If-Modified-Since da solicitação. Se o cabeçalho estiver presente e o recurso não tiver sido modificado desde, um <xref:System.ServiceModel.Web.WebFaultException> com um HTTP 304 (não modificado) do código de status é gerado.  
  
 Para solicitações PUT, POST e DELETE, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> usa o valor de ETag atual de um recurso. Se o valor atual de ETag for nulo, o método verifica se o cabeçalho If-None-Match tem um valor de "*".  Se o valor de ETag atual não é um valor padrão, o método verifica o valor de ETag atual contra o cabeçalho If - Match da solicitação. Em ambos os casos, o método gera uma <xref:System.ServiceModel.Web.WebFaultException> com um status HTTP código 412 (Falha na pré-condição) se o cabeçalho esperado não está presente na solicitação ou seu valor não satisfaz a verificação condicional e define o cabeçalho ETag da resposta para o ETag atual valor.  
  
 Ambos os `CheckConditional` métodos e <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> método garante que o valor de ETag definido no cabeçalho de resposta é um ETag válido de acordo com a especificação de HTTP. Isso inclui ao redor do valor de ETag entre aspas duplas se eles não ainda estão presentes e corretamente ignorar nenhum caractere de aspas duplas interno. Não há suporte para a comparação de ETag fraca.  
  
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
 Solicitações que exigem autorização não devem ter suas respostas em cache, pois a autorização não é executada quando a resposta é servida do cache.  Essas respostas em cache geraria uma vulnerabilidade de segurança sério.  Geralmente, solicitações que exigem autorização fornecem dados específicos do usuário e, portanto, o cache do lado do servidor não é benéfico mesmo.  Em tais situações, o cache do cliente ou simplesmente não cache em todos os será mais adequado.
