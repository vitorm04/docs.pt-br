---
title: 'Tutorial: Implementar um contrato de serviço da Windows Communication Foundation'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: debdeeac7064f5bae21622b2d9de84a4d8a0e66f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184063"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>Tutorial: Implementar um contrato de serviço da Windows Communication Foundation

Este tutorial descreve a segunda das cinco tarefas necessárias para criar um aplicativo básico da Windows Communication Foundation (WCF). Para obter uma visão geral dos tutoriais, consulte [Tutorial: Comece com os aplicativos da Windows Communication Foundation](getting-started-tutorial.md).

O próximo passo para criar um aplicativo WCF é adicionar código para implementar a interface de serviço WCF que você criou na etapa anterior. Nesta etapa, você cria `CalculatorService` uma classe nomeada que `ICalculator` implementa a interface definida pelo usuário. Cada método no código a seguir chama uma operação de calculadora e grava texto no console para testá-lo.

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
>
> - Adicionar código para implementar o contrato de serviço WCF.
> - Compile a solução.

## <a name="add-code-to-implement-the-wcf-service-contract"></a>Adicionar código para implementar o contrato de serviço WCF

Em **GettingStartedLib,** abra o arquivo **Service1.cs** ou **Service1.vb** e substitua seu código pelo seguinte código:

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
    public class CalculatorService : ICalculator
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            // Code added to write output to the console window.
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
}
```

```vb
Imports System.ServiceModel

Namespace GettingStartedLib

    Public Class CalculatorService
        Implements ICalculator

        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
            Dim result As Double = n1 + n2
            ' Code added to write output to the console window.
            Console.WriteLine("Received Add({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result
        End Function

        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
            Dim result As Double = n1 - n2
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
            Dim result As Double = n1 * n2
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
            Dim result As Double = n1 / n2
            Console.WriteLine("Received Divide({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function
    End Class
End Namespace
```

## <a name="edit-appconfig"></a>Editar App.config

Editar **App.config** em **GettingStartedLib** para refletir as alterações feitas no código.

- Para projetos Visuais C#:
  - Alterar linha 14 para`<service name="GettingStartedLib.CalculatorService">`
  - Mudar linha 17 para`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Alterar linha 22 para`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

- Para projetos do Visual Basic:
  - Alterar linha 14 para`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`
  - Mudar linha 17 para`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Alterar linha 22 para`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`

## <a name="compile-the-code"></a>Compilar o código

Construa a solução para verificar se não há erros de compilação. Se você estiver usando o Visual Studio, no menu **Build** selecione **Build Solution** (ou **pressione Ctrl**+**Shift**+**B**).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu a:
> [!div class="checklist"]
>
> - Adicionar código para implementar o contrato de serviço WCF.
> - Compile a solução.

Avance para o próximo tutorial para saber como executar o serviço WCF.

> [!div class="nextstepaction"]
> [Tutorial: Hospede e execute um serviço básico do WCF](how-to-host-and-run-a-basic-wcf-service.md)
