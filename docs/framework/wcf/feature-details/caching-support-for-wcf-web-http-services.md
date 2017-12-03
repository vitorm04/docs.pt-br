---
title: "Cache com suporte para serviços HTTP Web do WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a4dd96f444d6405022a0a812a55a92cec1052fbb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="caching-support-for-wcf-web-http-services"></a><span data-ttu-id="bbbe1-102">Cache com suporte para serviços HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="bbbe1-102">Caching Support for WCF Web HTTP Services</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="bbbe1-103">permite que você use o mecanismo de cache declarativo já disponível em ASP.NET em seus serviços WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-103"> enables you to use the declarative caching mechanism already available in ASP.NET in your WCF Web HTTP services.</span></span> <span data-ttu-id="bbbe1-104">Isso permite que você para respostas de cache de suas operações de serviço WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-104">This allows you to cache responses from your WCF Web HTTP service operations.</span></span> <span data-ttu-id="bbbe1-105">Quando um usuário envia um HTTP GET para o serviço que está configurado para armazenar em cache, ASP.NET envia a resposta armazenada em cache e o método de serviço não for chamado.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-105">When a user sends an HTTP GET to your service that is configured for caching, ASP.NET sends back the cached response and the service method is not called.</span></span> <span data-ttu-id="bbbe1-106">Quando o cache expira, na próxima vez que um usuário envia um HTTP GET é chamado o método de serviço e uma vez é armazenado em cache a resposta.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-106">When the cache expires, the next time a user sends an HTTP GET, your service method is called and the response is once again cached.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="bbbe1-107">ASP.NET armazenar em cache, consulte [visão geral de cache do ASP.NET](http://go.microsoft.com/fwlink/?LinkId=152534)</span><span class="sxs-lookup"><span data-stu-id="bbbe1-107"> ASP.NET caching, see [ASP.NET Caching Overview](http://go.microsoft.com/fwlink/?LinkId=152534)</span></span>  
  
## <a name="basic-web-http-service-caching"></a><span data-ttu-id="bbbe1-108">Cache de serviço do Web básico HTTP</span><span class="sxs-lookup"><span data-stu-id="bbbe1-108">Basic Web HTTP Service Caching</span></span>  
 <span data-ttu-id="bbbe1-109">Para habilitar o HTTP WEB do serviço de cache, você deve primeiro habilitar compatibilidade com ASP.NET aplicando o <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> à configuração de serviço <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> para <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> ou <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-109">To enable WEB HTTP service caching you must first enable ASP.NET compatibility by applying the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to the service setting <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> or <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span></span>  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]<span data-ttu-id="bbbe1-110">apresenta um novo atributo chamado <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> que permite que você especifique um nome de perfil de cache.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-110"> introduces a new attribute called <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> that allows you to specify a cache profile name.</span></span> <span data-ttu-id="bbbe1-111">Esse atributo é aplicado a uma operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-111">This attribute is applied to a service operation.</span></span> <span data-ttu-id="bbbe1-112">O exemplo a seguir se aplica a <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> a um serviço para habilitar a compatibilidade com ASP.NET e configura o `GetCustomer` operação para armazenar em cache.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-112">The following example applies the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to a service to enable ASP.NET compatibility and configures the `GetCustomer` operation for caching.</span></span> <span data-ttu-id="bbbe1-113">O <!--zz<xref:System.ServiceModel.Activation.AspNetCacheProfileAttribute>--> `System.ServiceModel.Activation.AspNetCacheProfileAttribute` atributo especifica um perfil de cache que contém as configurações de cache a ser usado.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-113">The <!--zz<xref:System.ServiceModel.Activation.AspNetCacheProfileAttribute>--> `System.ServiceModel.Activation.AspNetCacheProfileAttribute` attribute specifies a cache profile that contains the cache settings to be used.</span></span>  
  
```csharp
[ServiceContract] AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]
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
  
 <span data-ttu-id="bbbe1-114">Você também deve ativar o modo de compatibilidade ASP.NET no arquivo Web. config, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-114">You must also turn on ASP.NET compatibility mode in the Web.config file as shown in the following example.</span></span>  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
>  <span data-ttu-id="bbbe1-115">Se o modo de compatibilidade ASP.NET não está ativado e o <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> é usada uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-115">If ASP.NET compatibility mode is not turned on and the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is used an exception is thrown.</span></span>  
  
 <span data-ttu-id="bbbe1-116">O nome do perfil de cache especificado pelo <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifica um perfil de cache que é adicionado ao seu arquivo de configuração Web. config.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-116">The cache profile name specified by the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifies a cache profile that is added to your Web.config configuration file.</span></span> <span data-ttu-id="bbbe1-117">O perfil de cache é definido com em um <`outputCacheSetting`> elemento conforme mostrado no exemplo de configuração a seguir.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-117">The cache profile is defined with in a <`outputCacheSetting`> element as shown in the following configuration example.</span></span>  
  
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
  
 <span data-ttu-id="bbbe1-118">Este é o mesmo elemento de configuração que está disponível para aplicativos ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-118">This is the same configuration element that is available to ASP.NET applications.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="bbbe1-119">Perfis de cache do ASP.NET, consulte <xref:System.Web.Configuration.OutputCacheProfile>.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-119"> ASP.NET cache profiles, see <xref:System.Web.Configuration.OutputCacheProfile>.</span></span> <span data-ttu-id="bbbe1-120">Para serviços da Web HTTP, os atributos mais importantes no perfil de cache são: `cacheDuration` e `varyByParam`.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-120">For Web HTTP services, the most important attributes in the cache profile are: `cacheDuration` and `varyByParam`.</span></span> <span data-ttu-id="bbbe1-121">Ambos os atributos são necessários.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-121">Both of these attributes are required.</span></span> <span data-ttu-id="bbbe1-122">`cacheDuration`Define a quantidade de tempo que uma resposta deve ser armazenada em cache em segundos.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-122">`cacheDuration` sets the amount of time a response should be cached in seconds.</span></span> <span data-ttu-id="bbbe1-123">`varyByParam`permite que você especifique um parâmetro de cadeia de caracteres de consulta que é usada para respostas de cache.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-123">`varyByParam` allows you to specify a query string parameter that is used to cache responses.</span></span> <span data-ttu-id="bbbe1-124">Todas as solicitações feitas com valores de parâmetro de cadeia de caracteres de consulta diferentes são armazenadas em cache separadamente.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-124">All requests made with different query string parameter values are cached separately.</span></span> <span data-ttu-id="bbbe1-125">Por exemplo, depois que uma solicitação inicial é feita para http://MyServer/MyHttpService/MyOperation?param=10 todas as solicitações subsequentes feitas com o mesmo URI deve ser retornadas a resposta armazenada em cache (desde que a duração do cache não tiver decorrido).</span><span class="sxs-lookup"><span data-stu-id="bbbe1-125">For example, once an initial request is made to http://MyServer/MyHttpService/MyOperation?param=10 all subsequent requests made with the same URI would be returned the cached response (so long as the cache duration has not elapsed).</span></span> <span data-ttu-id="bbbe1-126">As respostas para uma solicitação semelhante que é o mesmo, mas tem um valor diferente para o parâmetro de cadeia de caracteres de consulta de parâmetro são armazenadas separadamente.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-126">Responses for a similar request that is the same but has a different value for the parameter query string parameter are cached separately.</span></span> <span data-ttu-id="bbbe1-127">Se você não quiser que esse comportamento de cache separado, defina `varyByParam` para "none".</span><span class="sxs-lookup"><span data-stu-id="bbbe1-127">If you do not want this separate caching behavior, set `varyByParam` to "none".</span></span>  
  
## <a name="sql-cache-dependency"></a><span data-ttu-id="bbbe1-128">Dependência de Cache do SQL</span><span class="sxs-lookup"><span data-stu-id="bbbe1-128">SQL Cache Dependency</span></span>  
 <span data-ttu-id="bbbe1-129">Respostas de serviço da Web HTTP podem também ser armazenados em cache com uma dependência de cache SQL.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-129">Web HTTP service responses can also be cached with a SQL cache dependency.</span></span> <span data-ttu-id="bbbe1-130">Se seu serviço WCF Web HTTP depende de dados armazenados em um banco de dados SQL, convém resposta do serviço de cache e invalidar a resposta em cache quando as alterações da tabela de banco de dados de dados no SQL.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-130">If your WCF Web HTTP service depends on data stored in a SQL database, you may want to cache the service's response and invalidate the cached response when data in the SQL database table changes.</span></span> <span data-ttu-id="bbbe1-131">Esse comportamento é totalmente configurado no arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-131">This behavior is configured completely within the Web.config file.</span></span> <span data-ttu-id="bbbe1-132">Você deve primeiro definir uma cadeia de caracteres de conexão no <`connectionStrings`> elemento.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-132">You must first define a connection string in the <`connectionStrings`> element.</span></span>  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 <span data-ttu-id="bbbe1-133">Em seguida, você deve habilitar a dependência de cache SQL dentro de um <`caching`> elemento dentro a <`system.web`> elemento conforme mostrado no exemplo de configuração a seguir.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-133">Then you must enable SQL cache dependency within a <`caching`> element within the <`system.web`> element as shown in the following config example.</span></span>  
  
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
  
 <span data-ttu-id="bbbe1-134">Aqui a dependência de cache SQL está habilitada e uma hora de sondagem de 1000 milissegundos é definida.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-134">Here SQL cache dependency is enabled and a polling time of 1000 milliseconds is set.</span></span> <span data-ttu-id="bbbe1-135">Cada vez que o tempo de pesquisa decorrido a tabela de banco de dados é verificado para atualizações.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-135">Each time the polling time elapses the database table is checked for updates.</span></span> <span data-ttu-id="bbbe1-136">Se forem detectadas alterações, o conteúdo do cache é removido e na próxima vez em que a operação de serviço é invocado uma nova resposta é armazenado em cache.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-136">If changes are detected the contents of the cache are removed and the next time the service operation is invoked a new response is cached.</span></span> <span data-ttu-id="bbbe1-137">Dentro de <`sqlCacheDependency`> elemento adicionar os bancos de dados e fazer referência as cadeias de caracteres de conexão dentro de <`databases`> elemento conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-137">Within the <`sqlCacheDependency`> element add the databases and reference the connection strings within the <`databases`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="bbbe1-138">Em seguida, você deve configurar as definições de cache de saída dentro de <`caching`> elemento conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-138">Next you must configure the output cache settings within the <`caching`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="bbbe1-139">Aqui a duração do cache é definida como 60 segundos, `varyByParam` está definida como none e `sqlDependency` é definido como uma lista delimitada por ponto e vírgula de pares de nome/tabela de banco de dados separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-139">Here the cache duration is set to 60 seconds, `varyByParam` is set to none and `sqlDependency` is set to a semicolon delimited list of database name/table pairs separated by colons.</span></span> <span data-ttu-id="bbbe1-140">Quando dados em `MyTable` é alterado a resposta armazenada em cache para a operação de serviço é removida e quando a operação é chamada uma nova resposta é gerada (chamando a operação de serviço), armazenados em cache e retornada ao cliente.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-140">When data in `MyTable` is changed the cached response for the service operation is removed and when the operation is invoked a new response is generated (by calling the service operation), cached, and returned to the client.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bbbe1-141">Para o ASP.NET acessar um banco de dados SQL, você deve usar o [ferramenta de registro do ASP.NET SQL Server](http://go.microsoft.com/fwlink/?LinkId=152536).</span><span class="sxs-lookup"><span data-stu-id="bbbe1-141">For ASP.NET to access a SQL database, you must use the [ASP.NET SQL Server Registration Tool](http://go.microsoft.com/fwlink/?LinkId=152536).</span></span> <span data-ttu-id="bbbe1-142">Além disso, você deve permitir o acesso de conta de usuário apropriado para o banco de dados e a tabela.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-142">In addition you must allow the appropriate user account access to the database and table.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="bbbe1-143">[Acessar o SQL Server de um aplicativo Web](http://go.microsoft.com/fwlink/?LinkId=178988).</span><span class="sxs-lookup"><span data-stu-id="bbbe1-143"> [Accessing SQL Server from a Web Application](http://go.microsoft.com/fwlink/?LinkId=178988).</span></span>  
  
## <a name="conditional-http-get-based-caching"></a><span data-ttu-id="bbbe1-144">HTTP condicional obter com base em cache</span><span class="sxs-lookup"><span data-stu-id="bbbe1-144">Conditional HTTP GET Based Caching</span></span>  
 <span data-ttu-id="bbbe1-145">Em cenários de Web HTTP um HTTP GET condicional é geralmente usado pelos serviços para implementar cache inteligente de HTTP conforme descrito no [especificação HTTP](http://go.microsoft.com/fwlink/?LinkId=165800).</span><span class="sxs-lookup"><span data-stu-id="bbbe1-145">In Web HTTP scenarios a conditional HTTP GET is often used by services to implement intelligent HTTP caching as described in the [HTTP Specification](http://go.microsoft.com/fwlink/?LinkId=165800).</span></span> <span data-ttu-id="bbbe1-146">Para fazer isso o serviço deve definir o valor de cabeçalho ETag na resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-146">To do this the service must set the value of the ETag header in the HTTP response.</span></span> <span data-ttu-id="bbbe1-147">Ele também deve verificar o cabeçalho If-None-Match na solicitação HTTP para ver se qualquer uma da ETag especificado corresponde o ETag atual.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-147">It also must check the If-None-Match header in the HTTP request to see whether any of the ETag specified matches the current ETag.</span></span>  
  
 <span data-ttu-id="bbbe1-148">Para solicitações GET e HEAD, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> tem um valor de ETag e a compara com o cabeçalho If-None-Match da solicitação.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-148">For GET and HEAD requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> takes an ETag value and checks it against the If-None-Match header of the request.</span></span> <span data-ttu-id="bbbe1-149">Se o cabeçalho estiver presente e houver uma correspondência, um <xref:System.ServiceModel.Web.WebFaultException> com um HTTP 304 (não modificado) do código de status é gerado e um cabeçalho ETag é adicionado à resposta com o ETag correspondente.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-149">If the header is present and there is a match, a <xref:System.ServiceModel.Web.WebFaultException> with a HTTP status code 304 (Not Modified) is thrown and an ETag header is added to the response with the matching ETag.</span></span>  
  
 <span data-ttu-id="bbbe1-150">Uma sobrecarga do <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> método leva a uma data da última modificação e a compara com o cabeçalho If-Modified-Since da solicitação.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-150">One overload of the <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> method takes a last modified date and checks it against the If-Modified-Since header of the request.</span></span> <span data-ttu-id="bbbe1-151">Se o cabeçalho estiver presente e o recurso não tiver sido modificado desde, um <xref:System.ServiceModel.Web.WebFaultException> com um HTTP 304 (não modificado) do código de status é gerado.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-151">If the header is present and the resource has not been modified since, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown.</span></span>  
  
 <span data-ttu-id="bbbe1-152">Para solicitações PUT, POST e DELETE, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> usa o valor de ETag atual de um recurso.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-152">For PUT, POST, and DELETE requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> takes the current ETag value of a resource.</span></span> <span data-ttu-id="bbbe1-153">Se o valor atual de ETag for nulo, o método verifica se o cabeçalho If-None-Match tem um valor de "*".</span><span class="sxs-lookup"><span data-stu-id="bbbe1-153">If the current ETag value is null, the method checks that the If-None- Match header has a value of "*".</span></span>  <span data-ttu-id="bbbe1-154">Se o valor de ETag atual não é um valor padrão, o método verifica o valor de ETag atual contra o cabeçalho If - Match da solicitação.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-154">If the current ETag value is not a default value, then the method checks the current ETag value against the If- Match header of the request.</span></span> <span data-ttu-id="bbbe1-155">Em ambos os casos, o método gera uma <xref:System.ServiceModel.Web.WebFaultException> com um status HTTP código 412 (Falha na pré-condição) se o cabeçalho esperado não está presente na solicitação ou seu valor não satisfaz a verificação condicional e define o cabeçalho ETag da resposta para o ETag atual valor.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-155">In either case, the method throws a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 412 (Precondition Failed) if the expected header is not present in the request or its value does not satisfy the conditional check and sets the ETag header of the response to the current ETag value.</span></span>  
  
 <span data-ttu-id="bbbe1-156">Ambos os `CheckConditional` métodos e <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> método garante que o valor de ETag definido no cabeçalho de resposta é um ETag válido de acordo com a especificação de HTTP.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-156">Both the `CheckConditional` methods and the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> method ensures that the ETag value set on the response header is a valid ETag according to the HTTP specification.</span></span> <span data-ttu-id="bbbe1-157">Isso inclui ao redor do valor de ETag entre aspas duplas se eles não ainda estão presentes e corretamente ignorar nenhum caractere de aspas duplas interno.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-157">This includes surrounding the ETag value in double quotes if they are not already present and properly escaping any internal double quote characters.</span></span> <span data-ttu-id="bbbe1-158">Não há suporte para a comparação de ETag fraca.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-158">Weak ETag comparison is not supported.</span></span>  
  
 <span data-ttu-id="bbbe1-159">O exemplo a seguir mostra como usar esses métodos.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-159">The following example shows how to use these methods.</span></span>  
  
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
  
## <a name="security-considerations"></a><span data-ttu-id="bbbe1-160">Considerações sobre segurança</span><span class="sxs-lookup"><span data-stu-id="bbbe1-160">Security Considerations</span></span>  
 <span data-ttu-id="bbbe1-161">Solicitações que exigem autorização não devem ter suas respostas em cache, pois a autorização não é executada quando a resposta é servida do cache.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-161">Requests that require authorization should not have their responses cached, because the authorization is not performed when the response is served from the cache.</span></span>  <span data-ttu-id="bbbe1-162">Essas respostas em cache geraria uma vulnerabilidade de segurança sério.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-162">Caching such responses would introduce a serious security vulnerability.</span></span>  <span data-ttu-id="bbbe1-163">Geralmente, solicitações que exigem autorização fornecem dados específicos do usuário e, portanto, o cache do lado do servidor não é benéfico mesmo.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-163">Usually, requests that require authorization provide user-specific data and therefore server-side caching is not even beneficial.</span></span>  <span data-ttu-id="bbbe1-164">Em tais situações, o cache do cliente ou simplesmente não cache em todos os será mais adequado.</span><span class="sxs-lookup"><span data-stu-id="bbbe1-164">In such situations, client-side caching or simply not caching at all will be more appropriate.</span></span>
