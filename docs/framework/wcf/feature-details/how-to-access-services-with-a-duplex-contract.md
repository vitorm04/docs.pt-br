---
title: "Como acessar serviços com um contrato duplex"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 425d17fa34b61985ad3600f992e028e156f6adb9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-access-services-with-a-duplex-contract"></a><span data-ttu-id="d4ba3-102">Como acessar serviços com um contrato duplex</span><span class="sxs-lookup"><span data-stu-id="d4ba3-102">How to: Access Services with a Duplex Contract</span></span>
<span data-ttu-id="d4ba3-103">Um recurso de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] é a capacidade de criar um serviço que usa um padrão de mensagens duplex.</span><span class="sxs-lookup"><span data-stu-id="d4ba3-103">One feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is the ability to create a service that uses a duplex messaging pattern.</span></span> <span data-ttu-id="d4ba3-104">Esse padrão permite que um serviço para se comunicar com o cliente por meio de um retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="d4ba3-104">This pattern allows a service to communicate with the client through a callback.</span></span> <span data-ttu-id="d4ba3-105">Este tópico mostra as etapas para criar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente em uma classe de cliente que implementa a interface de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="d4ba3-105">This topic shows the steps to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client in a client class that implements the callback interface.</span></span>  
  
 <span data-ttu-id="d4ba3-106">Uma associação dupla expõe o endereço IP do cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="d4ba3-106">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="d4ba3-107">O cliente deve usar a segurança para garantir que ele se conecta apenas para serviços relações de confiança.</span><span class="sxs-lookup"><span data-stu-id="d4ba3-107">The client should use security to ensure that it connects only to services it trusts.</span></span>  
  
 <span data-ttu-id="d4ba3-108">Para obter um tutorial sobre como criar um basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço e cliente, consulte [Tutorial de Introdução](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="d4ba3-108">For a tutorial on creating a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service and client, see [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  
  
### <a name="to-access-a-duplex-service"></a><span data-ttu-id="d4ba3-109">Para acessar um serviço duplex</span><span class="sxs-lookup"><span data-stu-id="d4ba3-109">To access a duplex service</span></span>  
  
1.  <span data-ttu-id="d4ba3-110">Crie um serviço que contém duas interfaces.</span><span class="sxs-lookup"><span data-stu-id="d4ba3-110">Create a service that contains two interfaces.</span></span> <span data-ttu-id="d4ba3-111">É a primeira interface para o serviço, o segundo é para o retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="d4ba3-111">The first interface is for the service, the second is for the callback.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="d4ba3-112">criar um serviço duplex, consulte [como: criar um contrato Duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="d4ba3-112"> creating a duplex service, see [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
2.  <span data-ttu-id="d4ba3-113">Execute o serviço.</span><span class="sxs-lookup"><span data-stu-id="d4ba3-113">Run the service.</span></span>  
  
3.  <span data-ttu-id="d4ba3-114">Use o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar contratos (interfaces) para o cliente.</span><span class="sxs-lookup"><span data-stu-id="d4ba3-114">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate contracts (interfaces) for the client.</span></span> <span data-ttu-id="d4ba3-115">Para obter informações sobre como fazer isso, consulte [como: criar um cliente](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="d4ba3-115">For information about how to do this, see  [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
4.  <span data-ttu-id="d4ba3-116">Implemente a interface de retorno de chamada na classe do cliente, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d4ba3-116">Implement the callback interface in the client class, as shown in the following example.</span></span>  
  
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
  
5.  <span data-ttu-id="d4ba3-117">Crie uma instância da classe <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="d4ba3-117">Create an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="d4ba3-118">O construtor requer uma instância da classe do cliente.</span><span class="sxs-lookup"><span data-stu-id="d4ba3-118">The constructor requires an instance of the client class.</span></span>  
  
    ```csharp  
    InstanceContext site = new InstanceContext(new CallbackHandler());  
    ```  
  
    ```vb  
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())  
    ```  
  
6.  <span data-ttu-id="d4ba3-119">Criar uma instância do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente usando o construtor que requer um <xref:System.ServiceModel.InstanceContext> objeto.</span><span class="sxs-lookup"><span data-stu-id="d4ba3-119">Create an instance of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client using the constructor that requires an <xref:System.ServiceModel.InstanceContext> object.</span></span> <span data-ttu-id="d4ba3-120">O segundo parâmetro do construtor é o nome de um ponto de extremidade encontrado no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d4ba3-120">The second parameter of the constructor is the name of an endpoint found in the configuration file.</span></span>  
  
    ```csharp  
    CalculatorDuplexClient wcfClient =   
    new CalculatorDuplexClient(site, "default")  
    ```  
  
    ```vb  
    Dim wcfClient As New CalculatorDuplexClient(site, "default")  
    ```  
  
7.  <span data-ttu-id="d4ba3-121">Chame os métodos do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="d4ba3-121">Call the methods of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client as required.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4ba3-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d4ba3-122">Example</span></span>  
 <span data-ttu-id="d4ba3-123">O exemplo de código a seguir demonstra como criar uma classe de cliente que acessa um contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="d4ba3-123">The following code example demonstrates how to create a client class that accesses a duplex contract.</span></span>  
  
 [!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
 [!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="d4ba3-124">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d4ba3-124">.NET Framework Security</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4ba3-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4ba3-125">See Also</span></span>  
 [<span data-ttu-id="d4ba3-126">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="d4ba3-126">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [<span data-ttu-id="d4ba3-127">Como criar um contrato duplex</span><span class="sxs-lookup"><span data-stu-id="d4ba3-127">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [<span data-ttu-id="d4ba3-128">Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="d4ba3-128">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="d4ba3-129">Como criar um cliente</span><span class="sxs-lookup"><span data-stu-id="d4ba3-129">How to: Create a Client</span></span>](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="d4ba3-130">Como usar o ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="d4ba3-130">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
