---
title: "Como migrar serviços habilitados para AJAX ASP.NET para o WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 91b611af6c8de5c2bc0119838eb12950d3207177
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a>Como migrar serviços habilitados para AJAX ASP.NET para o WCF
Este tópico descreve os procedimentos para migrar um serviço básico do ASP.NET AJAX para um equivalente habilitado para AJAX [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço. Ele mostra como criar um funcionalmente equivalente [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] versão de um serviço ASP.NET AJAX. Os dois serviços podem ser usados lado a lado, ou o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço pode ser usado para substituir o serviço de AJAX do ASP.NET.  
  
 Migrando um serviço ASP.NET AJAX existente para um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço AJAX oferece os seguintes benefícios:  
  
-   Você pode expor seu serviço de AJAX como um serviço do SOAP com configuração mínima de extra.  
  
-   Você pode se beneficiar de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] recursos, como o rastreamento e assim por diante.  
  
 Os procedimentos a seguir presumem que você esteja usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
 O código que resulta dos procedimentos descritos neste tópico é fornecido no exemplo a seguir os procedimentos.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]expor um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de serviço por meio de um ponto de extremidade habilitado para AJAX, consulte o [como: usar a configuração para adicionar um ponto de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) tópico.  
  
### <a name="to-create-and-test-the-aspnet-web-service-application"></a>Para criar e testar o aplicativo de serviço da Web do ASP.NET  
  
1.  Abra [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Do **arquivo** menu, selecione **novo**, em seguida, **projeto**, em seguida, **Web**e, em seguida, selecione **aplicativo de serviço Web ASP.NET** .  
  
3.  Nomeie o projeto `ASPHello` e clique em **Okey**.  
  
4.  Descomente a linha no arquivo Service1. asmx.cs que contém `System.Web.Script.Services.ScriptService]` para habilitar o AJAX para esse serviço.  
  
5.  Do **criar** menu, selecione **compilar solução**.  
  
6.  Do **depurar** menu, selecione **Start Without Debugging**.  
  
7.  Na página da Web gerada, selecione o `HelloWorld` operação.  
  
8.  Clique o **Invoke** botão o `HelloWorld` página de teste. Você deve receber a seguinte resposta XML.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <string xmlns="http://tempuri.org/">Hello World</string>  
    ```  
  
9. Essa resposta confirma que agora você tem um serviço ASP.NET AJAX está funcionando e, em particular, o que o serviço agora tem exposto a um ponto de extremidade em Service1.asmx/HelloWorld que responde a HTTP POST solicitações e retorna o XML.  
  
     Agora você está pronto para converter esse serviço para usar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço AJAX.  
  
### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a>Para criar um aplicativo de serviço WCF AJAX equivalente  
  
1.  Com o botão direito do **ASPHello** do projeto e selecione **adicionar**, em seguida, **Novo Item**e, em seguida, **serviço do WCF habilitado para AJAX**.  
  
2.  O serviço de nomes `WCFHello` e clique em **adicionar**.  
  
3.  Abra o arquivo WCFHello.svc.cs.  
  
4.  A partir do Service1. asmx.cs, copie a seguinte implementação do `HelloWorld` operação.  
  
    ```  
    public string HelloWorld()  
    {  
         return "Hello World";  
    }  
    ```  
  
5.  Colar a implementação copiada do `HelloWorld` operação no arquivo WCFHello.svc.cs no lugar de código a seguir.  
  
    ```  
    public void DoWork()  
    {  
          // Add your operation implementation here  
          return;  
    }  
    ```  
  
6.  Especifique o `Namespace` atributo <xref:System.ServiceModel.ServiceContractAttribute> como `WCFHello`.  
  
    ```  
    [ServiceContract(Namespace="WCFHello")]  
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]  
    public class WCFHello  
    { … }  
    ```  
  
7.  Adicionar o <xref:System.ServiceModel.Web.WebInvokeAttribute> para o `HelloWorld` operação e conjunto de <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> propriedade para retornar <xref:System.ServiceModel.Web.WebMessageFormat.Xml>. Observe que, se não for definido, o padrão é do tipo de retorno <xref:System.ServiceModel.Web.WebMessageFormat.Json>.  
  
    ```  
    [OperationContract]  
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]  
    public string HelloWorld()  
    {  
        return "Hello World";  
    }  
    ```  
  
8.  Do **criar** menu, selecione **compilar solução**.  
  
9. Abra o arquivo WCFHello.svc e o **depurar** menu, selecione **Start Without Debugging**.  
  
10. Agora, o serviço expõe um ponto de extremidade em `WCFHello.svc/HelloWorld`, que responde a solicitações HTTP POST. Solicitações HTTP POST não podem ser testadas do navegador, mas o ponto de extremidade retorna XML a seguir do XML.  
  
    ```xml  
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>  
    ```  
  
11. O `WCFHello.svc/HelloWorld` e `Service1.aspx/HelloWorld` pontos de extremidade agora são funcionalmente equivalentes.  
  
## <a name="example"></a>Exemplo  
 O código que resulta dos procedimentos descritos neste tópico é fornecido no exemplo a seguir.  
  
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
  
 O <xref:System.Xml.XmlDocument> tipo não é suportado pelo <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> porque ele não é serializável, o <xref:System.Xml.Serialization.XmlSerializer>. Você pode usar um <xref:System.Xml.Linq.XDocument> digite ou serializar o <xref:System.Xml.XmlDocument.DocumentElement%2A> em vez disso.  
  
 Se os serviços Web ASMX estão sendo atualizados e migração lado a lado para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços, evite dois tipos de mapeamento para o mesmo nome no cliente. Isso faz com que uma exceção serializadores se o mesmo tipo é usado em uma <xref:System.Web.Services.WebMethodAttribute> e um <xref:System.ServiceModel.ServiceContractAttribute>:  
  
-   Se [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço é adicionado pela primeira vez, invocando o método de serviço da Web ASMX faz com que a exceção em <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> porque o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] definição de estilo do pedido no proxy tem precedência.  
  
-   Se o serviço da Web ASMX é adicionado pela primeira vez, chamar o método em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço faz com que a exceção em <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> porque a definição de estilo do serviço Web do pedido no proxy tem precedência.  
  
 Há diferenças significativas no comportamento entre o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> e o ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>. Por exemplo, o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> representa um dicionário como uma matriz de pares chave/valor, enquanto que o ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> representa um dicionário como objetos JSON reais. Portanto, o seguinte é o dicionário representado no ASP.NET AJAX.  
  
```  
Dictionary<string, int> d = new Dictionary<string, int>();  
d.Add("one", 1);  
d.Add("two", 2);  
```  
  
 Esse dicionário é representado de objetos JSON, conforme mostrado na lista a seguir:  
  
-   [{"Chave": "Um", "valor": 1}, {"Chave": "Dois", "valor": 2}] pelo<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>  
  
-   {"um": 1, "dois": 2}, o ASP.NET AJAX<xref:System.Web.Script.Serialization.JavaScriptSerializer>  
  
 O <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> é mais avançada no sentido de que ele possa manipular dicionários onde o tipo de chave não é cadeia de caracteres, enquanto o <xref:System.Web.Script.Serialization.JavaScriptSerializer> não é possível. Mas o último é mais amigável do JSON.  
  
 As diferenças significativas entre esses serializadores são resumidas na tabela a seguir.  
  
|Categoria de diferenças|DataContractJsonSerializer|ASP.NET AJAX JavaScriptSerializer|  
|-----------------------------|--------------------------------|---------------------------------------|  
|Desserializando o buffer vazio (novo byte[0]) em <xref:System.Object> (ou <xref:System.Uri>, ou algumas outras classes).|SerializationException|nulo|  
|Serialização de<xref:System.DBNull.Value>|{} (ou { type":"#System"})|Nulo|  
|Serialização de membros particulares de tipos [Serializable].|serializado|não serializado|  
|Serialização de propriedades públicas de <xref:System.Runtime.Serialization.ISerializable> tipos.|não serializado|serializado|  
|"Extensões" de JSON|Segue a especificação JSON, que requer aspas nos nomes de membro de objeto ({"a": "Olá"}).|Oferece suporte os nomes de membros de objeto sem aspas ({r: "Olá"}).|  
|<xref:System.DateTime>Tempo Universal Coordenado (UTC)|Não oferece suporte ao formato "\\/Date(123456789U)\\/" ou "\\/data\\(\d+ (U &#124;) (\\+\\-[\d\{4\]}))?\\) \\\\/)".|Formato dá suporte a "\\/Date(123456789U)\\/" e "\\/data\\(\d+ (U &#124;) (\\+\\-[\d\{4\]}))?\\) \\ \\/) "como valores de data e hora.|  
|Representação de dicionários|Uma matriz de KeyValuePair\<K, V >, manipula os tipos de chave que não são cadeias de caracteres.|Como objetos JSON reais - mas somente tipos de chave de identificadores que são cadeias de caracteres.|  
|Caracteres de escape|Sempre com um escape barra (/). nunca permite sem escapados caracteres inválidos de JSON, como "\n".|Com um escape barra (/) para valores de data e hora.|  
  
## <a name="see-also"></a>Consulte também  
 [Como: usar a configuração para adicionar um ponto de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
