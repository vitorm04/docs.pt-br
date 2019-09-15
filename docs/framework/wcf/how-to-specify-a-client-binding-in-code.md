---
title: 'Como: especificar uma associação de cliente no código'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: 37769a84ca623e2f7f246d36180aa17537e90bfa
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990228"
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="27303-102">Como: especificar uma associação de cliente no código</span><span class="sxs-lookup"><span data-stu-id="27303-102">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="27303-103">Neste exemplo, um cliente é criado para usar um serviço de calculadora e a associação para esse cliente é especificada imperativamente no código.</span><span class="sxs-lookup"><span data-stu-id="27303-103">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="27303-104">O cliente acessa o `CalculatorService`, que implementa a `ICalculator` interface, e o serviço e o cliente usam a <xref:System.ServiceModel.BasicHttpBinding> classe.</span><span class="sxs-lookup"><span data-stu-id="27303-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="27303-105">Este procedimento pressupõe que o serviço de calculadora está em execução.</span><span class="sxs-lookup"><span data-stu-id="27303-105">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="27303-106">Para obter informações sobre como criar o serviço [, consulte Como: Especifique uma associação de serviço na](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)configuração.</span><span class="sxs-lookup"><span data-stu-id="27303-106">For information about building the service, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="27303-107">Ele também usa a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) fornece para gerar automaticamente os componentes do cliente.</span><span class="sxs-lookup"><span data-stu-id="27303-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="27303-108">A ferramenta gera o código do cliente para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="27303-108">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="27303-109">O cliente é criado em duas partes.</span><span class="sxs-lookup"><span data-stu-id="27303-109">The client is built in two parts.</span></span> <span data-ttu-id="27303-110">Svcutil. exe gera o `ClientCalculator` que implementa a `ICalculator` interface.</span><span class="sxs-lookup"><span data-stu-id="27303-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="27303-111">Esse aplicativo cliente é então construído pela construção de uma instância do `ClientCalculator` e, em seguida, pela especificação da associação e do endereço do serviço no código.</span><span class="sxs-lookup"><span data-stu-id="27303-111">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="27303-112">Para a cópia de origem deste exemplo, consulte o exemplo de [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="27303-112">For the source copy of this example, see the [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="27303-113">Para especificar uma associação personalizada no código</span><span class="sxs-lookup"><span data-stu-id="27303-113">To specify a custom binding in code</span></span>  
  
1. <span data-ttu-id="27303-114">Use svcutil. exe da linha de comando para gerar código de metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="27303-114">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. <span data-ttu-id="27303-115">O cliente gerado contém a `ICalculator` interface que define o contrato de serviço que a implementação do cliente deve satisfazer.</span><span class="sxs-lookup"><span data-stu-id="27303-115">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. <span data-ttu-id="27303-116">O cliente gerado também contém a implementação do `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="27303-116">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. <span data-ttu-id="27303-117">Crie uma instância do `ClientCalculator` que usa a <xref:System.ServiceModel.BasicHttpBinding> classe em um aplicativo cliente e, em seguida, chame as operações de serviço no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="27303-117">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. <span data-ttu-id="27303-118">Compile e execute o cliente.</span><span class="sxs-lookup"><span data-stu-id="27303-118">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27303-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27303-119">See also</span></span>

- [<span data-ttu-id="27303-120">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="27303-120">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
