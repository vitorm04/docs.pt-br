---
title: Como utilizar o cliente do Windows Communication Foundation
ms.date: 09/14/2018
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 12e911fb899cb85121c129b762828cdda01e64f1
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46580207"
---
# <a name="how-to-use-a-windows-communication-foundation-client"></a>Como utilizar o cliente do Windows Communication Foundation

Esta é a última das seis tarefas necessárias para criar um aplicativo básico do Windows Communication Foundation (WCF). Para obter uma visão geral de todas as seis tarefas, confira o tópico [Tutorial de introdução](../../../docs/framework/wcf/getting-started-tutorial.md).

Depois que um proxy do Windows Communication Foundation (WCF) foi criado e configurado, uma instância do cliente pode ser criada e o aplicativo cliente pode ser compilado e usado para se comunicar com o serviço WCF. Este tópico descreve procedimentos para instanciar e usar um cliente WCF. Este procedimento faz três coisas:

1.  Cria uma instância de um cliente do WCF.

2.  Chama as operações de serviço do proxy gerado.

3.  Fecha o cliente depois que a chamada da operação é concluída.

## <a name="use-a-windows-communication-foundation-client"></a>Usar um cliente do Windows Communication Foundation

Abra o arquivo Program.cs ou Program. vb do projeto GettingStartedClient e substitua o código existente pelo código a seguir:

```csharp
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

```vb
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

Observe que o `using` ou `Imports` instrução que importa o `GettingStartedClient.ServiceReference1`. Este importa o código gerado pelo **adicionar referência de serviço** no Visual Studio. O código instancia o proxy do WCF e, em seguida, chama cada uma das operações de serviço expostas pelo serviço de Calculadora, fecha o proxy e será encerrado.

Agora você concluiu o tutorial. É definido um contrato de serviço, implementado o contrato de serviço, gerado de um proxy do WCF, configurado um aplicativo de cliente do WCF e usado, em seguida, o proxy para chamar operações de serviço. Para testar o aplicativo, primeiro execute GettingStartedHost para iniciar o serviço e, em seguida, executar GettingStartedClient.

A saída de um GettingStartedHost deve ter esta aparência:

```text
The service is ready.Press <ENTER> to terminate service.Received Add(100,15.99)Return: 115.99Received Subtract(145,76.54)Return: 68.46Received Multiply(9,81.25)Return: 731.25Received Divide(22,7)Return: 3.14285714285714
```

A saída de GettingStartedClient deve ter esta aparência:

```text
Add(100,15.99) = 115.99Subtract(145,76.54) = 68.46Multiply(9,81.25) = 731.25Divide(22,7) = 3.14285714285714Press <ENTER> to terminate client.
```

## <a name="see-also"></a>Consulte também

- [Compilando clientes](../../../docs/framework/wcf/building-clients.md)
- [Como criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [Tutorial de Introdução](../../../docs/framework/wcf/getting-started-tutorial.md)
- [Programação básica do WCF](../../../docs/framework/wcf/basic-wcf-programming.md)
- [Como criar um contrato duplex](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [Como acessar serviços com um contrato Duplex](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Introdução](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [Auto-hospedagem](../../../docs/framework/wcf/samples/self-host.md)