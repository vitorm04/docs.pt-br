---
title: Criando serviços interoperáveis de perfil básico de WS-I 1.1
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: fd7828cccb1a19a17e899525d863021d3670fbdd
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389758"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="573f6-102">Criando serviços interoperáveis de perfil básico de WS-I 1.1</span><span class="sxs-lookup"><span data-stu-id="573f6-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="573f6-103">Para configurar um ponto final de serviço WCF para ser interoperável com ASP.NET clientes de serviço web:</span><span class="sxs-lookup"><span data-stu-id="573f6-103">To configure a WCF service endpoint to be interoperable with ASP.NET Web service clients:</span></span>  
  
- <span data-ttu-id="573f6-104">Use <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> o tipo como o tipo de vinculação para o ponto final do serviço.</span><span class="sxs-lookup"><span data-stu-id="573f6-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
- <span data-ttu-id="573f6-105">Não use recursos de contrato de chamada e sessão ou comportamentos de transação no ponto final do serviço</span><span class="sxs-lookup"><span data-stu-id="573f6-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
<span data-ttu-id="573f6-106">Você pode habilitar opcionalmente o suporte para autenticação de cliente HTTPS e nível de transporte na vinculação.</span><span class="sxs-lookup"><span data-stu-id="573f6-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
<span data-ttu-id="573f6-107">Os seguintes <xref:System.ServiceModel.BasicHttpBinding> recursos da classe exigem funcionalidade além do Perfil Básico WS-I 1.1:</span><span class="sxs-lookup"><span data-stu-id="573f6-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
- <span data-ttu-id="573f6-108">Codificação de mensagens MTOM (Message Transmission <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> Optimization Mechanism, mecanismo de otimização de transmissão de mensagens) controlada pela propriedade.</span><span class="sxs-lookup"><span data-stu-id="573f6-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="573f6-109">Deixe esta propriedade em seu <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> valor padrão, que é não usar MTOM.</span><span class="sxs-lookup"><span data-stu-id="573f6-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
- <span data-ttu-id="573f6-110">A segurança de <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> mensagens controlada pelo valor fornece suporte ao WS-Security compatível com o Perfil básico de segurança 1.0 do WS-I.</span><span class="sxs-lookup"><span data-stu-id="573f6-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="573f6-111">Deixe esta propriedade em seu <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> valor padrão, que é não usar o WS-Security.</span><span class="sxs-lookup"><span data-stu-id="573f6-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
<span data-ttu-id="573f6-112">Para disponibilizar os metadados de um serviço WCF para ASP.NET, use as ferramentas de geração de clientes de [serviços web: Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Web Services Discovery Tool (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)e o recurso **Add Web Reference** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="573f6-112">To make the metadata for a WCF service available to ASP.NET, use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Web Services Discovery Tool (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29), and the **Add Web Reference** feature in Visual Studio.</span></span> <span data-ttu-id="573f6-113">Habilite a publicação de metadados.</span><span class="sxs-lookup"><span data-stu-id="573f6-113">Enable metadata publication.</span></span> <span data-ttu-id="573f6-114">Para obter mais informações, consulte [''Pontos finais de metadados'](publishing-metadata-endpoints.md)de publicação .</span><span class="sxs-lookup"><span data-stu-id="573f6-114">For more information, see [Publishing Metadata Endpoints](publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="573f6-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="573f6-115">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="573f6-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="573f6-116">Description</span></span>  
 <span data-ttu-id="573f6-117">O código de exemplo a seguir demonstra como adicionar um ponto final WCF compatível com ASP.NET clientes de serviço web em código e, alternativamente, em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="573f6-117">The following example code demonstrates how to add a WCF endpoint that is compatible with ASP.NET Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="573f6-118">Código</span><span class="sxs-lookup"><span data-stu-id="573f6-118">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="573f6-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="573f6-119">See also</span></span>

- [<span data-ttu-id="573f6-120">Interoperabilidade com serviços Web do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="573f6-120">Interoperability with ASP.NET Web Services</span></span>](./feature-details/interop-with-aspnet-web-services.md)
