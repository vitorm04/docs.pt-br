---
title: 'Como: criar um serviço que aceita dados arbitrários usando o modelo de programação WCF REST'
ms.date: 03/30/2017
ms.assetid: e566c15a-b600-4e4a-be3a-4af43e767dae
ms.openlocfilehash: a1c30491f6c5b0a91f93a6f26417f9dc2b996a48
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614789"
---
# <a name="how-to-create-a-service-that-accepts-arbitrary-data-using-the-wcf-rest-programming-model"></a><span data-ttu-id="f9157-102">Como: criar um serviço que aceita dados arbitrários usando o modelo de programação WCF REST</span><span class="sxs-lookup"><span data-stu-id="f9157-102">How to: Create a Service That Accepts Arbitrary Data using the WCF REST Programming Model</span></span>
<span data-ttu-id="f9157-103">Às vezes, os desenvolvedores devem ter controle total sobre como os dados são retornados de uma operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="f9157-103">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="f9157-104">Esse é o caso quando uma operação de serviço deve retornar dados em um formato não tem suporte byWCF.</span><span class="sxs-lookup"><span data-stu-id="f9157-104">This is the case when a service operation must return data in a format not supported byWCF.</span></span> <span data-ttu-id="f9157-105">Este tópico discute usando o modelo de programação WCF REST para criar um serviço que recebe dados arbitrários.</span><span class="sxs-lookup"><span data-stu-id="f9157-105">This topic discusses using the WCF REST Programming Model to create a service that receives arbitrary data.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="f9157-106">Para implementar o contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="f9157-106">To implement the service contract</span></span>  
  
1. <span data-ttu-id="f9157-107">Defina o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="f9157-107">Define the service contract.</span></span> <span data-ttu-id="f9157-108">A operação que recebe os dados arbitrários deve ter um parâmetro de tipo <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="f9157-108">The operation that receives the arbitrary data must have a parameter of type <xref:System.IO.Stream>.</span></span> <span data-ttu-id="f9157-109">Além disso, esse parâmetro deve ser o único parâmetro passado no corpo da solicitação.</span><span class="sxs-lookup"><span data-stu-id="f9157-109">In addition, this parameter must be the only parameter passed in the body of the request.</span></span> <span data-ttu-id="f9157-110">A operação descrita neste exemplo também usa um parâmetro de nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="f9157-110">The operation described in this example also takes a filename parameter.</span></span> <span data-ttu-id="f9157-111">Este parâmetro é passado na URL da solicitação.</span><span class="sxs-lookup"><span data-stu-id="f9157-111">This parameter is passed within the URL of the request.</span></span> <span data-ttu-id="f9157-112">Você pode especificar que um parâmetro é passado na URL, especificando um <xref:System.UriTemplate> no <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f9157-112">You can specify that a parameter is passed within the URL by specifying a <xref:System.UriTemplate> in the <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="f9157-113">Nesse caso, que o URI usado para chamar esse método termina em "UploadFile/alguns-nome do arquivo".</span><span class="sxs-lookup"><span data-stu-id="f9157-113">In this case the URI used to call this method ends in "UploadFile/Some-Filename".</span></span> <span data-ttu-id="f9157-114">A parte "{filename}" do modelo de URI especifica que o parâmetro de nome de arquivo para a operação é passado no URI usado para chamar a operação.</span><span class="sxs-lookup"><span data-stu-id="f9157-114">The "{filename}" portion of the URI template specifies that the filename parameter for the operation is passed within the URI used to call the operation.</span></span>  
  
    ```csharp  
     [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    ```  
  
2. <span data-ttu-id="f9157-115">Implemente o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="f9157-115">Implement the service contract.</span></span> <span data-ttu-id="f9157-116">O contrato tem apenas um método, `UploadFile` que recebe um arquivo de dados arbitrários em um fluxo.</span><span class="sxs-lookup"><span data-stu-id="f9157-116">The contract has only one method, `UploadFile` that receives a file of arbitrary data in a stream.</span></span> <span data-ttu-id="f9157-117">A operação lê o fluxo de contagem do número de bytes lidos e, em seguida, exibe o nome do arquivo e o número de bytes lidos.</span><span class="sxs-lookup"><span data-stu-id="f9157-117">The operation reads the stream counting the number of bytes read and then displays the filename and the number of bytes read.</span></span>  
  
    ```csharp  
    public class RawDataService : IReceiveData  
    {  
        public void UploadFile(string fileName, Stream fileContents)  
        {  
            byte[] buffer = new byte[10000];  
            int bytesRead, totalBytesRead = 0;  
            do  
            {  
                bytesRead = fileContents.Read(buffer, 0, buffer.Length);  
                totalBytesRead += bytesRead;  
            } while (bytesRead > 0);  
            Console.WriteLine("Service: Received file {0} with {1} bytes", fileName, totalBytesRead);  
        }  
    }  
    ```  
  
### <a name="to-host-the-service"></a><span data-ttu-id="f9157-118">Para hospedar o serviço</span><span class="sxs-lookup"><span data-stu-id="f9157-118">To host the service</span></span>  
  
1. <span data-ttu-id="f9157-119">Crie um aplicativo de console para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="f9157-119">Create a console application to host the service.</span></span>  
  
    ```csharp  
    class Program  
    {  
       static void Main(string[] args)  
       {  
       }  
    }  
    ```  
  
2. <span data-ttu-id="f9157-120">Crie uma variável para manter o endereço básico para o serviço dentro de `Main` método.</span><span class="sxs-lookup"><span data-stu-id="f9157-120">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```csharp  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. <span data-ttu-id="f9157-121">Criar um <xref:System.ServiceModel.ServiceHost> instância para o serviço que especifica a classe de serviço e o endereço básico.</span><span class="sxs-lookup"><span data-stu-id="f9157-121">Create a <xref:System.ServiceModel.ServiceHost> instance for the service that specifies the service class and the base address.</span></span>  
  
    ```csharp  
    ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
    ```  
  
4. <span data-ttu-id="f9157-122">Adicionar um ponto de extremidade que especifica o contrato <xref:System.ServiceModel.WebHttpBinding>, e <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="f9157-122">Add an endpoint that specifies the contract, <xref:System.ServiceModel.WebHttpBinding>, and <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. <span data-ttu-id="f9157-123">Abra o host do serviço.</span><span class="sxs-lookup"><span data-stu-id="f9157-123">Open the service host.</span></span> <span data-ttu-id="f9157-124">O serviço agora está pronto para receber solicitações.</span><span class="sxs-lookup"><span data-stu-id="f9157-124">The service is now ready to receive requests.</span></span>  
  
    ```csharp  
    host.Open();  
    Console.WriteLine("Host opened");  
    ```  
  
### <a name="to-call-the-service-programmatically"></a><span data-ttu-id="f9157-125">Para chamar o serviço de forma programática</span><span class="sxs-lookup"><span data-stu-id="f9157-125">To call the service programmatically</span></span>  
  
1. <span data-ttu-id="f9157-126">Criar um <xref:System.Net.HttpWebRequest> com o URI usado para chamar o serviço.</span><span class="sxs-lookup"><span data-stu-id="f9157-126">Create a <xref:System.Net.HttpWebRequest> with the URI used to call the service.</span></span> <span data-ttu-id="f9157-127">Nesse código, o endereço base é combinado com `"/UploadFile/Text"`.</span><span class="sxs-lookup"><span data-stu-id="f9157-127">In this code, the base address is combined with `"/UploadFile/Text"`.</span></span> <span data-ttu-id="f9157-128">O `"UploadFile"` parte do URI especifica a operação para chamar.</span><span class="sxs-lookup"><span data-stu-id="f9157-128">The `"UploadFile"` portion of the URI specifies the operation to call.</span></span> <span data-ttu-id="f9157-129">O `"Test.txt"` parte do URI especifica o parâmetro de nome de arquivo para passar para o `UploadFile` operação.</span><span class="sxs-lookup"><span data-stu-id="f9157-129">The `"Test.txt"` portion of the URI specifies the filename parameter to pass to the `UploadFile` operation.</span></span> <span data-ttu-id="f9157-130">Ambos esses itens do mapa para o <xref:System.UriTemplate> aplicados ao contrato de operação.</span><span class="sxs-lookup"><span data-stu-id="f9157-130">Both of these items map to the <xref:System.UriTemplate> applied to the operation contract.</span></span>  
  
    ```csharp  
    HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
    ```  
  
2. <span data-ttu-id="f9157-131">Defina a <xref:System.Net.HttpWebRequest.Method%2A> propriedade do <xref:System.Net.HttpWebRequest> para `POST` e o <xref:System.Net.HttpWebRequest.ContentType%2A> propriedade para `"text/plain"`.</span><span class="sxs-lookup"><span data-stu-id="f9157-131">Set the <xref:System.Net.HttpWebRequest.Method%2A> property of the <xref:System.Net.HttpWebRequest> to `POST` and the <xref:System.Net.HttpWebRequest.ContentType%2A> property to `"text/plain"`.</span></span> <span data-ttu-id="f9157-132">Isso instrui o serviço que o código está enviando dados e são de que os dados em texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="f9157-132">This tells the service that the code is sending data and that data is in plain text.</span></span>  
  
    ```csharp  
    req.Method = "POST";  
    req.ContentType = "text/plain";  
    ```  
  
3. <span data-ttu-id="f9157-133">Chamar <xref:System.Net.HttpWebRequest.GetRequestStream%2A> para obter o fluxo da solicitação, crie os dados para enviar, gravar dados no fluxo de solicitação e feche o fluxo.</span><span class="sxs-lookup"><span data-stu-id="f9157-133">Call <xref:System.Net.HttpWebRequest.GetRequestStream%2A> to get the request stream, create the data to send, write that data to the request stream, and close the stream.</span></span>  
  
    ```csharp  
    Stream reqStream = req.GetRequestStream();  
    byte[] fileToSend = new byte[12345];  
    for (int i = 0; i < fileToSend.Length; i++)  
       {  
           fileToSend[i] = (byte)('a' + (i % 26));  
       }  
    reqStream.Write(fileToSend, 0, fileToSend.Length);  
    reqStream.Close();  
    ```  
  
4. <span data-ttu-id="f9157-134">Obter a resposta do serviço chamando <xref:System.Net.HttpWebRequest.GetResponse%2A> e exibir os dados de resposta para o console.</span><span class="sxs-lookup"><span data-stu-id="f9157-134">Get the response from the service by calling <xref:System.Net.HttpWebRequest.GetResponse%2A> and display the response data to the console.</span></span>  
  
    ```csharp  
    HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
    Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
    ```  
  
5. <span data-ttu-id="f9157-135">Feche o host de serviço.</span><span class="sxs-lookup"><span data-stu-id="f9157-135">Close the service host.</span></span>  
  
    ```csharp  
    host.Close();  
    ```  
  
## <a name="example"></a><span data-ttu-id="f9157-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f9157-136">Example</span></span>  
 <span data-ttu-id="f9157-137">A seguir está uma listagem completa do código para este exemplo.</span><span class="sxs-lookup"><span data-stu-id="f9157-137">The following is a complete listing of the code for this example.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.ServiceModel;  
using System.ServiceModel.Web;  
using System.ServiceModel.Description;  
using System.IO;  
using System.Net;  
  
namespace ReceiveRawData  
{  
    [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    public class RawDataService : IReceiveData  
    {  
        public void UploadFile(string fileName, Stream fileContents)  
        {  
            byte[] buffer = new byte[10000];  
            int bytesRead, totalBytesRead = 0;  
            do  
            {  
                bytesRead = fileContents.Read(buffer, 0, buffer.Length);  
                totalBytesRead += bytesRead;  
            } while (bytesRead > 0);  
            Console.WriteLine("Service: Received file {0} with {1} bytes", fileName, totalBytesRead);  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
            ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
            host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            host.Open();  
            Console.WriteLine("Host opened");  
  
            HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
            req.Method = "POST";  
            req.ContentType = "text/plain";  
            Stream reqStream = req.GetRequestStream();  
            byte[] fileToSend = new byte[12345];  
            for (int i = 0; i < fileToSend.Length; i++)  
            {  
                fileToSend[i] = (byte)('a' + (i % 26));  
            }  
            reqStream.Write(fileToSend, 0, fileToSend.Length);  
            reqStream.Close();  
            HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
            Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
            host.Close();  
  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f9157-138">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="f9157-138">Compiling the Code</span></span>  
  
- <span data-ttu-id="f9157-139">Ao compilar o ServiceModel e referência de código de ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f9157-139">When compiling the code reference System.ServiceModel.dll and System.ServiceModel.Web.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9157-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9157-140">See also</span></span>

- [<span data-ttu-id="f9157-141">UriTemplate e UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="f9157-141">UriTemplate and UriTemplateTable</span></span>](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)
- [<span data-ttu-id="f9157-142">Modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="f9157-142">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="f9157-143">Visão geral do modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="f9157-143">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
