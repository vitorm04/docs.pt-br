---
title: "Como criar um serviço que retorna dados arbitrários utilizando o Modelo de programação HTTP Web do Windows Communication Foundation (WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 829e9f2bcf909bee41f53b4b7cabbb0803e77963
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a><span data-ttu-id="73de7-102">Como criar um serviço que retorna dados arbitrários utilizando o Modelo de programação HTTP Web do Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="73de7-102">How to: Create a Service That Returns Arbitrary Data Using The WCF Web HTTP Programming Model</span></span>
<span data-ttu-id="73de7-103">Às vezes, os desenvolvedores devem ter controle total sobre como os dados são retornados de uma operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="73de7-103">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="73de7-104">Esse é o caso quando uma operação de serviço deve retornar dados em um formato sem suporte pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="73de7-104">This is the case when a service operation must return data in a format not supported by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="73de7-105">Este tópico discute o uso de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de programação HTTP WEB para criar um serviço.</span><span class="sxs-lookup"><span data-stu-id="73de7-105">This topic discusses using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP Programming Model to create such a service.</span></span> <span data-ttu-id="73de7-106">Esse serviço tem uma operação que retorna um fluxo.</span><span class="sxs-lookup"><span data-stu-id="73de7-106">This service has one operation that returns a stream.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="73de7-107">Para implementar o contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="73de7-107">To implement the service contract</span></span>  
  
1.  <span data-ttu-id="73de7-108">Defina o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="73de7-108">Define the service contract.</span></span> <span data-ttu-id="73de7-109">O contrato é chamado `IImageServer` e tem um método chamado `GetImage` que retorna um <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="73de7-109">The contract is called `IImageServer` and has one method called `GetImage` that returns a <xref:System.IO.Stream>.</span></span>  
  
    ```  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     <span data-ttu-id="73de7-110">Como o método retorna um <xref:System.IO.Stream>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pressupõe que a operação tem controle total sobre os bytes retornados da operação de serviço e se aplica a nenhuma formatação para os dados que são retornados.</span><span class="sxs-lookup"><span data-stu-id="73de7-110">Because the method returns a <xref:System.IO.Stream>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] assumes that the operation has complete control over the bytes that are returned from the service operation and it applies no formatting to the data that is returned.</span></span>  
  
2.  <span data-ttu-id="73de7-111">Implemente o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="73de7-111">Implement the service contract.</span></span> <span data-ttu-id="73de7-112">O contrato tem apenas uma operação (`GetImage`).</span><span class="sxs-lookup"><span data-stu-id="73de7-112">The contract has only one operation (`GetImage`).</span></span> <span data-ttu-id="73de7-113">Este método gera um bitmap e, em seguida, salvá-lo para um <xref:System.IO.MemoryStream> no formato. jpg.</span><span class="sxs-lookup"><span data-stu-id="73de7-113">This method generates a bitmap and then save it to a <xref:System.IO.MemoryStream> in .jpg format.</span></span> <span data-ttu-id="73de7-114">A operação, em seguida, retorna o fluxo ao chamador.</span><span class="sxs-lookup"><span data-stu-id="73de7-114">The operation then returns that stream to the caller.</span></span>  
  
    ```  
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
  
     <span data-ttu-id="73de7-115">Observe que a segunda à última linha de código:`WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span><span class="sxs-lookup"><span data-stu-id="73de7-115">Notice the second to last line of code: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span></span>  
  
     <span data-ttu-id="73de7-116">Isso define o cabeçalho de tipo de conteúdo para `"image/jpeg"`.</span><span class="sxs-lookup"><span data-stu-id="73de7-116">This sets the content type header to `"image/jpeg"`.</span></span> <span data-ttu-id="73de7-117">Embora este exemplo mostra como retornar um arquivo. jpg, ele pode ser modificado para retornar qualquer tipo de dados que é necessários, em qualquer formato.</span><span class="sxs-lookup"><span data-stu-id="73de7-117">Although this sample shows how to return a .jpg file, it can be modified to return any type of data that is required, in any format.</span></span> <span data-ttu-id="73de7-118">A operação deve recuperar ou gerar os dados e, em seguida, gravá-la em um fluxo.</span><span class="sxs-lookup"><span data-stu-id="73de7-118">The operation must retrieve or generate the data and then write it to a stream.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="73de7-119">Para hospedar o serviço</span><span class="sxs-lookup"><span data-stu-id="73de7-119">To host the service</span></span>  
  
1.  <span data-ttu-id="73de7-120">Crie um aplicativo de console para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="73de7-120">Create a console application to host the service.</span></span>  
  
    ```  
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }   
    }  
    ```  
  
2.  <span data-ttu-id="73de7-121">Criar uma variável para conter o endereço base para o serviço dentro do `Main` método.</span><span class="sxs-lookup"><span data-stu-id="73de7-121">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3.  <span data-ttu-id="73de7-122">Criar um <xref:System.ServiceModel.ServiceHost> instância para o serviço especificando a classe de serviço e o endereço base.</span><span class="sxs-lookup"><span data-stu-id="73de7-122">Create a <xref:System.ServiceModel.ServiceHost> instance for the service specifying the service class and the base address.</span></span>  
  
    ```  
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4.  <span data-ttu-id="73de7-123">Adicionar um ponto de extremidade usando o <xref:System.ServiceModel.WebHttpBinding> e <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="73de7-123">Add an endpoint using the <xref:System.ServiceModel.WebHttpBinding> and the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5.  <span data-ttu-id="73de7-124">Abra o host do serviço.</span><span class="sxs-lookup"><span data-stu-id="73de7-124">Open the service host.</span></span>  
  
    ```  
    host.Open()  
    ```  
  
6.  <span data-ttu-id="73de7-125">Aguarde até que o usuário pressiona ENTER para encerrar o serviço.</span><span class="sxs-lookup"><span data-stu-id="73de7-125">Wait until the user presses ENTER to terminate the service.</span></span>  
  
    ```  
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a><span data-ttu-id="73de7-126">Para chamar o serviço bruto usando o Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="73de7-126">To call the raw service using Internet Explorer</span></span>  
  
1.  <span data-ttu-id="73de7-127">Executar o serviço, você verá a seguinte saída do serviço.</span><span class="sxs-lookup"><span data-stu-id="73de7-127">Run the service, you should see the following output from the service.</span></span> `Service is running Press ENTER to close the host`  
  
2.  <span data-ttu-id="73de7-128">Abra o Internet Explorer e digite `http://localhost:8000/Service/GetImage?width=50&height=40` você verá um retângulo amarelo com uma linha azul diagonal por meio do centro.</span><span class="sxs-lookup"><span data-stu-id="73de7-128">Open Internet Explorer and type in `http://localhost:8000/Service/GetImage?width=50&height=40` you should see a yellow rectangle with a blue diagonal line through the center.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73de7-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="73de7-129">Example</span></span>  
 <span data-ttu-id="73de7-130">A seguir está uma listagem completa do código para este tópico.</span><span class="sxs-lookup"><span data-stu-id="73de7-130">The following is a complete listing of the code for this topic.</span></span>  
  
```  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="73de7-131">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="73de7-131">Compiling the Code</span></span>  
  
-   <span data-ttu-id="73de7-132">Quando estiver compilando o código de exemplo referência a System.ServiceModel.dll e System.</span><span class="sxs-lookup"><span data-stu-id="73de7-132">When compiling the sample code reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73de7-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73de7-133">See Also</span></span>  
 [<span data-ttu-id="73de7-134">Modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="73de7-134">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
