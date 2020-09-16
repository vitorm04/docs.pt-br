---
title: Criando serviços interoperáveis de perfil básico de WS-I 1.1
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: 5fc29432bdd55daff2d60d641a4cea4925278032
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543011"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="cbdef-102">Criando serviços interoperáveis de perfil básico de WS-I 1.1</span><span class="sxs-lookup"><span data-stu-id="cbdef-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="cbdef-103">Para configurar um ponto de extremidade de serviço WCF para ser interoperável com clientes do serviço Web ASP.NET:</span><span class="sxs-lookup"><span data-stu-id="cbdef-103">To configure a WCF service endpoint to be interoperable with ASP.NET Web service clients:</span></span>  
  
- <span data-ttu-id="cbdef-104">Use o <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> tipo como o tipo de associação para o ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="cbdef-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
- <span data-ttu-id="cbdef-105">Não usar recursos de retorno de chamada e de contrato de sessão ou comportamentos de transação em seu ponto de extremidade de serviço</span><span class="sxs-lookup"><span data-stu-id="cbdef-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
<span data-ttu-id="cbdef-106">Opcionalmente, você pode habilitar o suporte para HTTPS e autenticação de cliente de nível de transporte na associação.</span><span class="sxs-lookup"><span data-stu-id="cbdef-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
<span data-ttu-id="cbdef-107">Os seguintes recursos da <xref:System.ServiceModel.BasicHttpBinding> classe exigem funcionalidade além do WS-I Basic Profile 1,1:</span><span class="sxs-lookup"><span data-stu-id="cbdef-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
- <span data-ttu-id="cbdef-108">Codificação de mensagem MTOM (mecanismo de otimização de transmissão de mensagens) controlada pela <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="cbdef-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="cbdef-109">Deixe essa propriedade em seu valor padrão, que é <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> não usar MTOM.</span><span class="sxs-lookup"><span data-stu-id="cbdef-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
- <span data-ttu-id="cbdef-110">A segurança da mensagem controlada pelo <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> valor fornece suporte ao WS-Security com o WS-I Basic Security Profile 1,0.</span><span class="sxs-lookup"><span data-stu-id="cbdef-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="cbdef-111">Deixe essa propriedade em seu valor padrão, que é <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> para não usar o WS-Security.</span><span class="sxs-lookup"><span data-stu-id="cbdef-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
<span data-ttu-id="cbdef-112">Para disponibilizar os metadados de um serviço WCF para o ASP.NET, use a ferramenta de geração de cliente do serviço Web: [Web Services Description Language Tool (Wsdl.exe)](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100)), [Web Services Discovery Tool (Disco.exe)](/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100))e o recurso **Add Web Reference** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cbdef-112">To make the metadata for a WCF service available to ASP.NET, use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100)), [Web Services Discovery Tool (Disco.exe)](/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100)), and the **Add Web Reference** feature in Visual Studio.</span></span> <span data-ttu-id="cbdef-113">Habilitar publicação de metadados.</span><span class="sxs-lookup"><span data-stu-id="cbdef-113">Enable metadata publication.</span></span> <span data-ttu-id="cbdef-114">Para obter mais informações, consulte [publicando pontos de extremidade de metadados](publishing-metadata-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="cbdef-114">For more information, see [Publishing Metadata Endpoints](publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbdef-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cbdef-115">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="cbdef-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="cbdef-116">Description</span></span>  
 <span data-ttu-id="cbdef-117">O código de exemplo a seguir demonstra como adicionar um ponto de extremidade WCF compatível com clientes de serviço Web ASP.NET em código e, como alternativa, em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="cbdef-117">The following example code demonstrates how to add a WCF endpoint that is compatible with ASP.NET Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cbdef-118">Código</span><span class="sxs-lookup"><span data-stu-id="cbdef-118">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cbdef-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="cbdef-119">See also</span></span>

- [<span data-ttu-id="cbdef-120">Interoperabilidade com serviços Web do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="cbdef-120">Interoperability with ASP.NET Web Services</span></span>](./feature-details/interop-with-aspnet-web-services.md)
