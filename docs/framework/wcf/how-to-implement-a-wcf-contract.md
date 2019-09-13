---
title: 'Tutorial: Implementar um contrato de serviço de Windows Communication Foundation'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: 05923dc0a2223da5e5fcda483abc1ee1dd2d643f
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928703"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>Tutorial: Implementar um contrato de serviço de Windows Communication Foundation

Este tutorial descreve a segunda das cinco tarefas necessárias para criar um aplicativo de Windows Communication Foundation básico (WCF). Para obter uma visão geral dos tutoriais, [consulte o tutorial: Introdução aos aplicativos](getting-started-tutorial.md)Windows Communication Foundation.

A próxima etapa para criar um aplicativo WCF é adicionar código para implementar a interface de serviço do WCF que você criou na etapa anterior. Nesta etapa, você cria uma classe chamada `CalculatorService` que implementa a interface definida pelo `ICalculator` usuário. Cada método no código a seguir chama uma operação de calculadora e grava o texto no console do para testá-lo. 

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
>
> - Adicione o código para implementar o contrato de serviço do WCF.
> - Compile a solução.

## <a name="add-code-to-implement-the-wcf-service-contract"></a>Adicionar código para implementar o contrato de serviço do WCF

No **GettingStartedLib**, abra o arquivo **Service1.cs** ou **Service1. vb** e substitua seu código pelo código a seguir:

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

## <a name="edit-appconfig"></a>Editar app. config

Edite **app. config** em **GettingStartedLib** para refletir as alterações feitas no código.

- Para projetos C# visuais:
  - Altere a linha 14 para`<service name="GettingStartedLib.CalculatorService">`
  - Altere a linha 17 para`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Altere a linha 22 para`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

- Para projetos do Visual Basic:
  - Altere a linha 14 para`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`
  - Altere a linha 17 para`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Altere a linha 22 para`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`

## <a name="compile-the-code"></a>Compilar o código

Compile a solução para verificar se não há erros de compilação. Se você estiver usando o Visual Studio, no **menu Compilar** , selecione **Compilar solução** (ou pressione **Ctrl**+**Shift**+**B**).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como:
> [!div class="checklist"]
>
> - Adicione o código para implementar o contrato de serviço do WCF.
> - Compile a solução.

Avance para o próximo tutorial para aprender a executar o serviço WCF.

> [!div class="nextstepaction"]
> [Tutorial: Hospedar e executar um serviço WCF básico](how-to-host-and-run-a-basic-wcf-service.md)
