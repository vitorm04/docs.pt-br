---
title: Como implementar um contrato de serviço do Windows Communication Foundation
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: 569de6f49b56b46ccfeb22e9f0bd25bcf339b7e0
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48037359"
---
# <a name="how-to-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="6a89f-102">Como implementar um contrato de serviço do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="6a89f-102">How to: Implement a Windows Communication Foundation Service Contract</span></span>

<span data-ttu-id="6a89f-103">Este é o segundo de seis tarefas necessárias para criar um serviço básico do Windows Communication Foundation (WCF) e um cliente que possa chamar o serviço.</span><span class="sxs-lookup"><span data-stu-id="6a89f-103">This is the second of six tasks required to create a basic Windows Communication Foundation (WCF) service and a client that can call the service.</span></span> <span data-ttu-id="6a89f-104">Para obter uma visão geral de todas as seis tarefas, consulte a [Tutorial de Introdução](../../../docs/framework/wcf/getting-started-tutorial.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="6a89f-104">For an overview of all six tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>

<span data-ttu-id="6a89f-105">A próxima etapa na criação de um aplicativo WCF é implementar a interface de serviço.</span><span class="sxs-lookup"><span data-stu-id="6a89f-105">The next step in creating a WCF application is to implement the service interface.</span></span> <span data-ttu-id="6a89f-106">Isso envolve a criação de uma classe chamada `CalculatorService` que implementa o definido pelo usuário `ICalculator` interface...</span><span class="sxs-lookup"><span data-stu-id="6a89f-106">This involves creating a class called `CalculatorService` that implements the user-defined `ICalculator` interface..</span></span>

## <a name="to-implement-a-wcf-service-contract"></a><span data-ttu-id="6a89f-107">Para implementar um contrato de serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="6a89f-107">To implement a WCF service contract</span></span>

<span data-ttu-id="6a89f-108">Abra o arquivo Service1.cs or Service1.vb e adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="6a89f-108">Open the Service1.cs or Service1.vb file and add the following code:</span></span>

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

<span data-ttu-id="6a89f-109">Cada método implementa a operação de Calculadora e grava um texto no console para facilitar os testes.</span><span class="sxs-lookup"><span data-stu-id="6a89f-109">Each method implements the calculator operation and writes some text to the console to make testing easier.</span></span>

## <a name="example"></a><span data-ttu-id="6a89f-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6a89f-110">Example</span></span>

<span data-ttu-id="6a89f-111">O código a seguir mostra a interface que define o contrato e a implementação da interface.</span><span class="sxs-lookup"><span data-stu-id="6a89f-111">The following code shows both the interface that defines the contract and the implementation of the interface.</span></span>

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
    [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
    public interface ICalculator
    {
        [OperationContract]
        double Add(double n1, double n2);
        [OperationContract]
        double Subtract(double n1, double n2);
        [OperationContract]
        double Multiply(double n1, double n2);
        [OperationContract]
        double Divide(double n1, double n2);
    }
}
```

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

    <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
    Public Interface ICalculator

        <OperationContract()> _
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
    End Interface
End Namespace
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

## <a name="compile-the-code"></a><span data-ttu-id="6a89f-112">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="6a89f-112">Compile the code</span></span>

<span data-ttu-id="6a89f-113">Compile a solução para garantir que não há nenhum erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="6a89f-113">Build the solution to ensure there are no compilation errors.</span></span> <span data-ttu-id="6a89f-114">Se você estiver usando o Visual Studio, o **Build** menu, selecione **compilar solução** (ou pressione **Ctrl**+**Shift** + **B**).</span><span class="sxs-lookup"><span data-stu-id="6a89f-114">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="6a89f-115">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="6a89f-115">Next steps</span></span>

<span data-ttu-id="6a89f-116">Agora o contrato de serviço é criado e implementado.</span><span class="sxs-lookup"><span data-stu-id="6a89f-116">Now the service contract is created and implemented.</span></span> <span data-ttu-id="6a89f-117">Na próxima etapa, você deve executar o serviço.</span><span class="sxs-lookup"><span data-stu-id="6a89f-117">In the next step, you run the service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6a89f-118">Como hospedar e executar um serviço básico</span><span class="sxs-lookup"><span data-stu-id="6a89f-118">How to: Host and Run a Basic Service</span></span>](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md)

<span data-ttu-id="6a89f-119">Para obter informações sobre solução de problemas, confira [Solução de problemas do tutorial de introdução](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="6a89f-119">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6a89f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a89f-120">See also</span></span>

- [<span data-ttu-id="6a89f-121">Introdução</span><span class="sxs-lookup"><span data-stu-id="6a89f-121">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="6a89f-122">Auto-hospedagem</span><span class="sxs-lookup"><span data-stu-id="6a89f-122">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)