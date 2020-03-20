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
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="e283a-102">Tutorial: Implementar um contrato de serviço da Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="e283a-102">Tutorial: Implement a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="e283a-103">Este tutorial descreve a segunda das cinco tarefas necessárias para criar um aplicativo básico da Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e283a-103">This tutorial describes the second of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="e283a-104">Para obter uma visão geral dos tutoriais, consulte [Tutorial: Comece com os aplicativos da Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="e283a-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="e283a-105">O próximo passo para criar um aplicativo WCF é adicionar código para implementar a interface de serviço WCF que você criou na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="e283a-105">The next step for creating a WCF application is to add code to implement the WCF service interface that you created in the previous step.</span></span> <span data-ttu-id="e283a-106">Nesta etapa, você cria `CalculatorService` uma classe nomeada que `ICalculator` implementa a interface definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="e283a-106">In this step, you create a class named `CalculatorService` that implements the user-defined `ICalculator` interface.</span></span> <span data-ttu-id="e283a-107">Cada método no código a seguir chama uma operação de calculadora e grava texto no console para testá-lo.</span><span class="sxs-lookup"><span data-stu-id="e283a-107">Each method in the following code calls a calculator operation and writes text to the console to test it.</span></span>

<span data-ttu-id="e283a-108">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="e283a-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="e283a-109">Adicionar código para implementar o contrato de serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="e283a-109">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="e283a-110">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="e283a-110">Build the solution.</span></span>

## <a name="add-code-to-implement-the-wcf-service-contract"></a><span data-ttu-id="e283a-111">Adicionar código para implementar o contrato de serviço WCF</span><span class="sxs-lookup"><span data-stu-id="e283a-111">Add code to implement the WCF service contract</span></span>

<span data-ttu-id="e283a-112">Em **GettingStartedLib,** abra o arquivo **Service1.cs** ou **Service1.vb** e substitua seu código pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="e283a-112">In **GettingStartedLib**, open the **Service1.cs** or **Service1.vb** file and replace its code with the following code:</span></span>

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

## <a name="edit-appconfig"></a><span data-ttu-id="e283a-113">Editar App.config</span><span class="sxs-lookup"><span data-stu-id="e283a-113">Edit App.config</span></span>

<span data-ttu-id="e283a-114">Editar **App.config** em **GettingStartedLib** para refletir as alterações feitas no código.</span><span class="sxs-lookup"><span data-stu-id="e283a-114">Edit **App.config** in **GettingStartedLib** to reflect the changes you made to the code.</span></span>

- <span data-ttu-id="e283a-115">Para projetos Visuais C#:</span><span class="sxs-lookup"><span data-stu-id="e283a-115">For Visual C# projects:</span></span>
  - <span data-ttu-id="e283a-116">Alterar linha 14 para`<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="e283a-116">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="e283a-117">Mudar linha 17 para`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="e283a-117">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="e283a-118">Alterar linha 22 para`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="e283a-118">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

- <span data-ttu-id="e283a-119">Para projetos do Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="e283a-119">For Visual Basic projects:</span></span>
  - <span data-ttu-id="e283a-120">Alterar linha 14 para`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="e283a-120">Change line 14 to `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="e283a-121">Mudar linha 17 para`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="e283a-121">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="e283a-122">Alterar linha 22 para`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="e283a-122">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="e283a-123">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="e283a-123">Compile the code</span></span>

<span data-ttu-id="e283a-124">Construa a solução para verificar se não há erros de compilação.</span><span class="sxs-lookup"><span data-stu-id="e283a-124">Build the solution to verify there aren't any compilation errors.</span></span> <span data-ttu-id="e283a-125">Se você estiver usando o Visual Studio, no menu **Build** selecione **Build Solution** (ou **pressione Ctrl**+**Shift**+**B**).</span><span class="sxs-lookup"><span data-stu-id="e283a-125">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="e283a-126">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="e283a-126">Next steps</span></span>

<span data-ttu-id="e283a-127">Neste tutorial, você aprendeu a:</span><span class="sxs-lookup"><span data-stu-id="e283a-127">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="e283a-128">Adicionar código para implementar o contrato de serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="e283a-128">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="e283a-129">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="e283a-129">Build the solution.</span></span>

<span data-ttu-id="e283a-130">Avance para o próximo tutorial para saber como executar o serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="e283a-130">Advance to the next tutorial to learn how to run the WCF service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e283a-131">Tutorial: Hospede e execute um serviço básico do WCF</span><span class="sxs-lookup"><span data-stu-id="e283a-131">Tutorial: Host and run a basic WCF service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)
