---
title: Como migrar serviços habilitados para AJAX ASP.NET para o WCF
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 60e3088b9075464176c328af1f52676a69c4990f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976139"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a><span data-ttu-id="5561c-102">Como migrar serviços habilitados para AJAX ASP.NET para o WCF</span><span class="sxs-lookup"><span data-stu-id="5561c-102">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>
<span data-ttu-id="5561c-103">Este tópico descreve os procedimentos para migrar um serviço AJAX ASP.NET básico para um serviço equivalente habilitado para AJAX (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="5561c-103">This topic outlines procedures to migrate a basic ASP.NET AJAX service to an equivalent AJAX-enabled Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="5561c-104">Ele mostra como criar uma versão WCF equivalente funcional de um serviço ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="5561c-104">It shows how to create a functionally equivalent WCF version of an ASP.NET AJAX service.</span></span> <span data-ttu-id="5561c-105">Os dois serviços podem ser usados lado a lado, ou o serviço WCF pode ser usado para substituir o serviço ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="5561c-105">The two services can then be used side by side, or the WCF service can be used to replace the ASP.NET AJAX service.</span></span>

 <span data-ttu-id="5561c-106">A migração de um serviço ASP.NET AJAX existente para um serviço WCF AJAX oferece os seguintes benefícios:</span><span class="sxs-lookup"><span data-stu-id="5561c-106">Migrating an existing ASP.NET AJAX service to a WCF AJAX service gives you the following benefits:</span></span>

- <span data-ttu-id="5561c-107">Você pode expor seu serviço AJAX como um serviço SOAP com configuração extra mínima.</span><span class="sxs-lookup"><span data-stu-id="5561c-107">You can expose your AJAX service as a SOAP service with minimal extra configuration.</span></span>

- <span data-ttu-id="5561c-108">Você pode se beneficiar de recursos do WCF, como rastreamento e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="5561c-108">You can benefit from WCF features such as tracing, and so on.</span></span>

 <span data-ttu-id="5561c-109">Os procedimentos a seguir pressupõem que você esteja usando o Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="5561c-109">The following procedures assume that you are using Visual Studio 2012.</span></span>

 <span data-ttu-id="5561c-110">O código que resulta dos procedimentos descritos neste tópico é fornecido no exemplo após os procedimentos.</span><span class="sxs-lookup"><span data-stu-id="5561c-110">The code that results from the procedures outlined in this topic is provided in the example following the procedures.</span></span>

 <span data-ttu-id="5561c-111">Para obter mais informações sobre como expor um serviço WCF por meio de um ponto de extremidade habilitado para AJAX, consulte o tópico [como: usar a configuração para adicionar um ponto de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) .</span><span class="sxs-lookup"><span data-stu-id="5561c-111">For more information about exposing a WCF service through an AJAX-enabled endpoint, see the [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) topic.</span></span>

### <a name="to-create-and-test-the-aspnet-web-service-application"></a><span data-ttu-id="5561c-112">Para criar e testar o aplicativo de serviço Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5561c-112">To create and test the ASP.NET Web service application</span></span>

1. <span data-ttu-id="5561c-113">Abra o Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="5561c-113">Open Visual Studio 2012.</span></span>

2. <span data-ttu-id="5561c-114">No menu **arquivo** , selecione **novo**, **projeto**, **Web**e, em seguida, selecione **aplicativo de serviço Web ASP.net**.</span><span class="sxs-lookup"><span data-stu-id="5561c-114">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Service Application**.</span></span>

3. <span data-ttu-id="5561c-115">Nomeie o projeto `ASPHello` e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="5561c-115">Name the project `ASPHello` and click **OK**.</span></span>

4. <span data-ttu-id="5561c-116">Remova a marca de comentário da linha no arquivo Service1.asmx.cs que contém `System.Web.Script.Services.ScriptService]` para habilitar o AJAX para este serviço.</span><span class="sxs-lookup"><span data-stu-id="5561c-116">Uncomment the line in the Service1.asmx.cs file that contains `System.Web.Script.Services.ScriptService]` to enable AJAX for this service.</span></span>

5. <span data-ttu-id="5561c-117">No menu **Compilar** , selecione **Compilar solução**.</span><span class="sxs-lookup"><span data-stu-id="5561c-117">From the **Build** menu, select **Build Solution**.</span></span>

6. <span data-ttu-id="5561c-118">No menu **Depurar**, selecione **Iniciar sem Depurar**.</span><span class="sxs-lookup"><span data-stu-id="5561c-118">From the **Debug** menu, select **Start Without Debugging**.</span></span>

7. <span data-ttu-id="5561c-119">Na página da Web gerada, selecione a operação de `HelloWorld`.</span><span class="sxs-lookup"><span data-stu-id="5561c-119">On the Web page generated, select the `HelloWorld` operation.</span></span>

8. <span data-ttu-id="5561c-120">Clique no botão **invocar** na página `HelloWorld` teste.</span><span class="sxs-lookup"><span data-stu-id="5561c-120">Click the **Invoke** button on the `HelloWorld` test page.</span></span> <span data-ttu-id="5561c-121">Você deve receber a resposta XML a seguir.</span><span class="sxs-lookup"><span data-stu-id="5561c-121">You should receive the following XML response.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. <span data-ttu-id="5561c-122">Essa resposta confirma que agora você tem um serviço ASP.NET AJAX em funcionamento e, em particular, que o serviço agora expôs um ponto de extremidade em Service1. asmx/HelloWorld que responde às solicitações HTTP POST e retorna XML.</span><span class="sxs-lookup"><span data-stu-id="5561c-122">This response confirms that you now have a functioning ASP.NET AJAX service and, in particular, that the service has now exposed an endpoint at Service1.asmx/HelloWorld that responds to HTTP POST requests and returns XML.</span></span>

     <span data-ttu-id="5561c-123">Agora você está pronto para converter este serviço para usar um serviço WCF AJAX.</span><span class="sxs-lookup"><span data-stu-id="5561c-123">Now you are ready to convert this service to use a WCF AJAX service.</span></span>

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a><span data-ttu-id="5561c-124">Para criar um aplicativo de serviço WCF AJAX equivalente</span><span class="sxs-lookup"><span data-stu-id="5561c-124">To create an equivalent WCF AJAX service application</span></span>

1. <span data-ttu-id="5561c-125">Clique com o botão direito do mouse no projeto **ASPHello** e selecione **Adicionar**, **novo item**e, em seguida, **serviço WCF habilitado para AJAX**.</span><span class="sxs-lookup"><span data-stu-id="5561c-125">Right-click the **ASPHello** project and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>

2. <span data-ttu-id="5561c-126">Nomeie o serviço `WCFHello` e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="5561c-126">Name the service `WCFHello` and click **Add**.</span></span>

3. <span data-ttu-id="5561c-127">Abra o arquivo WCFHello.svc.cs.</span><span class="sxs-lookup"><span data-stu-id="5561c-127">Open the WCFHello.svc.cs file.</span></span>

4. <span data-ttu-id="5561c-128">Em Service1.asmx.cs, copie a seguinte implementação da operação `HelloWorld`.</span><span class="sxs-lookup"><span data-stu-id="5561c-128">From Service1.asmx.cs, copy the following implementation of the `HelloWorld` operation.</span></span>

    ```csharp
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

5. <span data-ttu-id="5561c-129">Cole na implementação copiada da operação de `HelloWorld` no arquivo WCFHello.svc.cs no lugar do código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5561c-129">Paste to copied implementation of the `HelloWorld` operation into the WCFHello.svc.cs file in place of the following code.</span></span>

    ```csharp
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6. <span data-ttu-id="5561c-130">Especifique o atributo `Namespace` para <xref:System.ServiceModel.ServiceContractAttribute> como `WCFHello`.</span><span class="sxs-lookup"><span data-stu-id="5561c-130">Specify the `Namespace` attribute for <xref:System.ServiceModel.ServiceContractAttribute> as `WCFHello`.</span></span>

    ```csharp
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7. <span data-ttu-id="5561c-131">Adicione o <xref:System.ServiceModel.Web.WebInvokeAttribute> à operação `HelloWorld` e defina a propriedade <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> para retornar <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span><span class="sxs-lookup"><span data-stu-id="5561c-131">Add the <xref:System.ServiceModel.Web.WebInvokeAttribute> to the `HelloWorld` operation and set the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> property to return <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span></span> <span data-ttu-id="5561c-132">Observe que, se não estiver definido, o tipo de retorno padrão será <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="5561c-132">Note that, if not set, the default return type is <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span>

    ```csharp
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8. <span data-ttu-id="5561c-133">No menu **Compilar** , selecione **Compilar solução**.</span><span class="sxs-lookup"><span data-stu-id="5561c-133">From the **Build** menu, select **Build Solution**.</span></span>

9. <span data-ttu-id="5561c-134">Abra o arquivo WCFHello. svc e, no menu **depurar** , selecione **Iniciar sem depuração**.</span><span class="sxs-lookup"><span data-stu-id="5561c-134">Open the WCFHello.svc file and from the **Debug** menu, select **Start Without Debugging**.</span></span>

10. <span data-ttu-id="5561c-135">O serviço agora expõe um ponto de extremidade em `WCFHello.svc/HelloWorld`, que responde às solicitações HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="5561c-135">The service now exposes an endpoint at `WCFHello.svc/HelloWorld`, which responds to HTTP POST requests.</span></span> <span data-ttu-id="5561c-136">As solicitações HTTP POST não podem ser testadas no navegador, mas o ponto de extremidade retorna XML após XML.</span><span class="sxs-lookup"><span data-stu-id="5561c-136">HTTP POST requests cannot be tested from the browser, but the endpoint returns XML following XML.</span></span>

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. <span data-ttu-id="5561c-137">O `WCFHello.svc/HelloWorld` e os pontos de extremidade de `Service1.aspx/HelloWorld` agora são funcionalmente equivalentes.</span><span class="sxs-lookup"><span data-stu-id="5561c-137">The `WCFHello.svc/HelloWorld` and the `Service1.aspx/HelloWorld` endpoints are now functionally equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="5561c-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5561c-138">Example</span></span>
 <span data-ttu-id="5561c-139">O código que resulta dos procedimentos descritos neste tópico é fornecido no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5561c-139">The code that results from the procedures outlined in this topic is provided in the following example.</span></span>

```csharp
//This is the ASP.NET code in the Service1.asmx.cs file.

using System;
using System.Collections;
using System.ComponentModel;
using System.Data;
using System.Linq;
using System.Web;
using System.Web.Services;
using System.Web.Services.Protocols;
using System.Xml.Linq;
using System.Web.Script.Services;

namespace ASPHello
{
    /// <summary>
    /// Summary description for Service1.
    /// </summary>
    [WebService(Namespace = "http://tempuri.org/")]
    [WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]
    [ToolboxItem(false)]
    // To allow this Web Service to be called from script, using ASP.NET AJAX, uncomment the following line.
    [System.Web.Script.Services.ScriptService]
    public class Service1 : System.Web.Services.WebService
    {

        [WebMethod]
        public string HelloWorld()
        {
            return "Hello World";
        }
    }
}

//This is the WCF code in the WCFHello.svc.cs file.
using System;
using System.Linq;
using System.Runtime.Serialization;
using System.ServiceModel;
using System.ServiceModel.Activation;
using System.ServiceModel.Web;

namespace ASPHello
{
    [ServiceContract(Namespace = "WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class WCFHello
    {
        // Add [WebInvoke] attribute to use HTTP GET.
        [OperationContract]
        [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
        public string HelloWorld()
        {
            return "Hello World";
        }

        // Add more operations here and mark them with [OperationContract].
    }
}
```

 <span data-ttu-id="5561c-140">O <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> não dá suporte ao tipo de <xref:System.Xml.XmlDocument> porque ele não é serializável pelo <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5561c-140">The <xref:System.Xml.XmlDocument> type is not supported by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because it is not serializable by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="5561c-141">Você pode usar um tipo de <xref:System.Xml.Linq.XDocument> ou serializar o <xref:System.Xml.XmlDocument.DocumentElement%2A> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="5561c-141">You can use either an <xref:System.Xml.Linq.XDocument> type, or serialize the <xref:System.Xml.XmlDocument.DocumentElement%2A> instead.</span></span>

 <span data-ttu-id="5561c-142">Se os serviços Web ASMX estiverem sendo atualizados e migrados lado a lado para os serviços WCF, evite mapear dois tipos para o mesmo nome no cliente.</span><span class="sxs-lookup"><span data-stu-id="5561c-142">If ASMX Web services are being upgraded and migrated side-by-side to WCF services, avoid mapping two types to the same name on the client.</span></span> <span data-ttu-id="5561c-143">Isso causará uma exceção em serializadores se o mesmo tipo for usado em um <xref:System.Web.Services.WebMethodAttribute> e um <xref:System.ServiceModel.ServiceContractAttribute>:</span><span class="sxs-lookup"><span data-stu-id="5561c-143">This causes an exception in serializers if the same type is used in a <xref:System.Web.Services.WebMethodAttribute> and a <xref:System.ServiceModel.ServiceContractAttribute>:</span></span>

- <span data-ttu-id="5561c-144">Se o serviço WCF for adicionado primeiro, invocar o método no serviço Web ASMX causará exceção em <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> porque a definição de estilo WCF da ordem no proxy tem precedência.</span><span class="sxs-lookup"><span data-stu-id="5561c-144">If WCF service is added first, invoking the method on ASMX Web Service causes exception in <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> because the WCF style definition of the order in the proxy takes precedence.</span></span>

- <span data-ttu-id="5561c-145">Se o serviço Web ASMX for adicionado primeiro, invocar o método no serviço WCF causará exceção em <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> porque a definição de estilo do serviço Web da ordem no proxy tem precedência.</span><span class="sxs-lookup"><span data-stu-id="5561c-145">If ASMX Web Service is added first, invoking method on WCF service causes exception in <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because the Web Service style definition of the order in the proxy takes precedence.</span></span>

 <span data-ttu-id="5561c-146">Há diferenças significativas no comportamento entre o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> e o <xref:System.Web.Script.Serialization.JavaScriptSerializer>AJAX ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="5561c-146">There are significant differences in behavior between the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> and the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span></span> <span data-ttu-id="5561c-147">Por exemplo, o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> representa um dicionário como uma matriz de pares chave/valor, enquanto o ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> representa um dicionário como objetos JSON reais.</span><span class="sxs-lookup"><span data-stu-id="5561c-147">For example, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> represents a dictionary as an array of key/value pairs, whereas the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> represents a dictionary as actual JSON objects.</span></span> <span data-ttu-id="5561c-148">O seguinte é o dicionário representado no AJAX ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="5561c-148">So the following is the dictionary represented in ASP.NET AJAX.</span></span>

```csharp
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 <span data-ttu-id="5561c-149">Esse dicionário é representado em objetos JSON, conforme mostrado na lista a seguir:</span><span class="sxs-lookup"><span data-stu-id="5561c-149">This dictionary is represented in JSON objects as shown in the following list:</span></span>

- <span data-ttu-id="5561c-150">[{"Chave": "um", "valor": 1}, {"chave": "dois", "valor": 2}] pelo <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span><span class="sxs-lookup"><span data-stu-id="5561c-150">[{"Key":"one","Value":1},{"Key":"two","Value":2}] by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span></span>

- <span data-ttu-id="5561c-151">{"One": 1, "Two": 2} pelo AJAX ASP.NET <xref:System.Web.Script.Serialization.JavaScriptSerializer></span><span class="sxs-lookup"><span data-stu-id="5561c-151">{"one":1,"two":2} by the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span></span>

 <span data-ttu-id="5561c-152">O <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> é mais poderoso no sentido de que ele pode manipular dicionários em que o tipo de chave não é uma cadeia de caracteres, enquanto o <xref:System.Web.Script.Serialization.JavaScriptSerializer> não pode.</span><span class="sxs-lookup"><span data-stu-id="5561c-152">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is more powerful in the sense that it can handle dictionaries where the key type is not string, while the <xref:System.Web.Script.Serialization.JavaScriptSerializer> cannot.</span></span> <span data-ttu-id="5561c-153">Mas o último é mais amigável para JSON.</span><span class="sxs-lookup"><span data-stu-id="5561c-153">But the latter is more JSON-friendly.</span></span>

 <span data-ttu-id="5561c-154">As diferenças significativas entre esses serializadores são resumidas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="5561c-154">The significant differences between these serializers are summarized in the following table.</span></span>

|<span data-ttu-id="5561c-155">Categoria de diferenças</span><span class="sxs-lookup"><span data-stu-id="5561c-155">Category of Differences</span></span>|<span data-ttu-id="5561c-156">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="5561c-156">DataContractJsonSerializer</span></span>|<span data-ttu-id="5561c-157">ASP.NET AJAX JavaScriptSerializer</span><span class="sxs-lookup"><span data-stu-id="5561c-157">ASP.NET AJAX JavaScriptSerializer</span></span>|
|-----------------------------|--------------------------------|---------------------------------------|
|<span data-ttu-id="5561c-158">Desserializar o buffer vazio (novo byte [0]) em <xref:System.Object> (ou <xref:System.Uri>ou em algumas outras classes).</span><span class="sxs-lookup"><span data-stu-id="5561c-158">Deserializing the empty buffer (new byte[0]) into <xref:System.Object> (or <xref:System.Uri>, or some other classes).</span></span>|<span data-ttu-id="5561c-159">SerializationException</span><span class="sxs-lookup"><span data-stu-id="5561c-159">SerializationException</span></span>|<span data-ttu-id="5561c-160">nulo</span><span class="sxs-lookup"><span data-stu-id="5561c-160">null</span></span>|
|<span data-ttu-id="5561c-161">Serialização de <xref:System.DBNull.Value></span><span class="sxs-lookup"><span data-stu-id="5561c-161">Serialization of <xref:System.DBNull.Value></span></span>|<span data-ttu-id="5561c-162">{} (ou {"__type": "#System"})</span><span class="sxs-lookup"><span data-stu-id="5561c-162">{} (or {"__type":"#System"})</span></span>|<span data-ttu-id="5561c-163">Nulo</span><span class="sxs-lookup"><span data-stu-id="5561c-163">Null</span></span>|
|<span data-ttu-id="5561c-164">Serialização dos membros privados de tipos de [Serializable].</span><span class="sxs-lookup"><span data-stu-id="5561c-164">Serialization of the private members of [Serializable] types.</span></span>|<span data-ttu-id="5561c-165">serializado</span><span class="sxs-lookup"><span data-stu-id="5561c-165">serialized</span></span>|<span data-ttu-id="5561c-166">não serializado</span><span class="sxs-lookup"><span data-stu-id="5561c-166">not serialized</span></span>|
|<span data-ttu-id="5561c-167">Serialização das propriedades públicas de tipos de <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="5561c-167">Serialization of the public properties of <xref:System.Runtime.Serialization.ISerializable> types.</span></span>|<span data-ttu-id="5561c-168">não serializado</span><span class="sxs-lookup"><span data-stu-id="5561c-168">not serialized</span></span>|<span data-ttu-id="5561c-169">serializado</span><span class="sxs-lookup"><span data-stu-id="5561c-169">serialized</span></span>|
|<span data-ttu-id="5561c-170">"Extensões" de JSON</span><span class="sxs-lookup"><span data-stu-id="5561c-170">"Extensions" of JSON</span></span>|<span data-ttu-id="5561c-171">Segue a especificação JSON, que requer aspas em nomes de membros de objetos ({"a": "Olá"}).</span><span class="sxs-lookup"><span data-stu-id="5561c-171">Adheres to the JSON specification, which requires quotes on object member names ({"a":"hello"}).</span></span>|<span data-ttu-id="5561c-172">Dá suporte aos nomes de membros de objeto sem aspas ({a: "Olá"}).</span><span class="sxs-lookup"><span data-stu-id="5561c-172">Supports the names of object members without quotes ({a:"hello"}).</span></span>|
|<span data-ttu-id="5561c-173">Tempo universal coordenado <xref:System.DateTime> (UTC)</span><span class="sxs-lookup"><span data-stu-id="5561c-173"><xref:System.DateTime> Coordinated Universal Time (UTC)</span></span>|<span data-ttu-id="5561c-174">Não dá suporte ao formato "\\/Date (123456789U)\\/" ou "\\/Date\\(\d + (&#124;U (\\+\\-[\d{4}]))?\\)\\\\/) ".</span><span class="sxs-lookup"><span data-stu-id="5561c-174">Does not support format "\\/Date(123456789U)\\/" or "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)".</span></span>|<span data-ttu-id="5561c-175">Dá suporte ao formato "\\/Date (123456789U)\\/" e "\\/Date\\(\d +&#124;(U (\\+\\-[\d{4}]))?\\)\\\\/) "como valores de DateTime.</span><span class="sxs-lookup"><span data-stu-id="5561c-175">Supports format "\\/Date(123456789U)\\/" and "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)" as DateTime values.</span></span>|
|<span data-ttu-id="5561c-176">Representação de dicionários</span><span class="sxs-lookup"><span data-stu-id="5561c-176">Representation of dictionaries</span></span>|<span data-ttu-id="5561c-177">Uma matriz de KeyValuePair\<K, V >, lida com tipos de chave que não são cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5561c-177">An array of KeyValuePair\<K,V>, handles key types that are not strings.</span></span>|<span data-ttu-id="5561c-178">Como objetos JSON reais – mas só trata os tipos de chave que são cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5561c-178">As actual JSON objects - but only handles key types that are strings.</span></span>|
|<span data-ttu-id="5561c-179">Caracteres de escape</span><span class="sxs-lookup"><span data-stu-id="5561c-179">Escaped characters</span></span>|<span data-ttu-id="5561c-180">Sempre com uma barra de escape (/); Nunca permite caracteres JSON inválidos sem escape, como "\n".</span><span class="sxs-lookup"><span data-stu-id="5561c-180">Always with an escape forward slash (/); never allows un-escaped invalid JSON characters, such as "\n".</span></span>|<span data-ttu-id="5561c-181">Com uma barra de escape (/) para valores DateTime.</span><span class="sxs-lookup"><span data-stu-id="5561c-181">With an escape forward slash (/) for DateTime values.</span></span>|

## <a name="see-also"></a><span data-ttu-id="5561c-182">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5561c-182">See also</span></span>

- [<span data-ttu-id="5561c-183">Como usar a configuração para adicionar um ponto de extremidade do ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="5561c-183">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
