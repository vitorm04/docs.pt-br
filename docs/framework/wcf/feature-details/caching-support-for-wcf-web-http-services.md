---
title: Cache com suporte para serviços HTTP Web do WCF
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 0445f0214f90873dad4241789db270c9b6f4a2f6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559409"
---
# <a name="caching-support-for-wcf-web-http-services"></a><span data-ttu-id="ab032-102">Cache com suporte para serviços HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="ab032-102">Caching Support for WCF Web HTTP Services</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="ab032-103">permite que você use o mecanismo de cache declarativo já disponível em ASP.NET em seus serviços HTTP Web WCF.</span><span class="sxs-lookup"><span data-stu-id="ab032-103">enables you to use the declarative caching mechanism already available in ASP.NET in your WCF Web HTTP services.</span></span> <span data-ttu-id="ab032-104">Isso permite que você armazene em cache as respostas de suas operações de serviço HTTP Web do WCF.</span><span class="sxs-lookup"><span data-stu-id="ab032-104">This allows you to cache responses from your WCF Web HTTP service operations.</span></span> <span data-ttu-id="ab032-105">Quando um usuário envia um HTTP GET para seu serviço configurado para caching, o ASP.NET envia de volta a resposta armazenada em cache e o método de serviço não é chamado.</span><span class="sxs-lookup"><span data-stu-id="ab032-105">When a user sends an HTTP GET to your service that is configured for caching, ASP.NET sends back the cached response and the service method is not called.</span></span> <span data-ttu-id="ab032-106">Quando o cache expira, na próxima vez que um usuário envia um HTTP GET, seu método de serviço é chamado e a resposta é armazenada novamente em cache.</span><span class="sxs-lookup"><span data-stu-id="ab032-106">When the cache expires, the next time a user sends an HTTP GET, your service method is called and the response is once again cached.</span></span> <span data-ttu-id="ab032-107">Para obter mais informações sobre o cache ASP.NET, consulte [visão geral do cache de ASP.net](/previous-versions/aspnet/ms178597(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ab032-107">For more information about ASP.NET caching, see [ASP.NET Caching Overview](/previous-versions/aspnet/ms178597(v=vs.100)).</span></span>  
  
## <a name="basic-web-http-service-caching"></a><span data-ttu-id="ab032-108">Cache de serviço HTTP básico da Web</span><span class="sxs-lookup"><span data-stu-id="ab032-108">Basic Web HTTP Service Caching</span></span>  

  <span data-ttu-id="ab032-109">Para habilitar o cache do serviço HTTP WEB, primeiro você deve habilitar a compatibilidade do ASP.NET aplicando o <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> à configuração de serviço <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> para <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> ou <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required> .</span><span class="sxs-lookup"><span data-stu-id="ab032-109">To enable WEB HTTP service caching, you must first enable ASP.NET compatibility by applying the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to the service setting <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> or <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span></span>  
  
 <span data-ttu-id="ab032-110">.NET Framework 4 introduz um novo atributo chamado <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> que permite que você especifique um nome de perfil de cache.</span><span class="sxs-lookup"><span data-stu-id="ab032-110">.NET Framework 4 introduces a new attribute called <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> that allows you to specify a cache profile name.</span></span> <span data-ttu-id="ab032-111">Esse atributo é aplicado a uma operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="ab032-111">This attribute is applied to a service operation.</span></span> <span data-ttu-id="ab032-112">O exemplo a seguir aplica o <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> a um serviço para habilitar a compatibilidade de ASP.net e configura a `GetCustomer` operação para cache.</span><span class="sxs-lookup"><span data-stu-id="ab032-112">The following example applies the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to a service to enable ASP.NET compatibility and configures the `GetCustomer` operation for caching.</span></span> <span data-ttu-id="ab032-113">O <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> atributo especifica um perfil de cache que contém as configurações de cache a serem usadas.</span><span class="sxs-lookup"><span data-stu-id="ab032-113">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> attribute specifies a cache profile that contains the cache settings to be used.</span></span>  
  
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
  
<span data-ttu-id="ab032-114">Ative também o modo de compatibilidade ASP.NET no arquivo Web.config, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ab032-114">Also turn on ASP.NET compatibility mode in the Web.config file as shown in the following example.</span></span>  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
> <span data-ttu-id="ab032-115">Se o modo de compatibilidade ASP.NET não estiver ativado e o <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> for usado, uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="ab032-115">If ASP.NET compatibility mode is not turned on and the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is used an exception is thrown.</span></span>  
  
 <span data-ttu-id="ab032-116">O nome do perfil de cache especificado pelo <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifica um perfil de cache que é adicionado ao arquivo de configuração Web.config.</span><span class="sxs-lookup"><span data-stu-id="ab032-116">The cache profile name specified by the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifies a cache profile that is added to your Web.config configuration file.</span></span> <span data-ttu-id="ab032-117">O perfil de cache é definido com em um `outputCacheSetting` elemento <>, conforme mostrado no exemplo de configuração a seguir.</span><span class="sxs-lookup"><span data-stu-id="ab032-117">The cache profile is defined with in a <`outputCacheSetting`> element as shown in the following configuration example.</span></span>  
  
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
  
 <span data-ttu-id="ab032-118">Esse é o mesmo elemento de configuração que está disponível para aplicativos ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ab032-118">This is the same configuration element that is available to ASP.NET applications.</span></span> <span data-ttu-id="ab032-119">Para obter mais informações sobre perfis de cache ASP.NET, consulte <xref:System.Web.Configuration.OutputCacheProfile> .</span><span class="sxs-lookup"><span data-stu-id="ab032-119">For more information about ASP.NET cache profiles, see <xref:System.Web.Configuration.OutputCacheProfile>.</span></span> <span data-ttu-id="ab032-120">Para os serviços HTTP da Web, os atributos mais importantes no perfil de cache são: `cacheDuration` e `varyByParam` .</span><span class="sxs-lookup"><span data-stu-id="ab032-120">For Web HTTP services, the most important attributes in the cache profile are: `cacheDuration` and `varyByParam`.</span></span> <span data-ttu-id="ab032-121">Ambos os atributos são necessários.</span><span class="sxs-lookup"><span data-stu-id="ab032-121">Both of these attributes are required.</span></span> <span data-ttu-id="ab032-122">`cacheDuration` define a quantidade de tempo que uma resposta deve ser armazenada em cache em segundos.</span><span class="sxs-lookup"><span data-stu-id="ab032-122">`cacheDuration` sets the amount of time a response should be cached in seconds.</span></span> <span data-ttu-id="ab032-123">`varyByParam` permite que você especifique um parâmetro de cadeia de caracteres de consulta que é usado para armazenar em cache as respostas.</span><span class="sxs-lookup"><span data-stu-id="ab032-123">`varyByParam` allows you to specify a query string parameter that is used to cache responses.</span></span> <span data-ttu-id="ab032-124">Todas as solicitações feitas com diferentes valores de parâmetros de cadeia de caracteres de consulta são armazenadas em cache separadamente.</span><span class="sxs-lookup"><span data-stu-id="ab032-124">All requests made with different query string parameter values are cached separately.</span></span> <span data-ttu-id="ab032-125">Por exemplo, depois que uma solicitação inicial é feita para `http://MyServer/MyHttpService/MyOperation?param=10` , todas as solicitações subsequentes feitas com o mesmo URI retornariam a resposta armazenada em cache (desde que a duração do cache não tenha decorrido).</span><span class="sxs-lookup"><span data-stu-id="ab032-125">For example, once an initial request is made to `http://MyServer/MyHttpService/MyOperation?param=10`, all subsequent requests made with the same URI would be returned the cached response (so long as the cache duration has not elapsed).</span></span> <span data-ttu-id="ab032-126">Respostas para uma solicitação semelhante que é a mesma, mas que tem um valor diferente para o parâmetro de cadeia de caracteres de consulta de parâmetro são armazenadas em cache separadamente.</span><span class="sxs-lookup"><span data-stu-id="ab032-126">Responses for a similar request that is the same but has a different value for the parameter query string parameter are cached separately.</span></span> <span data-ttu-id="ab032-127">Se você não quiser esse comportamento de cache separado, defina `varyByParam` como "None".</span><span class="sxs-lookup"><span data-stu-id="ab032-127">If you do not want this separate caching behavior, set `varyByParam` to "none".</span></span>  
  
## <a name="sql-cache-dependency"></a><span data-ttu-id="ab032-128">Dependência de cache do SQL</span><span class="sxs-lookup"><span data-stu-id="ab032-128">SQL Cache Dependency</span></span>  

  <span data-ttu-id="ab032-129">As respostas do serviço HTTP da Web também podem ser armazenadas em cache com uma dependência de cache do SQL.</span><span class="sxs-lookup"><span data-stu-id="ab032-129">Web HTTP service responses can also be cached with a SQL cache dependency.</span></span> <span data-ttu-id="ab032-130">Se o serviço HTTP Web do WCF depende dos dados armazenados em um banco de dado SQL, talvez você queira armazenar em cache a resposta do serviço e invalidar a resposta armazenada em cache quando os dados na tabela do SQL Database forem alterados.</span><span class="sxs-lookup"><span data-stu-id="ab032-130">If your WCF Web HTTP service depends on data stored in a SQL database, you may want to cache the service's response and invalidate the cached response when data in the SQL database table changes.</span></span> <span data-ttu-id="ab032-131">Esse comportamento é configurado completamente dentro do arquivo de Web.config.</span><span class="sxs-lookup"><span data-stu-id="ab032-131">This behavior is configured completely within the Web.config file.</span></span> <span data-ttu-id="ab032-132">Primeiro, defina uma cadeia de conexão no `connectionStrings` elemento <>.</span><span class="sxs-lookup"><span data-stu-id="ab032-132">First, define a connection string in the <`connectionStrings`> element.</span></span>  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 <span data-ttu-id="ab032-133">Em seguida, você deve habilitar a dependência de cache do SQL dentro de um `caching` elemento <> dentro do `system.web` elemento <>, conforme mostrado no exemplo de configuração a seguir.</span><span class="sxs-lookup"><span data-stu-id="ab032-133">Then you must enable SQL cache dependency within a <`caching`> element within the <`system.web`> element as shown in the following config example.</span></span>  
  
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
  
 <span data-ttu-id="ab032-134">Aqui, a dependência do cache SQL está habilitada e um tempo de sondagem de 1000 milissegundos está definido.</span><span class="sxs-lookup"><span data-stu-id="ab032-134">Here SQL cache dependency is enabled and a polling time of 1000 milliseconds is set.</span></span> <span data-ttu-id="ab032-135">Cada vez que o tempo de sondagem decorre, a tabela do banco de dados é verificada quanto a atualizações.</span><span class="sxs-lookup"><span data-stu-id="ab032-135">Each time the polling time elapses the database table is checked for updates.</span></span> <span data-ttu-id="ab032-136">Se forem detectadas alterações, o conteúdo do cache será removido e na próxima vez que a operação de serviço for invocada, uma nova resposta será armazenada em cache.</span><span class="sxs-lookup"><span data-stu-id="ab032-136">If changes are detected the contents of the cache are removed and the next time the service operation is invoked a new response is cached.</span></span> <span data-ttu-id="ab032-137">Dentro do `sqlCacheDependency` elemento <> adicione os bancos de dados e referencie as cadeias de conexão dentro do `databases` elemento <>, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ab032-137">Within the <`sqlCacheDependency`> element add the databases and reference the connection strings within the <`databases`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="ab032-138">Em seguida, você deve definir as configurações de cache de saída dentro do `caching` elemento <>, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ab032-138">Next you must configure the output cache settings within the <`caching`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="ab032-139">Aqui, a duração do cache é definida como 60 segundos, `varyByParam` é definida como None e `sqlDependency` é definida como uma lista delimitada por ponto-e-vírgula de pares de nome de banco de dados/tabela separados por dois-pontos.</span><span class="sxs-lookup"><span data-stu-id="ab032-139">Here the cache duration is set to 60 seconds, `varyByParam` is set to none, and `sqlDependency` is set to a semicolon-delimited list of database name/table pairs separated by colons.</span></span> <span data-ttu-id="ab032-140">Quando os dados no `MyTable` são alterados, a resposta armazenada em cache para a operação de serviço é removida e quando a operação é invocada, uma nova resposta é gerada (chamando a operação de serviço), armazenada em cache e retornada ao cliente.</span><span class="sxs-lookup"><span data-stu-id="ab032-140">When data in `MyTable` is changed the cached response for the service operation is removed and when the operation is invoked a new response is generated (by calling the service operation), cached, and returned to the client.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ab032-141">Para que o ASP.NET acesse um banco de dados SQL, você deve usar a [ferramenta de registro do ASP.NET SQL Server](/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="ab032-141">For ASP.NET to access a SQL database, you must use the [ASP.NET SQL Server Registration Tool](/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90)).</span></span> <span data-ttu-id="ab032-142">Além disso, você deve permitir o acesso apropriado à conta de usuário ao banco de dados e à tabela.</span><span class="sxs-lookup"><span data-stu-id="ab032-142">In addition you must allow the appropriate user account access to the database and table.</span></span> <span data-ttu-id="ab032-143">Para obter mais informações, consulte [Acessando SQL Server de um aplicativo Web](/previous-versions/aspnet/ht43wsex(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ab032-143">For more information, see [Accessing SQL Server from a Web Application](/previous-versions/aspnet/ht43wsex(v=vs.100)).</span></span>  
  
## <a name="conditional-http-get-based-caching"></a><span data-ttu-id="ab032-144">Cache baseado em HTTP GET condicional</span><span class="sxs-lookup"><span data-stu-id="ab032-144">Conditional HTTP GET Based Caching</span></span>  

  <span data-ttu-id="ab032-145">Em cenários de HTTP da Web, uma GET HTTP condicional é frequentemente usada pelos serviços para implementar o cache HTTP inteligente, conforme descrito na [especificação http](https://www.w3.org/Protocols/rfc2616/rfc2616.html).</span><span class="sxs-lookup"><span data-stu-id="ab032-145">In Web HTTP scenarios a conditional HTTP GET is often used by services to implement intelligent HTTP caching as described in the [HTTP Specification](https://www.w3.org/Protocols/rfc2616/rfc2616.html).</span></span> <span data-ttu-id="ab032-146">Para fazer isso, o serviço deve definir o valor do cabeçalho ETag na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="ab032-146">To do this, the service must set the value of the ETag header in the HTTP response.</span></span> <span data-ttu-id="ab032-147">Ele também deve verificar o cabeçalho If-None-Match na solicitação HTTP para ver se qualquer ETag especificado corresponde ao ETag atual.</span><span class="sxs-lookup"><span data-stu-id="ab032-147">It also must check the If-None-Match header in the HTTP request to see whether any of the ETag specified matches the current ETag.</span></span>  
  
 <span data-ttu-id="ab032-148">Para solicitações GET e HEAD, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> usa um valor ETag e o verifica em relação ao cabeçalho If-None-Match da solicitação.</span><span class="sxs-lookup"><span data-stu-id="ab032-148">For GET and HEAD requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> takes an ETag value and checks it against the If-None-Match header of the request.</span></span> <span data-ttu-id="ab032-149">Se o cabeçalho estiver presente e houver uma correspondência, um <xref:System.ServiceModel.Web.WebFaultException> com um código de status HTTP 304 (não modificado) será gerado e um cabeçalho ETag será adicionado à resposta com a ETag correspondente.</span><span class="sxs-lookup"><span data-stu-id="ab032-149">If the header is present and there is a match, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown and an ETag header is added to the response with the matching ETag.</span></span>  
  
 <span data-ttu-id="ab032-150">Uma sobrecarga do <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> método usa uma data da última modificação e a verifica no cabeçalho If-Modified-Since da solicitação.</span><span class="sxs-lookup"><span data-stu-id="ab032-150">One overload of the <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> method takes a last modified date and checks it against the If-Modified-Since header of the request.</span></span> <span data-ttu-id="ab032-151">Se o cabeçalho estiver presente e o recurso não tiver sido modificado desde, um <xref:System.ServiceModel.Web.WebFaultException> com um código de status HTTP 304 (não modificado) será gerado.</span><span class="sxs-lookup"><span data-stu-id="ab032-151">If the header is present and the resource has not been modified since, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown.</span></span>  
  
 <span data-ttu-id="ab032-152">Para solicitações PUT, POST e DELETE, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> o usa o valor de eTag atual de um recurso.</span><span class="sxs-lookup"><span data-stu-id="ab032-152">For PUT, POST, and DELETE requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> takes the current ETag value of a resource.</span></span> <span data-ttu-id="ab032-153">Se o valor de ETag atual for nulo, o método verificará se o cabeçalho If-None-Match tem um valor de "\*".</span><span class="sxs-lookup"><span data-stu-id="ab032-153">If the current ETag value is null, the method checks that the If-None- Match header has a value of "\*".</span></span>  <span data-ttu-id="ab032-154">Se o valor de ETag atual não for um valor padrão, o método verificará o valor de ETag atual em relação ao cabeçalho If-Match da solicitação.</span><span class="sxs-lookup"><span data-stu-id="ab032-154">If the current ETag value is not a default value, then the method checks the current ETag value against the If- Match header of the request.</span></span> <span data-ttu-id="ab032-155">Em ambos os casos, o método gera um <xref:System.ServiceModel.Web.WebFaultException> com um código de status HTTP 412 (falha na pré-condição) se o cabeçalho esperado não estiver presente na solicitação ou se seu valor não atender à verificação condicional e definir o cabeçalho ETag da resposta para o valor de eTag atual.</span><span class="sxs-lookup"><span data-stu-id="ab032-155">In either case, the method throws a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 412 (Precondition Failed) if the expected header is not present in the request or its value does not satisfy the conditional check and sets the ETag header of the response to the current ETag value.</span></span>  
  
 <span data-ttu-id="ab032-156">Os `CheckConditional` métodos e o <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> método garantem que o valor de eTag definido no cabeçalho de resposta seja um ETag válido de acordo com a especificação http.</span><span class="sxs-lookup"><span data-stu-id="ab032-156">Both the `CheckConditional` methods and the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> method ensures that the ETag value set on the response header is a valid ETag according to the HTTP specification.</span></span> <span data-ttu-id="ab032-157">Isso inclui o circundar o valor de ETag entre aspas duplas se elas ainda não estiverem presentes e escapar corretamente quaisquer caracteres de aspas duplas internas.</span><span class="sxs-lookup"><span data-stu-id="ab032-157">This includes surrounding the ETag value in double quotes if they are not already present and properly escaping any internal double quote characters.</span></span> <span data-ttu-id="ab032-158">Não há suporte para a comparação de ETag fraco.</span><span class="sxs-lookup"><span data-stu-id="ab032-158">Weak ETag comparison is not supported.</span></span>  
  
 <span data-ttu-id="ab032-159">O exemplo a seguir mostra como usar esses métodos.</span><span class="sxs-lookup"><span data-stu-id="ab032-159">The following example shows how to use these methods.</span></span>  
  
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
  
## <a name="security-considerations"></a><span data-ttu-id="ab032-160">Considerações sobre segurança</span><span class="sxs-lookup"><span data-stu-id="ab032-160">Security Considerations</span></span>  
 <span data-ttu-id="ab032-161">As solicitações que exigem autorização não devem ter suas respostas armazenadas em cache, pois a autorização não é executada quando a resposta é servida do cache.</span><span class="sxs-lookup"><span data-stu-id="ab032-161">Requests that require authorization should not have their responses cached, because the authorization is not performed when the response is served from the cache.</span></span>  <span data-ttu-id="ab032-162">Armazenar essas respostas em cache introduziria uma séria vulnerabilidade de segurança.</span><span class="sxs-lookup"><span data-stu-id="ab032-162">Caching such responses would introduce a serious security vulnerability.</span></span>  <span data-ttu-id="ab032-163">Normalmente, as solicitações que exigem autorização fornecem dados específicos do usuário e, portanto, o armazenamento em cache do lado do servidor não é ainda benéfico.</span><span class="sxs-lookup"><span data-stu-id="ab032-163">Usually, requests that require authorization provide user-specific data and therefore server-side caching is not even beneficial.</span></span>  <span data-ttu-id="ab032-164">Nessas situações, o armazenamento em cache do lado do cliente ou simplesmente não o armazenamento em cache será mais apropriado.</span><span class="sxs-lookup"><span data-stu-id="ab032-164">In such situations, client-side caching or simply not caching at all will be more appropriate.</span></span>
