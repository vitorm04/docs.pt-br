---
title: 'Tutorial: Usar um cliente do Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: fa9aa3612a8dc72623fc4ea4b1ea337ac773fa26
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169957"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a>Tutorial: Usar um cliente do Windows Communication Foundation

Este tutorial descreve o último de cinco tarefas necessárias para criar um aplicativo básico do Windows Communication Foundation (WCF). Para obter uma visão geral dos tutoriais, consulte [Tutorial: Introdução a aplicativos do Windows Communication Foundation](getting-started-tutorial.md).

Depois que você criou e configurou um proxy do Windows Communication Foundation (WCF), você cria uma instância do cliente e compila o aplicativo cliente. Em seguida, usá-lo para se comunicar com o serviço WCF. 

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
> - Adicione código para usar o cliente do WCF.
> - Teste o cliente do WCF.

## <a name="add-code-to-use-the-wcf-client"></a>Adicionar código para usar o cliente do WCF

O código do cliente faz as seguintes etapas:
- Cria uma instância de cliente do WCF.
- Chama as operações de serviço do proxy gerado.
- Fecha o cliente após a chamada da operação.

Abra o **Program.cs** ou **Module1.vb** arquivo da **GettingStartedClient** do projeto e substitua seu código com o código a seguir:

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

            // Step 3: Close the client to gracefully close the connection and clean up resources.
            Console.WriteLine("\nPress <Enter> to terminate the client.");
            Console.ReadLine();
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
Imports GettingStartedClient.ServiceReference1

Module Module1

    Sub Main()
        ' Step 1: Create an instance of the WCF proxy.
        Dim Client As New CalculatorClient()

        ' Step 2: Call the service operations.
        ' Call the Add service operation.
        Dim value1 As Double = 100D
        Dim value2 As Double = 15.99D
        Dim result As Double = Client.Add(value1, value2)
        Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

        ' Call the Subtract service operation.
        value1 = 145D
        value2 = 76.54D
        result = Client.Subtract(value1, value2)
        Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

        ' Call the Multiply service operation.
        value1 = 9D
        value2 = 81.25D
        result = Client.Multiply(value1, value2)
        Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

        ' Call the Divide service operation.
        value1 = 22D
        value2 = 7D
        result = Client.Divide(value1, value2)
        Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

        ' Step 3: Close the client to gracefully close the connection and clean up resources.
        Console.WriteLine()
        Console.WriteLine("Press <Enter> to terminate the client.")
        Console.ReadLine()
        Client.Close()

    End Sub

End Module
```

Observe que o `using` (para Visual C#) ou `Imports` (para Visual Basic) instrução importa `GettingStartedClient.ServiceReference1`. Essa instrução importa o código que o Visual Studio gerado com o **adicionar referência de serviço** função. O código instancia o proxy do WCF e chama cada uma das operações de serviço que expõe o serviço da Calculadora. Em seguida, ele fecha o proxy e encerra o programa.

## <a name="test-the-wcf-client"></a>Testar o cliente do WCF

### <a name="test-the-application-from-visual-studio"></a>Testar o aplicativo do Visual Studio

1. Salve e compile a solução.

2. Selecione o **GettingStartedLib** pasta e, em seguida, selecione **definir como projeto de inicialização** no menu de atalho.

3. Partir **projetos de inicialização**, selecione **GettingStartedLib** na lista suspensa, selecione **execute** ou pressione **F5**.

### <a name="test-the-application-from-a-command-prompt"></a>Testar o aplicativo em um prompt de comando

1. Abra um prompt de comando como administrador e, em seguida, navegue até seu diretório de solução do Visual Studio. 

2. Para iniciar o serviço: Insira *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.

3. Para iniciar o cliente: Abra outro prompt de comando, navegue até seu diretório de solução do Visual Studio e insira *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.

   *GettingStartedHost.exe* produz a seguinte saída:

   ```text
   The service is ready.
   Press <Enter> to terminate the service.

   Received Add(100,15.99)
   Return: 115.99
   Received Subtract(145,76.54)
   Return: 68.46
   Received Multiply(9,81.25)
   Return: 731.25
   Received Divide(22,7)
   Return: 3.14285714285714
   ```

   *GettingStartedClient.exe* produz a seguinte saída:

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a>Próximas etapas

Agora você concluiu todas as tarefas no WCF tutorial de Introdução. Neste tutorial, você aprendeu como:

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
> - Adicione código para usar o cliente do WCF.
> - Teste o cliente do WCF.

Se você tiver problemas ou erros em qualquer uma das etapas, siga as etapas do artigo de solução de problemas para corrigi-los.

> [!div class="nextstepaction"]
> [Solucionar problemas de Get iniciado com tutoriais do WCF](troubleshooting-the-getting-started-tutorial.md)
