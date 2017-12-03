---
title: Como utilizar o cliente do Windows Communication Foundation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF clients [WCF], using
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
caps.latest.revision: "38"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0d9d2fb363aa753edc6d2d4002a948fbb35b75ad
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-a-windows-communication-foundation-client"></a>Como utilizar o cliente do Windows Communication Foundation
Este é o último dos seis tarefas necessárias para criar um basic [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplicativo. Para obter uma visão geral de todos os seis das tarefas, consulte o [Tutorial de Introdução](../../../docs/framework/wcf/getting-started-tutorial.md) tópico.  
  
 Uma vez um [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] proxy foi criado e configurado, pode ser criada uma instância do cliente e o aplicativo cliente pode ser compilado e usado para se comunicar com o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service. Este tópico descreve procedimentos para criar uma instância e usar um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] cliente. Este procedimento faz três coisas:  
  
1.  Cria um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] cliente.  
  
2.  Chama as operações de serviço do proxy gerado.  
  
3.  Fecha o cliente após a conclusão da chamada da operação.  
  
### <a name="to-use-a-windows-communication-foundation-client"></a>Para usar um cliente Windows Communication Foundation  
  
1.  Abra o arquivo Program.cs. vb ou do projeto GettingStartedClient e substitua o código existente pelo seguinte código:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using GettingStartedClient.ServiceReference1;  
  
    namespace GettingStartedClient  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                //Step 1: Create an instance of the WCF proxy.  
                CalculatorClient client = new CalculatorClient();  
  
                // Step 2: Call the service operations.  
                // Call the Add service operation.  
                double value1 = 100.00D;  
                double value2 = 15.99D;  
                double result = client.Add(value1, value2);  
                Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
                // Call the Subtract service operation.  
                value1 = 145.00D;  
                value2 = 76.54D;  
                result = client.Subtract(value1, value2);  
                Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
                // Call the Multiply service operation.  
                value1 = 9.00D;  
                value2 = 81.25D;  
                result = client.Multiply(value1, value2);  
                Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
                // Call the Divide service operation.  
                value1 = 22.00D;  
                value2 = 7.00D;  
                result = client.Divide(value1, value2);  
                Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
                //Step 3: Closing the client gracefully closes the connection and cleans up resources.  
                client.Close();  
            }  
        }  
    }  
    ```  
  
    ```  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.Text  
    Imports System.ServiceModel  
    Imports GettingStartedClientVB2.ServiceReference1  
  
    Module Module1  
  
        Sub Main()  
            ' Step 1: Create an instance of the WCF proxy  
            Dim Client As New CalculatorClient()  
  
            'Step 2: Call the service operations.  
            'Call the Add service operation.  
            Dim value1 As Double = 100D  
            Dim value2 As Double = 15.99D  
            Dim result As Double = Client.Add(value1, value2)  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Subtract service operation.  
            value1 = 145D  
            value2 = 76.54D  
            result = Client.Subtract(value1, value2)  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Multiply service operation.  
            value1 = 9D  
            value2 = 81.25D  
            result = Client.Multiply(value1, value2)  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Divide service operation.  
            value1 = 22D  
            value2 = 7D  
            result = Client.Divide(value1, value2)  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)  
  
            ' Step 3: Closing the client gracefully closes the connection and cleans up resources.  
            Client.Close()  
  
            Console.WriteLine()  
            Console.WriteLine("Press <ENTER> to terminate client.")  
            Console.ReadLine()  
  
        End Sub  
  
    End Module  
    ```  
  
     Observe a instrução usando ou importações que importa o GettingStartedClient.ServiceReference1. Isso importa o código gerado pelo Adicionar referência de serviço no Visual Studio. O código instancia o proxy do WCF e, em seguida, chama cada uma das operações de serviço expostas pelo serviço de cálculo, fecha o proxy e termina.  
  
 Agora você concluiu o tutorial. É definido um contrato de serviço, implementado o contrato de serviço, gerado um proxy WCF, configurado um aplicativo cliente WCF e usado, em seguida, o proxy para chamar operações de serviço. Para testar o aplicativo, primeiro execute GettingStartedHost para iniciar o serviço e, em seguida, executar GettingStartedClient. A saída de GettingStartedHost deve ter esta aparência:  
  
```Output  
The service is ready.Press <ENTER> to terminate service.Received Add(100,15.99)Return: 115.99Received Subtract(145,76.54)Return: 68.46Received Multiply(9,81.25)Return: 731.25Received Divide(22,7)Return: 3.14285714285714  
```  
  
 A saída de GettingStartedClient deve ter esta aparência:  
  
```Output  
Add(100,15.99) = 115.99Subtract(145,76.54) = 68.46Multiply(9,81.25) = 731.25Divide(22,7) = 3.14285714285714Press <ENTER> to terminate client.  
```  
  
## <a name="see-also"></a>Consulte também  
 [Building Clients](../../../docs/framework/wcf/building-clients.md) (Compilando clientes)  
 [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md) (Como criar um cliente)  
 [Tutorial de Introdução](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Basic WCF Programming](../../../docs/framework/wcf/basic-wcf-programming.md) (Programação básica do WCF)  
 [Como: criar um contrato Duplex](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [Como: acessar serviços com um contrato Duplex](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [Introdução](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Hospedagem interna](../../../docs/framework/wcf/samples/self-host.md)
