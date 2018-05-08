---
title: Como criar um serviço que retorna dados arbitrários utilizando o Modelo de programação HTTP Web do Windows Communication Foundation (WCF)
ms.date: 03/30/2017
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
ms.openlocfilehash: 763d62750380f025ae369e1e917b46d4e51874e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a>Como criar um serviço que retorna dados arbitrários utilizando o Modelo de programação HTTP Web do Windows Communication Foundation (WCF)
Às vezes, os desenvolvedores devem ter controle total sobre como os dados são retornados de uma operação de serviço. Esse é o caso quando uma operação de serviço deve retornar dados em um formato sem suporte pelo WCF. Este tópico discute como usar o modelo de programação WCF WEB HTTP para criar um serviço. Esse serviço tem uma operação que retorna um fluxo.  
  
### <a name="to-implement-the-service-contract"></a>Para implementar o contrato de serviço  
  
1.  Defina o contrato de serviço. O contrato é chamado `IImageServer` e tem um método chamado `GetImage` que retorna um <xref:System.IO.Stream>.  
  
    ```  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     Como o método retorna um <xref:System.IO.Stream>, WCF presume que a operação tem controle total sobre os bytes retornados da operação de serviço e se aplica a nenhuma formatação para os dados que são retornados.  
  
2.  Implemente o contrato de serviço. O contrato tem apenas uma operação (`GetImage`). Este método gera um bitmap e, em seguida, salvá-lo para um <xref:System.IO.MemoryStream> no formato. jpg. A operação, em seguida, retorna o fluxo ao chamador.  
  
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
  
     Observe que a segunda à última linha de código: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`  
  
     Isso define o cabeçalho de tipo de conteúdo para `"image/jpeg"`. Embora este exemplo mostra como retornar um arquivo. jpg, ele pode ser modificado para retornar qualquer tipo de dados que é necessários, em qualquer formato. A operação deve recuperar ou gerar os dados e, em seguida, gravá-la em um fluxo.  
  
### <a name="to-host-the-service"></a>Para hospedar o serviço  
  
1.  Crie um aplicativo de console para hospedar o serviço.  
  
    ```  
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }   
    }  
    ```  
  
2.  Criar uma variável para conter o endereço base para o serviço dentro do `Main` método.  
  
    ```  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3.  Criar um <xref:System.ServiceModel.ServiceHost> instância para o serviço especificando a classe de serviço e o endereço base.  
  
    ```  
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4.  Adicionar um ponto de extremidade usando o <xref:System.ServiceModel.WebHttpBinding> e <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
    ```  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5.  Abra o host do serviço.  
  
    ```  
    host.Open()  
    ```  
  
6.  Aguarde até que o usuário pressiona ENTER para encerrar o serviço.  
  
    ```  
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a>Para chamar o serviço bruto usando o Internet Explorer  
  
1.  Executar o serviço, você verá a seguinte saída do serviço. `Service is running Press ENTER to close the host`  
  
2.  Abra o Internet Explorer e digite `http://localhost:8000/Service/GetImage?width=50&height=40` você verá um retângulo amarelo com uma linha azul diagonal por meio do centro.  
  
## <a name="example"></a>Exemplo  
 A seguir está uma listagem completa do código para este tópico.  
  
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
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Quando estiver compilando o código de exemplo referência a System.ServiceModel.dll e System.  
  
## <a name="see-also"></a>Consulte também  
 [Modelo de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
