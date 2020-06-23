---
title: 'Tutorial: implementar um contrato de serviço de Windows Communication Foundation'
description: Saiba como adicionar código para implementar uma interface de serviço WCF como parte de uma série de artigos que ajudam você a começar a criar um aplicativo WCF.
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: 89f97610cccd42c2a5d298baa667327d077fd472
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244641"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="2cc7c-103">Tutorial: implementar um contrato de serviço de Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="2cc7c-103">Tutorial: Implement a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="2cc7c-104">Este tutorial descreve a segunda das cinco tarefas necessárias para criar um aplicativo de Windows Communication Foundation básico (WCF).</span><span class="sxs-lookup"><span data-stu-id="2cc7c-104">This tutorial describes the second of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="2cc7c-105">Para obter uma visão geral dos tutoriais, consulte [tutorial: introdução aos aplicativos Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="2cc7c-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="2cc7c-106">A próxima etapa para criar um aplicativo WCF é adicionar código para implementar a interface de serviço do WCF que você criou na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="2cc7c-106">The next step for creating a WCF application is to add code to implement the WCF service interface that you created in the previous step.</span></span> <span data-ttu-id="2cc7c-107">Nesta etapa, você cria uma classe chamada `CalculatorService` que implementa a interface definida pelo usuário `ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="2cc7c-107">In this step, you create a class named `CalculatorService` that implements the user-defined `ICalculator` interface.</span></span> <span data-ttu-id="2cc7c-108">Cada método no código a seguir chama uma operação de calculadora e grava o texto no console do para testá-lo.</span><span class="sxs-lookup"><span data-stu-id="2cc7c-108">Each method in the following code calls a calculator operation and writes text to the console to test it.</span></span>

<span data-ttu-id="2cc7c-109">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="2cc7c-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="2cc7c-110">Adicione o código para implementar o contrato de serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="2cc7c-110">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="2cc7c-111">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="2cc7c-111">Build the solution.</span></span>

## <a name="add-code-to-implement-the-wcf-service-contract"></a><span data-ttu-id="2cc7c-112">Adicionar código para implementar o contrato de serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="2cc7c-112">Add code to implement the WCF service contract</span></span>

<span data-ttu-id="2cc7c-113">No **GettingStartedLib**, abra o arquivo **Service1.cs** ou **Service1. vb** e substitua seu código pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="2cc7c-113">In **GettingStartedLib**, open the **Service1.cs** or **Service1.vb** file and replace its code with the following code:</span></span>

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

## <a name="edit-appconfig"></a><span data-ttu-id="2cc7c-114">Editar App.config</span><span class="sxs-lookup"><span data-stu-id="2cc7c-114">Edit App.config</span></span>

<span data-ttu-id="2cc7c-115">Edite **App.config** no **GettingStartedLib** para refletir as alterações feitas no código.</span><span class="sxs-lookup"><span data-stu-id="2cc7c-115">Edit **App.config** in **GettingStartedLib** to reflect the changes you made to the code.</span></span>

- <span data-ttu-id="2cc7c-116">Para projetos do Visual C#:</span><span class="sxs-lookup"><span data-stu-id="2cc7c-116">For Visual C# projects:</span></span>
  - <span data-ttu-id="2cc7c-117">Altere a linha 14 para`<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="2cc7c-117">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="2cc7c-118">Altere a linha 17 para`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="2cc7c-118">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="2cc7c-119">Altere a linha 22 para`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="2cc7c-119">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

- <span data-ttu-id="2cc7c-120">Para projetos do Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="2cc7c-120">For Visual Basic projects:</span></span>
  - <span data-ttu-id="2cc7c-121">Altere a linha 14 para`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="2cc7c-121">Change line 14 to `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="2cc7c-122">Altere a linha 17 para`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="2cc7c-122">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="2cc7c-123">Altere a linha 22 para`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="2cc7c-123">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="2cc7c-124">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="2cc7c-124">Compile the code</span></span>

<span data-ttu-id="2cc7c-125">Compile a solução para verificar se não há erros de compilação.</span><span class="sxs-lookup"><span data-stu-id="2cc7c-125">Build the solution to verify there aren't any compilation errors.</span></span> <span data-ttu-id="2cc7c-126">Se você estiver usando o Visual Studio, no menu **Compilar** , selecione **Compilar solução** (ou pressione **Ctrl** + **Shift** + **B**).</span><span class="sxs-lookup"><span data-stu-id="2cc7c-126">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="2cc7c-127">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="2cc7c-127">Next steps</span></span>

<span data-ttu-id="2cc7c-128">Neste tutorial, você aprendeu a:</span><span class="sxs-lookup"><span data-stu-id="2cc7c-128">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="2cc7c-129">Adicione o código para implementar o contrato de serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="2cc7c-129">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="2cc7c-130">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="2cc7c-130">Build the solution.</span></span>

<span data-ttu-id="2cc7c-131">Avance para o próximo tutorial para aprender a executar o serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="2cc7c-131">Advance to the next tutorial to learn how to run the WCF service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2cc7c-132">Tutorial: hospedar e executar um serviço WCF básico</span><span class="sxs-lookup"><span data-stu-id="2cc7c-132">Tutorial: Host and run a basic WCF service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)
