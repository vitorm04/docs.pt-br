---
title: Como acessar serviços com um contrato duplex
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
ms.openlocfilehash: bc42792b827b49265a0b1addf959de2fa1a041e3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597209"
---
# <a name="how-to-access-services-with-a-duplex-contract"></a><span data-ttu-id="7380c-102">Como acessar serviços com um contrato duplex</span><span class="sxs-lookup"><span data-stu-id="7380c-102">How to: Access services with a duplex contract</span></span>

<span data-ttu-id="7380c-103">Um recurso do Windows Communication Foundation (WCF) é a capacidade de criar um serviço que usa um padrão de mensagens duplex.</span><span class="sxs-lookup"><span data-stu-id="7380c-103">One feature of Windows Communication Foundation (WCF) is the ability to create a service that uses a duplex messaging pattern.</span></span> <span data-ttu-id="7380c-104">Esse padrão permite que um serviço se comunique com o cliente por meio de um retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="7380c-104">This pattern allows a service to communicate with the client through a callback.</span></span> <span data-ttu-id="7380c-105">Este tópico mostra as etapas para criar um cliente WCF em uma classe de cliente que implementa a interface de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="7380c-105">This topic shows the steps to create a WCF client in a client class that implements the callback interface.</span></span>

<span data-ttu-id="7380c-106">Uma associação dupla expõe o endereço IP do cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="7380c-106">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="7380c-107">O cliente deve usar a segurança para garantir que ele se conecte somente aos serviços que confia.</span><span class="sxs-lookup"><span data-stu-id="7380c-107">The client should use security to ensure that it connects only to services it trusts.</span></span>

<span data-ttu-id="7380c-108">Para obter um tutorial sobre como criar um serviço e cliente WCF básicos, consulte [introdução tutorial](../getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="7380c-108">For a tutorial on creating a basic WCF service and client, see [Getting Started Tutorial](../getting-started-tutorial.md).</span></span>

## <a name="to-access-a-duplex-service"></a><span data-ttu-id="7380c-109">Para acessar um serviço duplex</span><span class="sxs-lookup"><span data-stu-id="7380c-109">To access a duplex service</span></span>

1. <span data-ttu-id="7380c-110">Crie um serviço que contenha duas interfaces.</span><span class="sxs-lookup"><span data-stu-id="7380c-110">Create a service that contains two interfaces.</span></span> <span data-ttu-id="7380c-111">A primeira interface é para o serviço, a segunda é para o retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="7380c-111">The first interface is for the service, the second is for the callback.</span></span> <span data-ttu-id="7380c-112">Para obter mais informações sobre como criar um serviço duplex, consulte [como: criar um contrato duplex](how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="7380c-112">For more information about creating a duplex service, see [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>

2. <span data-ttu-id="7380c-113">Executar o serviço.</span><span class="sxs-lookup"><span data-stu-id="7380c-113">Run the service.</span></span>

3. <span data-ttu-id="7380c-114">Use a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar contratos (interfaces) para o cliente.</span><span class="sxs-lookup"><span data-stu-id="7380c-114">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate contracts (interfaces) for the client.</span></span> <span data-ttu-id="7380c-115">Para obter informações sobre como fazer isso, consulte [como: criar um cliente](../how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="7380c-115">For information about how to do this, see  [How to: Create a Client](../how-to-create-a-wcf-client.md).</span></span>

4. <span data-ttu-id="7380c-116">Implemente a interface de retorno de chamada na classe Client, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7380c-116">Implement the callback interface in the client class, as shown in the following example.</span></span>

    ```csharp
    public class CallbackHandler : ICalculatorDuplexCallback
    {
        public void Result(double result)
        {
            Console.WriteLine("Result ({0})", result);
        }
        public void Equation(string equation)
        {
            Console.WriteLine("Equation({0})", equation);
        }
    }
    ```

    ```vb
    Public Class CallbackHandler
    Implements ICalculatorDuplexCallback
       Public Sub Result (ByVal result As Double)
          Console.WriteLine("Result ({0})", result)
       End Sub
        Public Sub Equation(ByVal equation As String)
            Console.WriteLine("Equation({0})", equation)
        End Sub
    End Class
    ```

5. <span data-ttu-id="7380c-117">Criar uma instância da classe <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="7380c-117">Create an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="7380c-118">O construtor requer uma instância da classe Client.</span><span class="sxs-lookup"><span data-stu-id="7380c-118">The constructor requires an instance of the client class.</span></span>

    ```csharp
    InstanceContext site = new InstanceContext(new CallbackHandler());
    ```

    ```vb
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())
    ```

6. <span data-ttu-id="7380c-119">Crie uma instância do cliente WCF usando o construtor que requer um <xref:System.ServiceModel.InstanceContext> objeto.</span><span class="sxs-lookup"><span data-stu-id="7380c-119">Create an instance of the WCF client using the constructor that requires an <xref:System.ServiceModel.InstanceContext> object.</span></span> <span data-ttu-id="7380c-120">O segundo parâmetro do construtor é o nome de um ponto de extremidade encontrado no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="7380c-120">The second parameter of the constructor is the name of an endpoint found in the configuration file.</span></span>

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. <span data-ttu-id="7380c-121">Chame os métodos do cliente WCF, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="7380c-121">Call the methods of the WCF client as required.</span></span>

## <a name="example"></a><span data-ttu-id="7380c-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7380c-122">Example</span></span>

<span data-ttu-id="7380c-123">O exemplo de código a seguir demonstra como criar uma classe de cliente que acessa um contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="7380c-123">The following code example demonstrates how to create a client class that accesses a duplex contract.</span></span>

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a><span data-ttu-id="7380c-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7380c-124">See also</span></span>

- [<span data-ttu-id="7380c-125">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="7380c-125">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)
- [<span data-ttu-id="7380c-126">Como criar um contrato duplex</span><span class="sxs-lookup"><span data-stu-id="7380c-126">How to: Create a Duplex Contract</span></span>](how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="7380c-127">Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="7380c-127">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="7380c-128">Como criar um cliente</span><span class="sxs-lookup"><span data-stu-id="7380c-128">How to: Create a Client</span></span>](../how-to-create-a-wcf-client.md)
- [<span data-ttu-id="7380c-129">Como usar o ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="7380c-129">How to: Use the ChannelFactory</span></span>](how-to-use-the-channelfactory.md)
