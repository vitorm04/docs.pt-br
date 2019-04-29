---
title: 'Tutorial: Implementar um contrato de serviço do Windows Communication Foundation'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: fa8c5457c636d7f37215f0d4b4fdbb1c96c9481e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929047"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>Tutorial: Implementar um contrato de serviço do Windows Communication Foundation

Este tutorial descreve o segundo de cinco tarefas necessárias para criar um aplicativo básico do Windows Communication Foundation (WCF). Para obter uma visão geral dos tutoriais, consulte [Tutorial: Introdução a aplicativos do Windows Communication Foundation](getting-started-tutorial.md).

A próxima etapa para a criação de um aplicativo WCF é adicionar código para implementar a interface do serviço WCF que você criou na etapa anterior. Nesta etapa, você cria uma classe chamada `CalculatorService` que implementa o definido pelo usuário `ICalculator` interface. Cada método no código a seguir chama uma operação de Calculadora e grava o texto no console para testá-lo. 

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
> - Adicione código para implementar o contrato de serviço do WCF.
> - Compile a solução.

## <a name="add-code-to-implement-the-wcf-service-contract"></a>Adicione código para implementar o contrato de serviço do WCF

Na **GettingStartedLib**, abra o **Service1.cs** ou **Service1.vb** de arquivo e substitua seu código com o código a seguir:

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

## <a name="edit-appconfig"></a>Edit App.config

Edite **App. config** na **GettingStartedLib** para refletir as alterações feitas no código.
- Para o Visual C# projetos:
  - Altere a linha 14 para `<service name="GettingStartedLib.CalculatorService">`
  - Altere a linha 17 para `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Altere a linha 22 para `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

- Para projetos do Visual Basic:
  - Altere a linha 14 para `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`
  - Altere a linha 17 para `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Altere a linha 22 para `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`

## <a name="compile-the-code"></a>Compilar o código

Compile a solução para verificar se que não existem erros de compilação. Se você estiver usando o Visual Studio, o **Build** menu, selecione **compilar solução** (ou pressione **Ctrl**+**Shift** + **B**).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como:
> [!div class="checklist"]
> - Adicione código para implementar o contrato de serviço do WCF.
> - Compile a solução.

Avance para o próximo tutorial para aprender a executar o serviço do WCF.

> [!div class="nextstepaction"]
> [Tutorial: Hospedar e executar um serviço WCF básico](how-to-host-and-run-a-basic-wcf-service.md)
