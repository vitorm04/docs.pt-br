---
title: Como migrar serviços habilitados para AJAX ASP.NET para o WCF
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 048408adf8678c243a225a233cb1173c9b7f869f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a><span data-ttu-id="f9db3-102">Como migrar serviços habilitados para AJAX ASP.NET para o WCF</span><span class="sxs-lookup"><span data-stu-id="f9db3-102">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>
<span data-ttu-id="f9db3-103">Este tópico descreve procedimentos para migrar um serviço básico do ASP.NET AJAX para um serviço habilitado para AJAX Windows Communication Foundation (WCF) equivalente.</span><span class="sxs-lookup"><span data-stu-id="f9db3-103">This topic outlines procedures to migrate a basic ASP.NET AJAX service to an equivalent AJAX-enabled Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="f9db3-104">Ele mostra como criar uma versão WCF funcionalmente equivalente de um serviço ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="f9db3-104">It shows how to create a functionally equivalent WCF version of an ASP.NET AJAX service.</span></span> <span data-ttu-id="f9db3-105">Os dois serviços podem ser usados lado a lado, ou o serviço WCF pode ser usado para substituir o serviço de AJAX do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f9db3-105">The two services can then be used side by side, or the WCF service can be used to replace the ASP.NET AJAX service.</span></span>  
  
 <span data-ttu-id="f9db3-106">Migrando um existente do ASP.NET AJAX serviço para um serviço WCF AJAX oferece os seguintes benefícios:</span><span class="sxs-lookup"><span data-stu-id="f9db3-106">Migrating an existing ASP.NET AJAX service to a WCF AJAX service gives you the following benefits:</span></span>  
  
-   <span data-ttu-id="f9db3-107">Você pode expor seu serviço de AJAX como um serviço do SOAP com configuração mínima de extra.</span><span class="sxs-lookup"><span data-stu-id="f9db3-107">You can expose your AJAX service as a SOAP service with minimal extra configuration.</span></span>  
  
-   <span data-ttu-id="f9db3-108">Você pode se beneficiar dos recursos do WCF, como o rastreamento e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="f9db3-108">You can benefit from WCF features such as tracing, and so on.</span></span>  
  
 <span data-ttu-id="f9db3-109">Os procedimentos a seguir presumem que você esteja usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f9db3-109">The following procedures assume that you are using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
 <span data-ttu-id="f9db3-110">O código que resulta dos procedimentos descritos neste tópico é fornecido no exemplo a seguir os procedimentos.</span><span class="sxs-lookup"><span data-stu-id="f9db3-110">The code that results from the procedures outlined in this topic is provided in the example following the procedures.</span></span>  
  
 <span data-ttu-id="f9db3-111">Para obter mais informações sobre a exposição de um serviço WCF por meio de um ponto de extremidade habilitado para AJAX, consulte o [como: usar a configuração para adicionar um ponto de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="f9db3-111">For more information about exposing a WCF service through an AJAX-enabled endpoint, see the [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) topic.</span></span>  
  
### <a name="to-create-and-test-the-aspnet-web-service-application"></a><span data-ttu-id="f9db3-112">Para criar e testar o aplicativo de serviço da Web do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f9db3-112">To create and test the ASP.NET Web service application</span></span>  
  
1.  <span data-ttu-id="f9db3-113">Abra [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f9db3-113">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="f9db3-114">Do **arquivo** menu, selecione **novo**, em seguida, **projeto**, em seguida, **Web**e, em seguida, selecione **aplicativo de serviço Web ASP.NET** .</span><span class="sxs-lookup"><span data-stu-id="f9db3-114">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Service Application**.</span></span>  
  
3.  <span data-ttu-id="f9db3-115">Nomeie o projeto `ASPHello` e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="f9db3-115">Name the project `ASPHello` and click **OK**.</span></span>  
  
4.  <span data-ttu-id="f9db3-116">Descomente a linha no arquivo Service1. asmx.cs que contém `System.Web.Script.Services.ScriptService]` para habilitar o AJAX para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="f9db3-116">Uncomment the line in the Service1.asmx.cs file that contains `System.Web.Script.Services.ScriptService]` to enable AJAX for this service.</span></span>  
  
5.  <span data-ttu-id="f9db3-117">Do **criar** menu, selecione **compilar solução**.</span><span class="sxs-lookup"><span data-stu-id="f9db3-117">From the **Build** menu, select **Build Solution**.</span></span>  
  
6.  <span data-ttu-id="f9db3-118">Do **depurar** menu, selecione **Start Without Debugging**.</span><span class="sxs-lookup"><span data-stu-id="f9db3-118">From the **Debug** menu, select **Start Without Debugging**.</span></span>  
  
7.  <span data-ttu-id="f9db3-119">Na página da Web gerada, selecione o `HelloWorld` operação.</span><span class="sxs-lookup"><span data-stu-id="f9db3-119">On the Web page generated, select the `HelloWorld` operation.</span></span>  
  
8.  <span data-ttu-id="f9db3-120">Clique o **Invoke** botão o `HelloWorld` página de teste.</span><span class="sxs-lookup"><span data-stu-id="f9db3-120">Click the **Invoke** button on the `HelloWorld` test page.</span></span> <span data-ttu-id="f9db3-121">Você deve receber a seguinte resposta XML.</span><span class="sxs-lookup"><span data-stu-id="f9db3-121">You should receive the following XML response.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <string xmlns="http://tempuri.org/">Hello World</string>  
    ```  
  
9. <span data-ttu-id="f9db3-122">Essa resposta confirma que agora você tem um serviço ASP.NET AJAX está funcionando e, em particular, o que o serviço agora tem exposto a um ponto de extremidade em Service1.asmx/HelloWorld que responde a HTTP POST solicitações e retorna o XML.</span><span class="sxs-lookup"><span data-stu-id="f9db3-122">This response confirms that you now have a functioning ASP.NET AJAX service and, in particular, that the service has now exposed an endpoint at Service1.asmx/HelloWorld that responds to HTTP POST requests and returns XML.</span></span>  
  
     <span data-ttu-id="f9db3-123">Agora você está pronto para converter esse serviço para usar um serviço WCF AJAX.</span><span class="sxs-lookup"><span data-stu-id="f9db3-123">Now you are ready to convert this service to use a WCF AJAX service.</span></span>  
  
### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a><span data-ttu-id="f9db3-124">Para criar um aplicativo de serviço WCF AJAX equivalente</span><span class="sxs-lookup"><span data-stu-id="f9db3-124">To create an equivalent WCF AJAX service application</span></span>  
  
1.  <span data-ttu-id="f9db3-125">Com o botão direito do **ASPHello** do projeto e selecione **adicionar**, em seguida, **Novo Item**e, em seguida, **serviço do WCF habilitado para AJAX**.</span><span class="sxs-lookup"><span data-stu-id="f9db3-125">Right-click the **ASPHello** project and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>  
  
2.  <span data-ttu-id="f9db3-126">O serviço de nomes `WCFHello` e clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="f9db3-126">Name the service `WCFHello` and click **Add**.</span></span>  
  
3.  <span data-ttu-id="f9db3-127">Abra o arquivo WCFHello.svc.cs.</span><span class="sxs-lookup"><span data-stu-id="f9db3-127">Open the WCFHello.svc.cs file.</span></span>  
  
4.  <span data-ttu-id="f9db3-128">A partir do Service1. asmx.cs, copie a seguinte implementação do `HelloWorld` operação.</span><span class="sxs-lookup"><span data-stu-id="f9db3-128">From Service1.asmx.cs, copy the following implementation of the `HelloWorld` operation.</span></span>  
  
    ```  
    public string HelloWorld()  
    {  
         return "Hello World";  
    }  
    ```  
  
5.  <span data-ttu-id="f9db3-129">Colar a implementação copiada do `HelloWorld` operação no arquivo WCFHello.svc.cs no lugar de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="f9db3-129">Paste to copied implementation of the `HelloWorld` operation into the WCFHello.svc.cs file in place of the following code.</span></span>  
  
    ```  
    public void DoWork()  
    {  
          // Add your operation implementation here  
          return;  
    }  
    ```  
  
6.  <span data-ttu-id="f9db3-130">Especifique o `Namespace` atributo <xref:System.ServiceModel.ServiceContractAttribute> como `WCFHello`.</span><span class="sxs-lookup"><span data-stu-id="f9db3-130">Specify the `Namespace` attribute for <xref:System.ServiceModel.ServiceContractAttribute> as `WCFHello`.</span></span>  
  
    ```  
    [ServiceContract(Namespace="WCFHello")]  
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]  
    public class WCFHello  
    { … }  
    ```  
  
7.  <span data-ttu-id="f9db3-131">Adicionar o <xref:System.ServiceModel.Web.WebInvokeAttribute> para o `HelloWorld` operação e conjunto de <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> propriedade para retornar <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span><span class="sxs-lookup"><span data-stu-id="f9db3-131">Add the <xref:System.ServiceModel.Web.WebInvokeAttribute> to the `HelloWorld` operation and set the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> property to return <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span></span> <span data-ttu-id="f9db3-132">Observe que, se não for definido, o padrão é do tipo de retorno <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="f9db3-132">Note that, if not set, the default return type is <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span>  
  
    ```  
    [OperationContract]  
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]  
    public string HelloWorld()  
    {  
        return "Hello World";  
    }  
    ```  
  
8.  <span data-ttu-id="f9db3-133">Do **criar** menu, selecione **compilar solução**.</span><span class="sxs-lookup"><span data-stu-id="f9db3-133">From the **Build** menu, select **Build Solution**.</span></span>  
  
9. <span data-ttu-id="f9db3-134">Abra o arquivo WCFHello.svc e o **depurar** menu, selecione **Start Without Debugging**.</span><span class="sxs-lookup"><span data-stu-id="f9db3-134">Open the WCFHello.svc file and from the **Debug** menu, select **Start Without Debugging**.</span></span>  
  
10. <span data-ttu-id="f9db3-135">Agora, o serviço expõe um ponto de extremidade em `WCFHello.svc/HelloWorld`, que responde a solicitações HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="f9db3-135">The service now exposes an endpoint at `WCFHello.svc/HelloWorld`, which responds to HTTP POST requests.</span></span> <span data-ttu-id="f9db3-136">Solicitações HTTP POST não podem ser testadas do navegador, mas o ponto de extremidade retorna XML a seguir do XML.</span><span class="sxs-lookup"><span data-stu-id="f9db3-136">HTTP POST requests cannot be tested from the browser, but the endpoint returns XML following XML.</span></span>  
  
    ```xml  
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>  
    ```  
  
11. <span data-ttu-id="f9db3-137">O `WCFHello.svc/HelloWorld` e `Service1.aspx/HelloWorld` pontos de extremidade agora são funcionalmente equivalentes.</span><span class="sxs-lookup"><span data-stu-id="f9db3-137">The `WCFHello.svc/HelloWorld` and the `Service1.aspx/HelloWorld` endpoints are now functionally equivalent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9db3-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f9db3-138">Example</span></span>  
 <span data-ttu-id="f9db3-139">O código que resulta dos procedimentos descritos neste tópico é fornecido no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f9db3-139">The code that results from the procedures outlined in this topic is provided in the following example.</span></span>  
  
```  
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
  
 <span data-ttu-id="f9db3-140">O <xref:System.Xml.XmlDocument> tipo não é suportado pelo <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> porque ele não é serializável, o <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f9db3-140">The <xref:System.Xml.XmlDocument> type is not supported by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because it is not serializable by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="f9db3-141">Você pode usar um <xref:System.Xml.Linq.XDocument> digite ou serializar o <xref:System.Xml.XmlDocument.DocumentElement%2A> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="f9db3-141">You can use either an <xref:System.Xml.Linq.XDocument> type, or serialize the <xref:System.Xml.XmlDocument.DocumentElement%2A> instead.</span></span>  
  
 <span data-ttu-id="f9db3-142">Se os serviços Web ASMX estão sendo atualizados e migrados lado a lado para serviços WCF, evite a dois tipos de mapeamento para o mesmo nome no cliente.</span><span class="sxs-lookup"><span data-stu-id="f9db3-142">If ASMX Web services are being upgraded and migrated side-by-side to WCF services, avoid mapping two types to the same name on the client.</span></span> <span data-ttu-id="f9db3-143">Isso faz com que uma exceção serializadores se o mesmo tipo é usado em uma <xref:System.Web.Services.WebMethodAttribute> e um <xref:System.ServiceModel.ServiceContractAttribute>:</span><span class="sxs-lookup"><span data-stu-id="f9db3-143">This causes an exception in serializers if the same type is used in a <xref:System.Web.Services.WebMethodAttribute> and a <xref:System.ServiceModel.ServiceContractAttribute>:</span></span>  
  
-   <span data-ttu-id="f9db3-144">Se o serviço do WCF é adicionado pela primeira vez, invocando o método de serviço da Web ASMX faz com que a exceção em <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> porque a definição de estilo do WCF do pedido no proxy tem precedência.</span><span class="sxs-lookup"><span data-stu-id="f9db3-144">If WCF service is added first, invoking the method on ASMX Web Service causes exception in <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> because the WCF style definition of the order in the proxy takes precedence.</span></span>  
  
-   <span data-ttu-id="f9db3-145">Se o serviço da Web ASMX é adicionado pela primeira vez, chamar o método no serviço do WCF faz com que a exceção em <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> porque a definição de estilo do serviço Web do pedido no proxy tem precedência.</span><span class="sxs-lookup"><span data-stu-id="f9db3-145">If ASMX Web Service is added first, invoking method on WCF service causes exception in <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because the Web Service style definition of the order in the proxy takes precedence.</span></span>  
  
 <span data-ttu-id="f9db3-146">Há diferenças significativas no comportamento entre o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> e o ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f9db3-146">There are significant differences in behavior between the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> and the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span></span> <span data-ttu-id="f9db3-147">Por exemplo, o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> representa um dicionário como uma matriz de pares chave/valor, enquanto que o ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> representa um dicionário como objetos JSON reais.</span><span class="sxs-lookup"><span data-stu-id="f9db3-147">For example, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> represents a dictionary as an array of key/value pairs, whereas the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> represents a dictionary as actual JSON objects.</span></span> <span data-ttu-id="f9db3-148">Portanto, o seguinte é o dicionário representado no ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="f9db3-148">So the following is the dictionary represented in ASP.NET AJAX.</span></span>  
  
```  
Dictionary<string, int> d = new Dictionary<string, int>();  
d.Add("one", 1);  
d.Add("two", 2);  
```  
  
 <span data-ttu-id="f9db3-149">Esse dicionário é representado de objetos JSON, conforme mostrado na lista a seguir:</span><span class="sxs-lookup"><span data-stu-id="f9db3-149">This dictionary is represented in JSON objects as shown in the following list:</span></span>  
  
-   <span data-ttu-id="f9db3-150">[{"Chave": "Um", "valor": 1}, {"Chave": "Dois", "valor": 2}] pelo <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span><span class="sxs-lookup"><span data-stu-id="f9db3-150">[{"Key":"one","Value":1},{"Key":"two","Value":2}] by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span></span>  
  
-   <span data-ttu-id="f9db3-151">{"um": 1, "dois": 2}, o ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span><span class="sxs-lookup"><span data-stu-id="f9db3-151">{"one":1,"two":2} by the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span></span>  
  
 <span data-ttu-id="f9db3-152">O <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> é mais avançada no sentido de que ele possa manipular dicionários onde o tipo de chave não é cadeia de caracteres, enquanto o <xref:System.Web.Script.Serialization.JavaScriptSerializer> não é possível.</span><span class="sxs-lookup"><span data-stu-id="f9db3-152">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is more powerful in the sense that it can handle dictionaries where the key type is not string, while the <xref:System.Web.Script.Serialization.JavaScriptSerializer> cannot.</span></span> <span data-ttu-id="f9db3-153">Mas o último é mais amigável do JSON.</span><span class="sxs-lookup"><span data-stu-id="f9db3-153">But the latter is more JSON-friendly.</span></span>  
  
 <span data-ttu-id="f9db3-154">As diferenças significativas entre esses serializadores são resumidas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="f9db3-154">The significant differences between these serializers are summarized in the following table.</span></span>  
  
|<span data-ttu-id="f9db3-155">Categoria de diferenças</span><span class="sxs-lookup"><span data-stu-id="f9db3-155">Category of Differences</span></span>|<span data-ttu-id="f9db3-156">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="f9db3-156">DataContractJsonSerializer</span></span>|<span data-ttu-id="f9db3-157">ASP.NET AJAX JavaScriptSerializer</span><span class="sxs-lookup"><span data-stu-id="f9db3-157">ASP.NET AJAX JavaScriptSerializer</span></span>|  
|-----------------------------|--------------------------------|---------------------------------------|  
|<span data-ttu-id="f9db3-158">Desserializando o buffer vazio (novo byte[0]) em <xref:System.Object> (ou <xref:System.Uri>, ou algumas outras classes).</span><span class="sxs-lookup"><span data-stu-id="f9db3-158">Deserializing the empty buffer (new byte[0]) into <xref:System.Object> (or <xref:System.Uri>, or some other classes).</span></span>|<span data-ttu-id="f9db3-159">SerializationException</span><span class="sxs-lookup"><span data-stu-id="f9db3-159">SerializationException</span></span>|<span data-ttu-id="f9db3-160">nulo</span><span class="sxs-lookup"><span data-stu-id="f9db3-160">null</span></span>|  
|<span data-ttu-id="f9db3-161">Serialização de <xref:System.DBNull.Value></span><span class="sxs-lookup"><span data-stu-id="f9db3-161">Serialization of <xref:System.DBNull.Value></span></span>|<span data-ttu-id="f9db3-162">{} (ou { type":"#System"})</span><span class="sxs-lookup"><span data-stu-id="f9db3-162">{} (or {"__type":"#System"})</span></span>|<span data-ttu-id="f9db3-163">Nulo</span><span class="sxs-lookup"><span data-stu-id="f9db3-163">Null</span></span>|  
|<span data-ttu-id="f9db3-164">Serialização de membros particulares de tipos [Serializable].</span><span class="sxs-lookup"><span data-stu-id="f9db3-164">Serialization of the private members of [Serializable] types.</span></span>|<span data-ttu-id="f9db3-165">serializado</span><span class="sxs-lookup"><span data-stu-id="f9db3-165">serialized</span></span>|<span data-ttu-id="f9db3-166">não serializado</span><span class="sxs-lookup"><span data-stu-id="f9db3-166">not serialized</span></span>|  
|<span data-ttu-id="f9db3-167">Serialização de propriedades públicas de <xref:System.Runtime.Serialization.ISerializable> tipos.</span><span class="sxs-lookup"><span data-stu-id="f9db3-167">Serialization of the public properties of <xref:System.Runtime.Serialization.ISerializable> types.</span></span>|<span data-ttu-id="f9db3-168">não serializado</span><span class="sxs-lookup"><span data-stu-id="f9db3-168">not serialized</span></span>|<span data-ttu-id="f9db3-169">serializado</span><span class="sxs-lookup"><span data-stu-id="f9db3-169">serialized</span></span>|  
|<span data-ttu-id="f9db3-170">"Extensões" de JSON</span><span class="sxs-lookup"><span data-stu-id="f9db3-170">"Extensions" of JSON</span></span>|<span data-ttu-id="f9db3-171">Segue a especificação JSON, que requer aspas nos nomes de membro de objeto ({"a": "Olá"}).</span><span class="sxs-lookup"><span data-stu-id="f9db3-171">Adheres to the JSON specification, which requires quotes on object member names ({"a":"hello"}).</span></span>|<span data-ttu-id="f9db3-172">Oferece suporte os nomes de membros de objeto sem aspas ({r: "Olá"}).</span><span class="sxs-lookup"><span data-stu-id="f9db3-172">Supports the names of object members without quotes ({a:"hello"}).</span></span>|  
|<span data-ttu-id="f9db3-173"><xref:System.DateTime> Tempo Universal Coordenado (UTC)</span><span class="sxs-lookup"><span data-stu-id="f9db3-173"><xref:System.DateTime> Coordinated Universal Time (UTC)</span></span>|<span data-ttu-id="f9db3-174">Não oferece suporte ao formato "\\/Date(123456789U)\\/" ou "\\/data\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\\\/)".</span><span class="sxs-lookup"><span data-stu-id="f9db3-174">Does not support format "\\/Date(123456789U)\\/" or "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)".</span></span>|<span data-ttu-id="f9db3-175">Formato dá suporte a "\\/Date(123456789U)\\/" e "\\/data\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\ \\/) "como valores de data e hora.</span><span class="sxs-lookup"><span data-stu-id="f9db3-175">Supports format "\\/Date(123456789U)\\/" and "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)" as DateTime values.</span></span>|  
|<span data-ttu-id="f9db3-176">Representação de dicionários</span><span class="sxs-lookup"><span data-stu-id="f9db3-176">Representation of dictionaries</span></span>|<span data-ttu-id="f9db3-177">Uma matriz de KeyValuePair\<K, V >, manipula os tipos de chave que não são cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f9db3-177">An array of KeyValuePair\<K,V>, handles key types that are not strings.</span></span>|<span data-ttu-id="f9db3-178">Como objetos JSON reais - mas somente tipos de chave de identificadores que são cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f9db3-178">As actual JSON objects - but only handles key types that are strings.</span></span>|  
|<span data-ttu-id="f9db3-179">Caracteres de escape</span><span class="sxs-lookup"><span data-stu-id="f9db3-179">Escaped characters</span></span>|<span data-ttu-id="f9db3-180">Sempre com um escape barra (/). nunca permite sem escapados caracteres inválidos de JSON, como "\n".</span><span class="sxs-lookup"><span data-stu-id="f9db3-180">Always with an escape forward slash (/); never allows un-escaped invalid JSON characters, such as "\n".</span></span>|<span data-ttu-id="f9db3-181">Com um escape barra (/) para valores de data e hora.</span><span class="sxs-lookup"><span data-stu-id="f9db3-181">With an escape forward slash (/) for DateTime values.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9db3-182">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9db3-182">See Also</span></span>  
 [<span data-ttu-id="f9db3-183">Como usar a configuração para adicionar um ponto de extremidade do ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="f9db3-183">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
