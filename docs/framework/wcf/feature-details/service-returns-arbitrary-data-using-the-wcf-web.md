---
title: Como criar um serviço que retorna dados arbitrários utilizando o Modelo de programação HTTP Web do Windows Communication Foundation (WCF)
ms.date: 03/30/2017
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
ms.openlocfilehash: c85ab6725876a2d523a18c817ce3fd89f0d2285a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184477"
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a><span data-ttu-id="1153f-102">Como criar um serviço que retorna dados arbitrários utilizando o Modelo de programação HTTP Web do Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="1153f-102">How to: Create a Service That Returns Arbitrary Data Using The WCF Web HTTP Programming Model</span></span>
<span data-ttu-id="1153f-103">Às vezes, os desenvolvedores devem ter controle total de como os dados são retornados de uma operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="1153f-103">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="1153f-104">Este é o caso quando uma operação de serviço deve retornar dados em um formato não suportado pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="1153f-104">This is the case when a service operation must return data in a format not supported by WCF.</span></span> <span data-ttu-id="1153f-105">Este tópico discute o uso do WCF WEB HTTP Programming Model para criar tal serviço.</span><span class="sxs-lookup"><span data-stu-id="1153f-105">This topic discusses using the WCF WEB HTTP Programming Model to create such a service.</span></span> <span data-ttu-id="1153f-106">Este serviço tem uma operação que retorna um fluxo.</span><span class="sxs-lookup"><span data-stu-id="1153f-106">This service has one operation that returns a stream.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="1153f-107">Para implementar o contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="1153f-107">To implement the service contract</span></span>  
  
1. <span data-ttu-id="1153f-108">Defina o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="1153f-108">Define the service contract.</span></span> <span data-ttu-id="1153f-109">O contrato `IImageServer` é chamado e `GetImage` tem <xref:System.IO.Stream>um método chamado que retorna um .</span><span class="sxs-lookup"><span data-stu-id="1153f-109">The contract is called `IImageServer` and has one method called `GetImage` that returns a <xref:System.IO.Stream>.</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     <span data-ttu-id="1153f-110">Como o método <xref:System.IO.Stream>retorna a , o WCF assume que a operação tem controle total sobre os bytes que são devolvidos da operação de serviço e não aplica formatação aos dados que são devolvidos.</span><span class="sxs-lookup"><span data-stu-id="1153f-110">Because the method returns a <xref:System.IO.Stream>, WCF assumes that the operation has complete control over the bytes that are returned from the service operation and it applies no formatting to the data that is returned.</span></span>  
  
2. <span data-ttu-id="1153f-111">Implemente o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="1153f-111">Implement the service contract.</span></span> <span data-ttu-id="1153f-112">O contrato tem apenas`GetImage`uma operação ( .</span><span class="sxs-lookup"><span data-stu-id="1153f-112">The contract has only one operation (`GetImage`).</span></span> <span data-ttu-id="1153f-113">Este método gera um bitmap e, em seguida, salvá-lo em um <xref:System.IO.MemoryStream> formato .jpg.</span><span class="sxs-lookup"><span data-stu-id="1153f-113">This method generates a bitmap and then save it to a <xref:System.IO.MemoryStream> in .jpg format.</span></span> <span data-ttu-id="1153f-114">A operação então retorna esse fluxo para o chamador.</span><span class="sxs-lookup"><span data-stu-id="1153f-114">The operation then returns that stream to the caller.</span></span>  
  
    ```csharp
    public class Service : IImageServer
    {
        public Stream GetImage(int width, int height)
        {
            Bitmap bitmap = new Bitmap(width, height);
            for (int i = 0; i < bitmap.Width; i++)
            {
                for (int j = 0; j < bitmap.Height; j++)
                {
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);
                }
            }
            MemoryStream ms = new MemoryStream();
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);
            ms.Position = 0;
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";
            return ms;
        }
    }
    ```  
  
     <span data-ttu-id="1153f-115">Observe a penúltima linha de código:`WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span><span class="sxs-lookup"><span data-stu-id="1153f-115">Notice the second to last line of code: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span></span>  
  
     <span data-ttu-id="1153f-116">Isso define o cabeçalho do tipo de conteúdo para `"image/jpeg"`.</span><span class="sxs-lookup"><span data-stu-id="1153f-116">This sets the content type header to `"image/jpeg"`.</span></span> <span data-ttu-id="1153f-117">Embora esta amostra mostre como retornar um arquivo .jpg, ele pode ser modificado para retornar qualquer tipo de dados necessários, em qualquer formato.</span><span class="sxs-lookup"><span data-stu-id="1153f-117">Although this sample shows how to return a .jpg file, it can be modified to return any type of data that is required, in any format.</span></span> <span data-ttu-id="1153f-118">A operação deve recuperar ou gerar os dados e, em seguida, gravá-los para um fluxo.</span><span class="sxs-lookup"><span data-stu-id="1153f-118">The operation must retrieve or generate the data and then write it to a stream.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="1153f-119">Para hospedar o serviço</span><span class="sxs-lookup"><span data-stu-id="1153f-119">To host the service</span></span>  
  
1. <span data-ttu-id="1153f-120">Crie um aplicativo de console para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="1153f-120">Create a console application to host the service.</span></span>  
  
    ```csharp
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }
    }  
    ```  
  
2. <span data-ttu-id="1153f-121">Crie uma variável para manter o endereço `Main` base do serviço dentro do método.</span><span class="sxs-lookup"><span data-stu-id="1153f-121">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```csharp
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. <span data-ttu-id="1153f-122">Crie <xref:System.ServiceModel.ServiceHost> uma instância para o serviço especificando a classe de serviço e o endereço base.</span><span class="sxs-lookup"><span data-stu-id="1153f-122">Create a <xref:System.ServiceModel.ServiceHost> instance for the service specifying the service class and the base address.</span></span>  
  
    ```csharp
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4. <span data-ttu-id="1153f-123">Adicione um ponto <xref:System.ServiceModel.WebHttpBinding> final <xref:System.ServiceModel.Description.WebHttpBehavior>usando o e o .</span><span class="sxs-lookup"><span data-stu-id="1153f-123">Add an endpoint using the <xref:System.ServiceModel.WebHttpBinding> and the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. <span data-ttu-id="1153f-124">Abra o host do serviço.</span><span class="sxs-lookup"><span data-stu-id="1153f-124">Open the service host.</span></span>  
  
    ```csharp  
    host.Open();  
    ```  
  
6. <span data-ttu-id="1153f-125">Aguarde até que o usuário pressione ENTER para encerrar o serviço.</span><span class="sxs-lookup"><span data-stu-id="1153f-125">Wait until the user presses ENTER to terminate the service.</span></span>  
  
    ```csharp
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a><span data-ttu-id="1153f-126">Para chamar o serviço bruto usando o Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="1153f-126">To call the raw service using Internet Explorer</span></span>  
  
1. <span data-ttu-id="1153f-127">Executar o serviço, você deve ver a saída a seguir do serviço.</span><span class="sxs-lookup"><span data-stu-id="1153f-127">Run the service, you should see the following output from the service.</span></span> `Service is running Press ENTER to close the host`  
  
2. <span data-ttu-id="1153f-128">Abra o Internet `http://localhost:8000/Service/GetImage?width=50&height=40` Explorer e digite você deve ver um retângulo amarelo com uma linha diagonal azul através do centro.</span><span class="sxs-lookup"><span data-stu-id="1153f-128">Open Internet Explorer and type in `http://localhost:8000/Service/GetImage?width=50&height=40` you should see a yellow rectangle with a blue diagonal line through the center.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1153f-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1153f-129">Example</span></span>  
 <span data-ttu-id="1153f-130">A seguir está uma lista completa do código para este tópico.</span><span class="sxs-lookup"><span data-stu-id="1153f-130">The following is a complete listing of the code for this topic.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.ServiceModel;  
using System.ServiceModel.Web;  
using System.ServiceModel.Description;  
using System.IO;  
using System.Drawing;  
  
namespace RawImageService  
{  
    // Define the service contract  
    [ServiceContract]  
    public interface IImageServer  
    {  
        [WebGet]  
        Stream GetImage(int width, int height);  
    }  
  
    // implement the service contract  
    public class Service : IImageServer  
    {  
        public Stream GetImage(int width, int height)  
        {  
            // Although this method returns a jpeg, it can be  
            // modified to return any data you want within the stream  
            Bitmap bitmap = new Bitmap(width, height);  
            for (int i = 0; i < bitmap.Width; i++)  
            {  
                for (int j = 0; j < bitmap.Height; j++)  
                {  
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);  
                }  
            }  
            MemoryStream ms = new MemoryStream();  
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);  
            ms.Position = 0;  
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";  
            return ms;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
            ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
            host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            host.Open();  
            Console.WriteLine("Service is running");  
            Console.Write("Press ENTER to close the host");  
            Console.ReadLine();  
            host.Close();  
  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1153f-131">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="1153f-131">Compiling the Code</span></span>  
  
- <span data-ttu-id="1153f-132">Ao compilar o código de exemplo de referência System.ServiceModel.dll e System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="1153f-132">When compiling the sample code reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1153f-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="1153f-133">See also</span></span>

- [<span data-ttu-id="1153f-134">Modelo de programação WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="1153f-134">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
