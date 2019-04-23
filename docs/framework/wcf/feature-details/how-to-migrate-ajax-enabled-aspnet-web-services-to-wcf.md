---
title: 'Como: migrar serviços Web habilitados para AJAX ASP.NET para o WCF'
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 6114fa90b10a5d0cacb60a7ad40f63fae776e174
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337416"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a>Como: migrar serviços Web habilitados para AJAX ASP.NET para o WCF
Este tópico descreve procedimentos para migrar um serviço básico do ASP.NET AJAX a um serviço habilitado para AJAX Windows Communication Foundation (WCF) equivalente. Ele mostra como criar uma versão equivalente do WCF de um serviço ASP.NET AJAX. Os dois serviços, em seguida, podem ser usados lado a lado, ou o serviço WCF pode ser usado para substituir o serviço ASP.NET AJAX.

 Migrando um existente do ASP.NET AJAX serviço a um serviço WCF AJAX oferece os seguintes benefícios:

-   Você pode expor seu serviço de AJAX como um serviço SOAP com poucas configurações adicionais.

-   Você pode se beneficiar dos recursos do WCF, como rastreamento e assim por diante.

 Os procedimentos a seguir pressupõem que você está usando o Visual Studio 2012.

 O código que resulta dos procedimentos descritos neste tópico é fornecido no exemplo a seguir os procedimentos.

 Para obter mais informações sobre como expor um serviço WCF por meio de um ponto de extremidade habilitados para AJAX, consulte o [como: Usar a configuração para adicionar um ponto de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) tópico.

### <a name="to-create-and-test-the-aspnet-web-service-application"></a>Para criar e testar o aplicativo de serviço da Web do ASP.NET

1. Abra o Visual Studio 2012.

2. Do **arquivo** menu, selecione **New**, em seguida, **projeto**, em seguida, **Web**e, em seguida, selecione **aplicativo de serviço Web ASP.NET** .

3. Nomeie o projeto `ASPHello` e clique em **Okey**.

4. Remova a linha no arquivo de Service1.asmx.cs contém `System.Web.Script.Services.ScriptService]` para habilitar o AJAX para esse serviço.

5. Dos **construir** menu, selecione **compilar solução**.

6. No menu **Depurar**, selecione **Iniciar sem Depurar**.

7. Na página da Web gerada, selecione o `HelloWorld` operação.

8. Clique o **Invoke** botão o `HelloWorld` página de teste. Você deve receber a seguinte resposta XML.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. Essa resposta confirma que agora você tem um serviço ASP.NET AJAX está funcionando e, em particular, o que o serviço agora tem exposto a um ponto de extremidade em Service1.asmx/HelloWorld que responde a HTTP POST solicitações e retorna o XML.

     Agora você está pronto para converter esse serviço para usar um serviço WCF AJAX.

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a>Para criar um aplicativo de serviço WCF AJAX equivalente

1. Com o botão direito a **ASPHello** do projeto e selecione **Add**, em seguida, **Novo Item**e, em seguida, **serviço WCF habilitado para AJAX**.

2. Nomeie o serviço `WCFHello` e clique em **Add**.

3. Abra o arquivo WCFHello.svc.cs.

4. Service1.asmx.cs, copie a seguinte implementação do `HelloWorld` operação.

    ```
    public string HelloWorld()
    {
         return "Hello World";
    }
    ```

5. Colar a implementação copiada do `HelloWorld` operação no arquivo WCFHello.svc.cs no lugar o código a seguir.

    ```
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6. Especifique o `Namespace` de atributo para <xref:System.ServiceModel.ServiceContractAttribute> como `WCFHello`.

    ```
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7. Adicionar o <xref:System.ServiceModel.Web.WebInvokeAttribute> para o `HelloWorld` operação e defina o <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> propriedade para retornar <xref:System.ServiceModel.Web.WebMessageFormat.Xml>. Observe que, se não for definido, o padrão é de tipo de retorno <xref:System.ServiceModel.Web.WebMessageFormat.Json>.

    ```
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8. Dos **construir** menu, selecione **compilar solução**.

9. Abra o arquivo WCFHello.svc e para o **Debug** menu, selecione **Start Without Debugging**.

10. Agora, o serviço expõe um ponto de extremidade em `WCFHello.svc/HelloWorld`, que responde a solicitações HTTP POST. Não não possível testar a solicitações HTTP POST do navegador, mas o ponto de extremidade retorna XML a seguir do XML.

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. O `WCFHello.svc/HelloWorld` e o `Service1.aspx/HelloWorld` pontos de extremidade agora são funcionalmente equivalentes.

## <a name="example"></a>Exemplo
 O código que resulta dos procedimentos descritos neste tópico é fornecido no exemplo a seguir.

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

 O <xref:System.Xml.XmlDocument> tipo não tem suporte a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> porque ele não é serializável pelo <xref:System.Xml.Serialization.XmlSerializer>. Você pode usar tanto uma <xref:System.Xml.Linq.XDocument> digite ou serializar o <xref:System.Xml.XmlDocument.DocumentElement%2A> em vez disso.

 Se os serviços Web ASMX estão sendo atualizados e migrados lado a lado para os serviços WCF, evite a dois tipos de mapeamento para o mesmo nome no cliente. Isso faz com que uma exceção nos serializadores se o mesmo tipo for usado em uma <xref:System.Web.Services.WebMethodAttribute> e um <xref:System.ServiceModel.ServiceContractAttribute>:

-   Se o serviço do WCF é adicionado pela primeira vez, invocar o método de serviço da Web ASMX faz com que a exceção no <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> porque a definição de estilo do WCF do pedido no proxy tem precedência.

-   Se o serviço da Web ASMX é adicionado pela primeira vez, invocar o método no serviço do WCF faz com que a exceção no <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> porque a definição de estilo do pedido no proxy do serviço da Web terá precedência.

 Existem diferenças significativas no comportamento entre o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> e o ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>. Por exemplo, o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> representa um dicionário como uma matriz de pares chave/valor, ao passo que o ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> representa um dicionário como objetos do JSON reais. Portanto, o seguinte é o dicionário representado no ASP.NET AJAX.

```
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 Esse dicionário é representado em objetos JSON, conforme mostrado na lista a seguir:

-   [{"Chave": "Um", "Value": 1}, {"Chave": "Dois", "Value": 2}] pela <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>

-   {"um": 1, "dois": 2}, o AJAX ASP.NET <xref:System.Web.Script.Serialization.JavaScriptSerializer>

 O <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> é mais poderoso no sentido de que ele pode manipular dicionários onde o tipo de chave não é cadeia de caracteres, enquanto o <xref:System.Web.Script.Serialization.JavaScriptSerializer> não é possível. Mas o último é mais amigável para JSON.

 As diferenças significativas entre esses serializadores são resumidas na tabela a seguir.

|Categoria das diferenças|DataContractJsonSerializer|JavaScriptSerializer do AJAX ASP.NET|
|-----------------------------|--------------------------------|---------------------------------------|
|Ao desserializar o buffer vazio (novo byte[0]) em <xref:System.Object> (ou <xref:System.Uri>, ou algumas outras classes).|SerializationException|nulo|
|Serialização de <xref:System.DBNull.Value>|{} (ou { type":"#System"})|Nulo|
|Serialização de membros privados de tipos [Serializable].|serializado|não serializado|
|Serialização de propriedades públicas do <xref:System.Runtime.Serialization.ISerializable> tipos.|não serializado|serializado|
|"Extensões" do JSON|Adere à especificação JSON, que requer aspas nos nomes de membro de objeto ({"a": "hello"}).|Oferece suporte os nomes de membros de objeto sem aspas ({r: "hello"}).|
|<xref:System.DateTime> Hora Universal coordenada (UTC)|Não oferece suporte ao formato "\\/Date(123456789U)\\/" ou "\\/data\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\\\/)".|Formato dá suporte a "\\/Date(123456789U)\\/" e "\\/data\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\ \\/) "como valores de data e hora.|
|Representação de dicionários|Uma matriz de KeyValuePair\<K, V >, lida com tipos de chave que não são cadeias de caracteres.|Como objetos do JSON reais – mas apenas tipos de chave de identificadores que são cadeias de caracteres.|
|Caracteres de escape|Sempre com um escape de barra (/). nunca permite sem escape caracteres inválidos de JSON, como "\n".|Com um escape de barra (/) para valores de data e hora.|

## <a name="see-also"></a>Consulte também

- [Como: Usar a configuração para adicionar um ponto de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
