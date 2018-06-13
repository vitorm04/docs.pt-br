---
title: Como configurar um cliente do WCF para interoperar com serviços WSE3.0
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: e30403f9c97f31e93c22a9658ffb74d4d02a49ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490637"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a><span data-ttu-id="3b665-102">Como configurar um cliente do WCF para interoperar com serviços WSE3.0</span><span class="sxs-lookup"><span data-stu-id="3b665-102">How to: Configure a WCF Client to interoperate with WSE3.0 Services</span></span>
<span data-ttu-id="3b665-103">Os clientes do Windows Communication Foundation (WCF) são compatíveis com o nível de transmissão com 3.0 de aprimoramentos de serviços Web para serviços do Microsoft .NET (WSE) quando os clientes do WCF são configurados para usar a versão de agosto de 2004 da especificação WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="3b665-103">Windows Communication Foundation (WCF) clients are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) services when WCF clients are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a><span data-ttu-id="3b665-104">Para configurar um cliente WCF para interoperar com um serviço Web do WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="3b665-104">To configure a WCF client to interoperate with a WSE 3.0 Web service</span></span>  
  
1.  <span data-ttu-id="3b665-105">Execute o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para criar um cliente WCF para o serviço Web do WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="3b665-105">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a WCF client for the WSE 3.0 Web service.</span></span>  
  
     <span data-ttu-id="3b665-106">Para um serviço Web de WSE, uma classe de cliente do WCF é criada.</span><span class="sxs-lookup"><span data-stu-id="3b665-106">For a WSE Web service, a WCF client class is created.</span></span>  
  
     <span data-ttu-id="3b665-107">Para obter detalhes sobre a criação de um cliente do WCF, consulte o [como: criar um cliente](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="3b665-107">For details about creating a WCF client, see the [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="3b665-108">Crie uma classe que representa uma associação que pode se comunicar com serviços WSE 3.0 Web.</span><span class="sxs-lookup"><span data-stu-id="3b665-108">Create a class that represents a binding that can communicate with WSE 3.0 Web services.</span></span>  
  
     <span data-ttu-id="3b665-109">A seguinte classe faz parte do [interoperar com WSE](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) exemplo.</span><span class="sxs-lookup"><span data-stu-id="3b665-109">The following class is part of the [Interoperating with WSE](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) sample.</span></span>  
  
    1.  <span data-ttu-id="3b665-110">Crie uma classe que derive da classe <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="3b665-110">Create a class that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         <span data-ttu-id="3b665-111">O exemplo de código a seguir cria uma classe denominada `WseHttpBinding` que deriva de <xref:System.ServiceModel.Channels.Binding> classe.</span><span class="sxs-lookup"><span data-stu-id="3b665-111">The following code example creates a class named `WseHttpBinding` that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  <span data-ttu-id="3b665-112">Adicione propriedades à classe que especificam a declaração completa de WSE, se as chaves derivadas são necessárias, se sessões seguras são usadas, se as confirmações de assinatura são necessárias e as configurações de proteção de mensagem.</span><span class="sxs-lookup"><span data-stu-id="3b665-112">Add properties to the class that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings.</span></span>  
  
         <span data-ttu-id="3b665-113">O exemplo de código a seguir define `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` propriedades que especificam a declaração completa de WSE, se as chaves derivadas são necessárias, se sessões seguras são usadas, se confirmações de assinatura são necessárias e as configurações de proteção de mensagem respectivamente.</span><span class="sxs-lookup"><span data-stu-id="3b665-113">The following code example defines `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` properties that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings, respectively.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  <span data-ttu-id="3b665-114">Substituir o <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> método para definir as propriedades de associação.</span><span class="sxs-lookup"><span data-stu-id="3b665-114">Override the <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> method to set the binding properties.</span></span>  
  
         <span data-ttu-id="3b665-115">O exemplo de código a seguir especifica o transporte, a codificação de mensagem e as configurações de proteção de mensagem, fazendo com que os valores da `SecurityAssertion` e `MessageProtectionOrder` propriedades.</span><span class="sxs-lookup"><span data-stu-id="3b665-115">The following code example specifies the transport, message encoding, and message protection settings by getting the values of the `SecurityAssertion` and `MessageProtectionOrder` properties.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  <span data-ttu-id="3b665-116">No código do aplicativo cliente, adicione código para definir as propriedades de associação.</span><span class="sxs-lookup"><span data-stu-id="3b665-116">In the client application code, add code to set the binding properties.</span></span>  
  
     <span data-ttu-id="3b665-117">O exemplo de código a seguir especifica que o cliente WCF deve usar autenticação e proteção de mensagem, conforme definido pelo WSE 3.0 `AnonymousForCertificate` asserção de segurança completa.</span><span class="sxs-lookup"><span data-stu-id="3b665-117">The following code example specifies that the WCF client must use message protection and authentication as defined by the WSE 3.0 `AnonymousForCertificate` turnkey security assertion.</span></span> <span data-ttu-id="3b665-118">Além disso, sessões seguras e chaves derivadas são necessárias.</span><span class="sxs-lookup"><span data-stu-id="3b665-118">Additionally, secure sessions and derived keys are required.</span></span>  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="3b665-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3b665-119">Example</span></span>  
 <span data-ttu-id="3b665-120">O exemplo de código a seguir define uma associação personalizada que expõe propriedades que correspondem às propriedades de uma asserção de segurança completa de WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="3b665-120">The following code example defines a custom binding that exposes properties that correspond to the properties of a WSE 3.0 turnkey security assertion.</span></span> <span data-ttu-id="3b665-121">A associação personalizada, que é chamada de `WseHttpBinding`, em seguida, é usado para especificar as propriedades de associação para um cliente do WCF.</span><span class="sxs-lookup"><span data-stu-id="3b665-121">The custom binding, which is named `WseHttpBinding`, is then used to specify the binding properties for a WCF client.</span></span>  
  
  
[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="3b665-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b665-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 [<span data-ttu-id="3b665-123">Interoperando com WSE</span><span class="sxs-lookup"><span data-stu-id="3b665-123">Interoperating with WSE</span></span>](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)
