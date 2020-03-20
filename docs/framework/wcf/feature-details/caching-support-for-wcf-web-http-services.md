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
# <a name="caching-support-for-wcf-web-http-services"></a><span data-ttu-id="db3d5-102">Cache com suporte para serviços HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="db3d5-102">Caching Support for WCF Web HTTP Services</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="db3d5-103">permite que você use o mecanismo de cache declarativo já disponível em ASP.NET em seus serviços WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="db3d5-103">enables you to use the declarative caching mechanism already available in ASP.NET in your WCF Web HTTP services.</span></span> <span data-ttu-id="db3d5-104">Isso permite que você faça cache de respostas de suas operações de serviço WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="db3d5-104">This allows you to cache responses from your WCF Web HTTP service operations.</span></span> <span data-ttu-id="db3d5-105">Quando um usuário envia um HTTP GET para o seu serviço configurado para cache, ASP.NET envia de volta a resposta armazenada em cache e o método de serviço não é chamado.</span><span class="sxs-lookup"><span data-stu-id="db3d5-105">When a user sends an HTTP GET to your service that is configured for caching, ASP.NET sends back the cached response and the service method is not called.</span></span> <span data-ttu-id="db3d5-106">Quando o cache expira, na próxima vez que um usuário enviar um HTTP GET, seu método de serviço é chamado e a resposta é novamente armazenada em cache.</span><span class="sxs-lookup"><span data-stu-id="db3d5-106">When the cache expires, the next time a user sends an HTTP GET, your service method is called and the response is once again cached.</span></span> <span data-ttu-id="db3d5-107">Para obter mais informações sobre ASP.NET cache, consulte [ASP.NET Visão Geral do Cache](https://docs.microsoft.com/previous-versions/aspnet/ms178597(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="db3d5-107">For more information about ASP.NET caching, see [ASP.NET Caching Overview](https://docs.microsoft.com/previous-versions/aspnet/ms178597(v=vs.100)).</span></span>  
  
## <a name="basic-web-http-service-caching"></a><span data-ttu-id="db3d5-108">Caching básico do serviço WEB HTTP</span><span class="sxs-lookup"><span data-stu-id="db3d5-108">Basic Web HTTP Service Caching</span></span>  

  <span data-ttu-id="db3d5-109">Para habilitar o cache de serviço WEB HTTP, você <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> deve primeiro <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> habilitar ASP.NET compatibilidade aplicando a configuração de serviço para ou <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span><span class="sxs-lookup"><span data-stu-id="db3d5-109">To enable WEB HTTP service caching, you must first enable ASP.NET compatibility by applying the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to the service setting <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> or <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span></span>  
  
 <span data-ttu-id="db3d5-110">.NET Framework 4 introduz um <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> novo atributo chamado que permite especificar um nome de perfil de cache.</span><span class="sxs-lookup"><span data-stu-id="db3d5-110">.NET Framework 4 introduces a new attribute called <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> that allows you to specify a cache profile name.</span></span> <span data-ttu-id="db3d5-111">Este atributo é aplicado a uma operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="db3d5-111">This attribute is applied to a service operation.</span></span> <span data-ttu-id="db3d5-112">O exemplo a <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> seguir aplica-se a um serviço `GetCustomer` para habilitar ASP.NET compatibilidade e configura a operação para cache.</span><span class="sxs-lookup"><span data-stu-id="db3d5-112">The following example applies the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to a service to enable ASP.NET compatibility and configures the `GetCustomer` operation for caching.</span></span> <span data-ttu-id="db3d5-113">O <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> atributo especifica um perfil de cache que contém as configurações de cache a serem usadas.</span><span class="sxs-lookup"><span data-stu-id="db3d5-113">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> attribute specifies a cache profile that contains the cache settings to be used.</span></span>  
  
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
  
<span data-ttu-id="db3d5-114">Também ative ASP.NET modo de compatibilidade no arquivo Web.config, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="db3d5-114">Also turn on ASP.NET compatibility mode in the Web.config file as shown in the following example.</span></span>  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
> <span data-ttu-id="db3d5-115">Se ASP.NET modo de compatibilidade não <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> estiver ligado e for usado, uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="db3d5-115">If ASP.NET compatibility mode is not turned on and the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is used an exception is thrown.</span></span>  
  
 <span data-ttu-id="db3d5-116">O nome do perfil <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> de cache especificado pelo identifica um perfil de cache adicionado ao seu arquivo de configuração Web.config.</span><span class="sxs-lookup"><span data-stu-id="db3d5-116">The cache profile name specified by the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifies a cache profile that is added to your Web.config configuration file.</span></span> <span data-ttu-id="db3d5-117">O perfil de cache é `outputCacheSetting` definido com um elemento <> como mostrado no exemplo de configuração a seguir.</span><span class="sxs-lookup"><span data-stu-id="db3d5-117">The cache profile is defined with in a <`outputCacheSetting`> element as shown in the following configuration example.</span></span>  
  
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
  
 <span data-ttu-id="db3d5-118">Este é o mesmo elemento de configuração que está disponível para ASP.NET aplicativos.</span><span class="sxs-lookup"><span data-stu-id="db3d5-118">This is the same configuration element that is available to ASP.NET applications.</span></span> <span data-ttu-id="db3d5-119">Para obter mais informações sobre <xref:System.Web.Configuration.OutputCacheProfile>ASP.NET perfis de cache, consulte .</span><span class="sxs-lookup"><span data-stu-id="db3d5-119">For more information about ASP.NET cache profiles, see <xref:System.Web.Configuration.OutputCacheProfile>.</span></span> <span data-ttu-id="db3d5-120">Para os serviços Web HTTP, os atributos mais importantes no perfil de cache são: `cacheDuration` e `varyByParam`.</span><span class="sxs-lookup"><span data-stu-id="db3d5-120">For Web HTTP services, the most important attributes in the cache profile are: `cacheDuration` and `varyByParam`.</span></span> <span data-ttu-id="db3d5-121">Ambos os atributos são necessários.</span><span class="sxs-lookup"><span data-stu-id="db3d5-121">Both of these attributes are required.</span></span> <span data-ttu-id="db3d5-122">`cacheDuration`define a quantidade de tempo que uma resposta deve ser armazenada em cache em segundos.</span><span class="sxs-lookup"><span data-stu-id="db3d5-122">`cacheDuration` sets the amount of time a response should be cached in seconds.</span></span> <span data-ttu-id="db3d5-123">`varyByParam`permite especificar um parâmetro de seqüência de consultas que é usado para cache de respostas.</span><span class="sxs-lookup"><span data-stu-id="db3d5-123">`varyByParam` allows you to specify a query string parameter that is used to cache responses.</span></span> <span data-ttu-id="db3d5-124">Todas as solicitações feitas com diferentes valores de parâmetro de seqüência de consulta são armazenadas em cache separadamente.</span><span class="sxs-lookup"><span data-stu-id="db3d5-124">All requests made with different query string parameter values are cached separately.</span></span> <span data-ttu-id="db3d5-125">Por exemplo, uma vez que `http://MyServer/MyHttpService/MyOperation?param=10`uma solicitação inicial seja feita para , todas as solicitações subseqüentes feitas com o mesmo URI seriam devolvidas a resposta em cache (desde que a duração do cache não tenha transcorrido).</span><span class="sxs-lookup"><span data-stu-id="db3d5-125">For example, once an initial request is made to `http://MyServer/MyHttpService/MyOperation?param=10`, all subsequent requests made with the same URI would be returned the cached response (so long as the cache duration has not elapsed).</span></span> <span data-ttu-id="db3d5-126">As respostas para uma solicitação semelhante que é a mesma, mas tem um valor diferente para o parâmetro de seqüência de string de consulta de parâmetros, são armazenadas separadamente.</span><span class="sxs-lookup"><span data-stu-id="db3d5-126">Responses for a similar request that is the same but has a different value for the parameter query string parameter are cached separately.</span></span> <span data-ttu-id="db3d5-127">Se você não quiser esse comportamento `varyByParam` de cache separado, defina como "nenhum".</span><span class="sxs-lookup"><span data-stu-id="db3d5-127">If you do not want this separate caching behavior, set `varyByParam` to "none".</span></span>  
  
## <a name="sql-cache-dependency"></a><span data-ttu-id="db3d5-128">Dependência de cache SQL</span><span class="sxs-lookup"><span data-stu-id="db3d5-128">SQL Cache Dependency</span></span>  

  <span data-ttu-id="db3d5-129">As respostas do serviço Web HTTP também podem ser armazenadas em cache com uma dependência de cache SQL.</span><span class="sxs-lookup"><span data-stu-id="db3d5-129">Web HTTP service responses can also be cached with a SQL cache dependency.</span></span> <span data-ttu-id="db3d5-130">Se o serviço WCF Web HTTP depender dos dados armazenados em um banco de dados SQL, você pode querer fazer um cache da resposta do serviço e invalidar a resposta armazenada em cache quando os dados na tabela de banco de dados SQL forem alterados.</span><span class="sxs-lookup"><span data-stu-id="db3d5-130">If your WCF Web HTTP service depends on data stored in a SQL database, you may want to cache the service's response and invalidate the cached response when data in the SQL database table changes.</span></span> <span data-ttu-id="db3d5-131">Esse comportamento é configurado completamente dentro do arquivo Web.config.</span><span class="sxs-lookup"><span data-stu-id="db3d5-131">This behavior is configured completely within the Web.config file.</span></span> <span data-ttu-id="db3d5-132">Primeiro, defina uma seqüência de conexão no elemento> <. `connectionStrings`</span><span class="sxs-lookup"><span data-stu-id="db3d5-132">First, define a connection string in the <`connectionStrings`> element.</span></span>  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 <span data-ttu-id="db3d5-133">Em seguida, você deve ativar a `caching` dependência de cache `system.web` SQL dentro de um elemento <> dentro do elemento> <, conforme mostrado no exemplo de configuração a seguir.</span><span class="sxs-lookup"><span data-stu-id="db3d5-133">Then you must enable SQL cache dependency within a <`caching`> element within the <`system.web`> element as shown in the following config example.</span></span>  
  
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
  
 <span data-ttu-id="db3d5-134">Aqui, a dependência do cache SQL está ativada e um tempo de votação de 1000 milissegundos é definido.</span><span class="sxs-lookup"><span data-stu-id="db3d5-134">Here SQL cache dependency is enabled and a polling time of 1000 milliseconds is set.</span></span> <span data-ttu-id="db3d5-135">Cada vez que o tempo de votação é decorrido, a tabela do banco de dados é verificada para atualizações.</span><span class="sxs-lookup"><span data-stu-id="db3d5-135">Each time the polling time elapses the database table is checked for updates.</span></span> <span data-ttu-id="db3d5-136">Se for detectada a deserção, o conteúdo do cache será removido e, na próxima vez que a operação do serviço for invocada, uma nova resposta será armazenada em cache.</span><span class="sxs-lookup"><span data-stu-id="db3d5-136">If changes are detected the contents of the cache are removed and the next time the service operation is invoked a new response is cached.</span></span> <span data-ttu-id="db3d5-137">Dentro do `sqlCacheDependency` elemento <> adicionar as bases de `databases` dados e referenciar as strings de conexão dentro do elemento> <como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="db3d5-137">Within the <`sqlCacheDependency`> element add the databases and reference the connection strings within the <`databases`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="db3d5-138">Em seguida, você deve configurar as `caching` configurações de cache de saída dentro do elemento> <, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="db3d5-138">Next you must configure the output cache settings within the <`caching`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="db3d5-139">Aqui, a duração do cache `varyByParam` é definida como `sqlDependency` 60 segundos, não é definida como nenhuma e é definida como uma lista delimitada de nomes de banco de dados/pares de tabela separados por pontos.</span><span class="sxs-lookup"><span data-stu-id="db3d5-139">Here the cache duration is set to 60 seconds, `varyByParam` is set to none, and `sqlDependency` is set to a semicolon-delimited list of database name/table pairs separated by colons.</span></span> <span data-ttu-id="db3d5-140">Quando os `MyTable` dados são alterados, a resposta armazenada em cache para a operação do serviço é removida e, quando a operação é invocada, uma nova resposta é gerada (ligando para a operação do serviço), armazenada em cache e devolvida ao cliente.</span><span class="sxs-lookup"><span data-stu-id="db3d5-140">When data in `MyTable` is changed the cached response for the service operation is removed and when the operation is invoked a new response is generated (by calling the service operation), cached, and returned to the client.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="db3d5-141">Para ASP.NET acessar um banco de dados SQL, você deve usar a [ferramenta de registro de servidor sql ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="db3d5-141">For ASP.NET to access a SQL database, you must use the [ASP.NET SQL Server Registration Tool](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90)).</span></span> <span data-ttu-id="db3d5-142">Além disso, você deve permitir o acesso apropriado da conta de usuário ao banco de dados e à tabela.</span><span class="sxs-lookup"><span data-stu-id="db3d5-142">In addition you must allow the appropriate user account access to the database and table.</span></span> <span data-ttu-id="db3d5-143">Para obter mais informações, consulte [Acessando o SQL Server a partir de um aplicativo web](https://docs.microsoft.com/previous-versions/aspnet/ht43wsex(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="db3d5-143">For more information, see [Accessing SQL Server from a Web Application](https://docs.microsoft.com/previous-versions/aspnet/ht43wsex(v=vs.100)).</span></span>  
  
## <a name="conditional-http-get-based-caching"></a><span data-ttu-id="db3d5-144">Cache conditional HTTP GET baseado</span><span class="sxs-lookup"><span data-stu-id="db3d5-144">Conditional HTTP GET Based Caching</span></span>  

  <span data-ttu-id="db3d5-145">Em cenários Web HTTP, um HTTP GET condicional é frequentemente usado por serviços para implementar cache HTTP inteligente conforme descrito na [Especificação HTTP](https://www.w3.org/Protocols/rfc2616/rfc2616.html).</span><span class="sxs-lookup"><span data-stu-id="db3d5-145">In Web HTTP scenarios a conditional HTTP GET is often used by services to implement intelligent HTTP caching as described in the [HTTP Specification](https://www.w3.org/Protocols/rfc2616/rfc2616.html).</span></span> <span data-ttu-id="db3d5-146">Para isso, o serviço deve definir o valor do cabeçalho ETag na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="db3d5-146">To do this, the service must set the value of the ETag header in the HTTP response.</span></span> <span data-ttu-id="db3d5-147">Ele também deve verificar o cabeçalho If-None-Match na solicitação HTTP para ver se algum dos ETag especificados corresponde ao ETag atual.</span><span class="sxs-lookup"><span data-stu-id="db3d5-147">It also must check the If-None-Match header in the HTTP request to see whether any of the ETag specified matches the current ETag.</span></span>  
  
 <span data-ttu-id="db3d5-148">Para solicitações GET <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> e HEAD, pega um valor eTag e verifica-o no cabeçalho If-None-Match da solicitação.</span><span class="sxs-lookup"><span data-stu-id="db3d5-148">For GET and HEAD requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> takes an ETag value and checks it against the If-None-Match header of the request.</span></span> <span data-ttu-id="db3d5-149">Se o cabeçalho estiver presente <xref:System.ServiceModel.Web.WebFaultException> e houver uma correspondência, um com um código de status HTTP 304 (Não Modificado) será lançado e um cabeçalho ETag será adicionado à resposta com o ETag correspondente.</span><span class="sxs-lookup"><span data-stu-id="db3d5-149">If the header is present and there is a match, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown and an ETag header is added to the response with the matching ETag.</span></span>  
  
 <span data-ttu-id="db3d5-150">Uma sobrecarga <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> do método pega uma última data modificada e verifica-a com o cabeçalho If-Modified-Since da solicitação.</span><span class="sxs-lookup"><span data-stu-id="db3d5-150">One overload of the <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> method takes a last modified date and checks it against the If-Modified-Since header of the request.</span></span> <span data-ttu-id="db3d5-151">Se o cabeçalho estiver presente e o <xref:System.ServiceModel.Web.WebFaultException> recurso não tiver sido modificado desde então, um com um código de status HTTP 304 (Não Modificado) será lançado.</span><span class="sxs-lookup"><span data-stu-id="db3d5-151">If the header is present and the resource has not been modified since, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown.</span></span>  
  
 <span data-ttu-id="db3d5-152">Para solicitações PUT, POST <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> e DELETE, leva o valor atual do ETag de um recurso.</span><span class="sxs-lookup"><span data-stu-id="db3d5-152">For PUT, POST, and DELETE requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> takes the current ETag value of a resource.</span></span> <span data-ttu-id="db3d5-153">Se o valor atual do ETag for nulo, o método verificará se o cabeçalho If-None-Match tem um valor de "\*".</span><span class="sxs-lookup"><span data-stu-id="db3d5-153">If the current ETag value is null, the method checks that the If-None- Match header has a value of "\*".</span></span>  <span data-ttu-id="db3d5-154">Se o valor eTag atual não for um valor padrão, então o método verificará o valor atual do ETag em relação ao cabeçalho If-Match da solicitação.</span><span class="sxs-lookup"><span data-stu-id="db3d5-154">If the current ETag value is not a default value, then the method checks the current ETag value against the If- Match header of the request.</span></span> <span data-ttu-id="db3d5-155">Em ambos os casos, <xref:System.ServiceModel.Web.WebFaultException> o método lança um com um código de status HTTP 412 (Falha na pré-condição) se o cabeçalho esperado não estiver presente na solicitação ou seu valor não satisfaça a verificação condicional e define o cabeçalho ETag da resposta ao valor ETag atual.</span><span class="sxs-lookup"><span data-stu-id="db3d5-155">In either case, the method throws a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 412 (Precondition Failed) if the expected header is not present in the request or its value does not satisfy the conditional check and sets the ETag header of the response to the current ETag value.</span></span>  
  
 <span data-ttu-id="db3d5-156">Tanto `CheckConditional` os métodos <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> quanto o método garantem que o valor ETag definido no cabeçalho de resposta seja um ETag válido de acordo com a especificação HTTP.</span><span class="sxs-lookup"><span data-stu-id="db3d5-156">Both the `CheckConditional` methods and the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> method ensures that the ETag value set on the response header is a valid ETag according to the HTTP specification.</span></span> <span data-ttu-id="db3d5-157">Isso inclui cercar o valor do ETag em cotações duplas se eles ainda não estiverem presentes e escapar adequadamente de quaisquer caracteres internos de aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="db3d5-157">This includes surrounding the ETag value in double quotes if they are not already present and properly escaping any internal double quote characters.</span></span> <span data-ttu-id="db3d5-158">A comparação fraca do ETag não é suportada.</span><span class="sxs-lookup"><span data-stu-id="db3d5-158">Weak ETag comparison is not supported.</span></span>  
  
 <span data-ttu-id="db3d5-159">O exemplo a seguir mostra como usar esses métodos.</span><span class="sxs-lookup"><span data-stu-id="db3d5-159">The following example shows how to use these methods.</span></span>  
  
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
  
## <a name="security-considerations"></a><span data-ttu-id="db3d5-160">Considerações de segurança</span><span class="sxs-lookup"><span data-stu-id="db3d5-160">Security Considerations</span></span>  
 <span data-ttu-id="db3d5-161">As solicitações que requerem autorização não devem ter suas respostas armazenadas em cache, pois a autorização não é realizada quando a resposta é atendida a partir do cache.</span><span class="sxs-lookup"><span data-stu-id="db3d5-161">Requests that require authorization should not have their responses cached, because the authorization is not performed when the response is served from the cache.</span></span>  <span data-ttu-id="db3d5-162">Cache tais respostas introduziria uma séria vulnerabilidade de segurança.</span><span class="sxs-lookup"><span data-stu-id="db3d5-162">Caching such responses would introduce a serious security vulnerability.</span></span>  <span data-ttu-id="db3d5-163">Normalmente, solicitações que requerem autorização fornecem dados específicos do usuário e, portanto, o cache do lado do servidor nem sequer é benéfico.</span><span class="sxs-lookup"><span data-stu-id="db3d5-163">Usually, requests that require authorization provide user-specific data and therefore server-side caching is not even beneficial.</span></span>  <span data-ttu-id="db3d5-164">Em tais situações, o cache do lado do cliente ou simplesmente não cache em tudo será mais apropriado.</span><span class="sxs-lookup"><span data-stu-id="db3d5-164">In such situations, client-side caching or simply not caching at all will be more appropriate.</span></span>
