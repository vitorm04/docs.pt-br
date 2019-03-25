---
title: 'Tutorial: Implementar um contrato de serviço do Windows Communication Foundation'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: fcf96af11bae701585acd92001c8000125858449
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410076"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="1fbf9-102">Tutorial: Implementar um contrato de serviço do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="1fbf9-102">Tutorial: Implement a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="1fbf9-103">Este tutorial descreve o segundo de cinco tarefas necessárias para criar um aplicativo básico do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1fbf9-103">This tutorial describes the second of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="1fbf9-104">Para obter uma visão geral dos tutoriais, consulte [Tutorial: Introdução a aplicativos do Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="1fbf9-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="1fbf9-105">A próxima etapa para a criação de um aplicativo WCF é adicionar código para implementar a interface do serviço WCF que você criou na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="1fbf9-105">The next step for creating a WCF application is to add code to implement the WCF service interface that you created in the previous step.</span></span> <span data-ttu-id="1fbf9-106">Nesta etapa, você cria uma classe chamada `CalculatorService` que implementa o definido pelo usuário `ICalculator` interface.</span><span class="sxs-lookup"><span data-stu-id="1fbf9-106">In this step, you create a class named `CalculatorService` that implements the user-defined `ICalculator` interface.</span></span> <span data-ttu-id="1fbf9-107">Cada método no código a seguir chama uma operação de Calculadora e grava o texto no console para testá-lo.</span><span class="sxs-lookup"><span data-stu-id="1fbf9-107">Each method in the following code calls a calculator operation and writes text to the console to test it.</span></span> 

<span data-ttu-id="1fbf9-108">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="1fbf9-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="1fbf9-109">Adicione código para implementar o contrato de serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="1fbf9-109">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="1fbf9-110">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="1fbf9-110">Build the solution.</span></span>

## <a name="add-code-to-implement-the-wcf-service-contract"></a><span data-ttu-id="1fbf9-111">Adicione código para implementar o contrato de serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="1fbf9-111">Add code to implement the WCF service contract</span></span>

<span data-ttu-id="1fbf9-112">Na **GettingStartedLib**, abra o **Service1.cs** ou **Service1.vb** de arquivo e substitua seu código com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="1fbf9-112">In **GettingStartedLib**, open the **Service1.cs** or **Service1.vb** file and replace its code with the following code:</span></span>

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

## <a name="edit-appconfig"></a><span data-ttu-id="1fbf9-113">Edit App.config</span><span class="sxs-lookup"><span data-stu-id="1fbf9-113">Edit App.config</span></span>

<span data-ttu-id="1fbf9-114">Edite **App. config** na **GettingStartedLib** para refletir as alterações feitas no código.</span><span class="sxs-lookup"><span data-stu-id="1fbf9-114">Edit **App.config** in **GettingStartedLib** to reflect the changes you made to the code.</span></span>
   - <span data-ttu-id="1fbf9-115">Para o Visual C# projetos:</span><span class="sxs-lookup"><span data-stu-id="1fbf9-115">For Visual C# projects:</span></span>
       - <span data-ttu-id="1fbf9-116">Altere a linha 14 para `<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="1fbf9-116">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
       - <span data-ttu-id="1fbf9-117">Altere a linha 17 para `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="1fbf9-117">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
       - <span data-ttu-id="1fbf9-118">Altere a linha 22 para `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="1fbf9-118">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

   - <span data-ttu-id="1fbf9-119">Para projetos do Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="1fbf9-119">For Visual Basic projects:</span></span>
       - <span data-ttu-id="1fbf9-120">Altere a linha 14 para `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="1fbf9-120">Change line 14 to `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span></span>
       - <span data-ttu-id="1fbf9-121">Altere a linha 17 para `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="1fbf9-121">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
       - <span data-ttu-id="1fbf9-122">Altere a linha 22 para `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="1fbf9-122">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span></span>


## <a name="compile-the-code"></a><span data-ttu-id="1fbf9-123">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="1fbf9-123">Compile the code</span></span>

<span data-ttu-id="1fbf9-124">Compile a solução para verificar se que não existem erros de compilação.</span><span class="sxs-lookup"><span data-stu-id="1fbf9-124">Build the solution to verify there aren't any compilation errors.</span></span> <span data-ttu-id="1fbf9-125">Se você estiver usando o Visual Studio, o **Build** menu, selecione **compilar solução** (ou pressione **Ctrl**+**Shift** + **B**).</span><span class="sxs-lookup"><span data-stu-id="1fbf9-125">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="1fbf9-126">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="1fbf9-126">Next steps</span></span>

<span data-ttu-id="1fbf9-127">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="1fbf9-127">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="1fbf9-128">Adicione código para implementar o contrato de serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="1fbf9-128">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="1fbf9-129">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="1fbf9-129">Build the solution.</span></span>

<span data-ttu-id="1fbf9-130">Avance para o próximo tutorial para aprender a executar o serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="1fbf9-130">Advance to the next tutorial to learn how to run the WCF service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1fbf9-131">Tutorial: Hospedar e executar um serviço WCF básico</span><span class="sxs-lookup"><span data-stu-id="1fbf9-131">Tutorial: Host and run a basic WCF service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)
