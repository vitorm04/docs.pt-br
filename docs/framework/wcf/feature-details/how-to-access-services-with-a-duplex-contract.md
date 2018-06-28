---
title: 'Como: acessar serviços com um contrato duplex'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
ms.openlocfilehash: 6675da079b343b1b80477c65260ee8a1f44df72a
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027896"
---
# <a name="how-to-access-services-with-a-duplex-contract"></a><span data-ttu-id="337ad-102">Como: acessar serviços com um contrato duplex</span><span class="sxs-lookup"><span data-stu-id="337ad-102">How to: Access services with a duplex contract</span></span>

<span data-ttu-id="337ad-103">Um recurso do Windows Communication Foundation (WCF) é a capacidade de criar um serviço que usa um padrão de mensagens duplex.</span><span class="sxs-lookup"><span data-stu-id="337ad-103">One feature of Windows Communication Foundation (WCF) is the ability to create a service that uses a duplex messaging pattern.</span></span> <span data-ttu-id="337ad-104">Esse padrão permite que um serviço para se comunicar com o cliente por meio de um retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="337ad-104">This pattern allows a service to communicate with the client through a callback.</span></span> <span data-ttu-id="337ad-105">Este tópico mostra as etapas para criar um cliente do WCF em uma classe de cliente que implementa a interface de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="337ad-105">This topic shows the steps to create a WCF client in a client class that implements the callback interface.</span></span>

<span data-ttu-id="337ad-106">Uma associação dupla expõe o endereço IP do cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="337ad-106">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="337ad-107">O cliente deve usar a segurança para garantir que ele se conecta apenas para serviços relações de confiança.</span><span class="sxs-lookup"><span data-stu-id="337ad-107">The client should use security to ensure that it connects only to services it trusts.</span></span>

<span data-ttu-id="337ad-108">Para obter um tutorial sobre como criar um serviço WCF básico e um cliente, consulte [Tutorial de Introdução](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="337ad-108">For a tutorial on creating a basic WCF service and client, see [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>

## <a name="to-access-a-duplex-service"></a><span data-ttu-id="337ad-109">Para acessar um serviço duplex</span><span class="sxs-lookup"><span data-stu-id="337ad-109">To access a duplex service</span></span>

1. <span data-ttu-id="337ad-110">Crie um serviço que contém duas interfaces.</span><span class="sxs-lookup"><span data-stu-id="337ad-110">Create a service that contains two interfaces.</span></span> <span data-ttu-id="337ad-111">É a primeira interface para o serviço, o segundo é para o retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="337ad-111">The first interface is for the service, the second is for the callback.</span></span> <span data-ttu-id="337ad-112">Para obter mais informações sobre como criar um serviço duplex, consulte [como: criar um contrato Duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="337ad-112">For more information about creating a duplex service, see [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>

2. <span data-ttu-id="337ad-113">Execute o serviço.</span><span class="sxs-lookup"><span data-stu-id="337ad-113">Run the service.</span></span>

3. <span data-ttu-id="337ad-114">Use o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar contratos (interfaces) para o cliente.</span><span class="sxs-lookup"><span data-stu-id="337ad-114">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate contracts (interfaces) for the client.</span></span> <span data-ttu-id="337ad-115">Para obter informações sobre como fazer isso, consulte [como: criar um cliente](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="337ad-115">For information about how to do this, see  [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>

4. <span data-ttu-id="337ad-116">Implemente a interface de retorno de chamada na classe do cliente, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="337ad-116">Implement the callback interface in the client class, as shown in the following example.</span></span>

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
            Console.Writeline("Equation({0})", equation)
        End Sub
    End Class
    ```

5. <span data-ttu-id="337ad-117">Crie uma instância da classe <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="337ad-117">Create an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="337ad-118">O construtor requer uma instância da classe do cliente.</span><span class="sxs-lookup"><span data-stu-id="337ad-118">The constructor requires an instance of the client class.</span></span>

    ```csharp
    InstanceContext site = new InstanceContext(new CallbackHandler());
    ```

    ```vb
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())
    ```

6. <span data-ttu-id="337ad-119">Criar uma instância do cliente WCF usando o construtor que requer um <xref:System.ServiceModel.InstanceContext> objeto.</span><span class="sxs-lookup"><span data-stu-id="337ad-119">Create an instance of the WCF client using the constructor that requires an <xref:System.ServiceModel.InstanceContext> object.</span></span> <span data-ttu-id="337ad-120">O segundo parâmetro do construtor é o nome de um ponto de extremidade encontrado no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="337ad-120">The second parameter of the constructor is the name of an endpoint found in the configuration file.</span></span>

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. <span data-ttu-id="337ad-121">Chame os métodos do cliente WCF conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="337ad-121">Call the methods of the WCF client as required.</span></span>

## <a name="example"></a><span data-ttu-id="337ad-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="337ad-122">Example</span></span>

<span data-ttu-id="337ad-123">O exemplo de código a seguir demonstra como criar uma classe de cliente que acessa um contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="337ad-123">The following code example demonstrates how to create a client class that accesses a duplex contract.</span></span>

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a><span data-ttu-id="337ad-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="337ad-124">See also</span></span>

[<span data-ttu-id="337ad-125">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="337ad-125">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
[<span data-ttu-id="337ad-126">Como criar um contrato duplex</span><span class="sxs-lookup"><span data-stu-id="337ad-126">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
[<span data-ttu-id="337ad-127">Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="337ad-127">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
[<span data-ttu-id="337ad-128">Como criar um cliente</span><span class="sxs-lookup"><span data-stu-id="337ad-128">How to: Create a Client</span></span>](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
[<span data-ttu-id="337ad-129">Como usar o ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="337ad-129">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
