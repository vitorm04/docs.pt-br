---
title: Criando serviços interoperáveis de perfil básico de WS-I 1.1
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: 06a59c7457c0367d421cb46e33cb67f8fa039c7d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65879192"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="2cb70-102">Criando serviços interoperáveis de perfil básico de WS-I 1.1</span><span class="sxs-lookup"><span data-stu-id="2cb70-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="2cb70-103">Para configurar um ponto de extremidade de serviço do WCF para interoperabilidade com clientes de serviço Web do ASP.NET:</span><span class="sxs-lookup"><span data-stu-id="2cb70-103">To configure a WCF service endpoint to be interoperable with ASP.NET Web service clients:</span></span>  
  
- <span data-ttu-id="2cb70-104">Use o <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> tipo como o tipo de associação para o ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="2cb70-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
- <span data-ttu-id="2cb70-105">Não use o retorno de chamada e recursos de contrato de sessão ou comportamentos de transação em seu ponto de extremidade de serviço</span><span class="sxs-lookup"><span data-stu-id="2cb70-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
 <span data-ttu-id="2cb70-106">Opcionalmente, você pode habilitar o suporte para HTTPS e autenticação de cliente de nível de transporte na associação.</span><span class="sxs-lookup"><span data-stu-id="2cb70-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
 <span data-ttu-id="2cb70-107">Os seguintes recursos do <xref:System.ServiceModel.BasicHttpBinding> classe precisar de funcionalidade além do WS-I Basic Profile 1.1:</span><span class="sxs-lookup"><span data-stu-id="2cb70-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
- <span data-ttu-id="2cb70-108">Codificação de mensagem (MTOM Transmission Optimization Mechanism) mensagem controlada pela <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="2cb70-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="2cb70-109">Deixe essa propriedade em seu valor padrão, que é <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> para não usar o MTOM.</span><span class="sxs-lookup"><span data-stu-id="2cb70-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
- <span data-ttu-id="2cb70-110">Controlado por segurança da mensagem o <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> valor fornece suporte a WS-Security em conformidade com WS-I Basic Security Profile 1.0.</span><span class="sxs-lookup"><span data-stu-id="2cb70-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="2cb70-111">Deixe essa propriedade em seu valor padrão, que é <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> para não usar WS-Security.</span><span class="sxs-lookup"><span data-stu-id="2cb70-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
 <span data-ttu-id="2cb70-112">Para disponibilizar os metadados para um serviço WCF ao ASP.NET, use as ferramentas de geração de cliente de serviço Web: [Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [ferramenta de descoberta de serviços da Web (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)e o `Add Web Reference` recurso no Visual Studio; você deve habilitar a publicação de metadados.</span><span class="sxs-lookup"><span data-stu-id="2cb70-112">To make the metadata for a WCF service available to ASP.NET, use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Web Services Discovery Tool (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29), and the `Add Web Reference` feature in Visual Studio; you must enable metadata publication.</span></span> <span data-ttu-id="2cb70-113">Para obter mais informações, consulte [publicando pontos de extremidade de metadados](../../../docs/framework/wcf/publishing-metadata-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="2cb70-113">For more information, see [Publishing Metadata Endpoints](../../../docs/framework/wcf/publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cb70-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2cb70-114">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="2cb70-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="2cb70-115">Description</span></span>  
 <span data-ttu-id="2cb70-116">O exemplo de código a seguir demonstra como adicionar um ponto de extremidade do WCF que é compatível com clientes de serviço Web do ASP.NET em código e, como alternativa, em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2cb70-116">The following example code demonstrates how to add a WCF endpoint that is compatible with ASP.NET Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2cb70-117">Código</span><span class="sxs-lookup"><span data-stu-id="2cb70-117">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2cb70-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2cb70-118">See also</span></span>

- [<span data-ttu-id="2cb70-119">Interoperabilidade com serviços Web do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2cb70-119">Interoperability with ASP.NET Web Services</span></span>](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
