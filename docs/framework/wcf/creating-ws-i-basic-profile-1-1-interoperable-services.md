---
title: Criando serviços interoperáveis de perfil básico de WS-I 1.1
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fa561e5019bcf90e93da669f93cbce51d02e89dc
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="ea30f-102">Criando serviços interoperáveis de perfil básico de WS-I 1.1</span><span class="sxs-lookup"><span data-stu-id="ea30f-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="ea30f-103">Para configurar um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ponto de extremidade de serviço para interoperabilidade com [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] clientes de serviço Web:</span><span class="sxs-lookup"><span data-stu-id="ea30f-103">To configure a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service endpoint to be interoperable with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web service clients:</span></span>  
  
-   <span data-ttu-id="ea30f-104">Use o <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> tipo como o tipo de associação para o ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="ea30f-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
-   <span data-ttu-id="ea30f-105">Não use o retorno de chamada e os recursos de contrato de sessão ou comportamentos de transação em seu ponto de extremidade de serviço</span><span class="sxs-lookup"><span data-stu-id="ea30f-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
 <span data-ttu-id="ea30f-106">Opcionalmente, você pode habilitar o suporte para HTTPS e autenticação de cliente de nível de transporte na associação.</span><span class="sxs-lookup"><span data-stu-id="ea30f-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
 <span data-ttu-id="ea30f-107">Os seguintes recursos do <xref:System.ServiceModel.BasicHttpBinding> classe exigem a funcionalidade além do WS-I Basic Profile 1.1:</span><span class="sxs-lookup"><span data-stu-id="ea30f-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
-   <span data-ttu-id="ea30f-108">Codificação de mensagens do mecanismo de otimização de transmissão (MTOM) de mensagem controlado pelo <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="ea30f-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="ea30f-109">Deixe essa propriedade em seu valor padrão, que é <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> para não usar MTOM.</span><span class="sxs-lookup"><span data-stu-id="ea30f-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
-   <span data-ttu-id="ea30f-110">Segurança controlada pelo <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> valor fornece suporte do WS-Security compatível com WS-I Basic Profile 1.0 de segurança.</span><span class="sxs-lookup"><span data-stu-id="ea30f-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="ea30f-111">Deixe essa propriedade em seu valor padrão, que é <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> para não usar WS-Security.</span><span class="sxs-lookup"><span data-stu-id="ea30f-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
 <span data-ttu-id="ea30f-112">Para tornar os metadados para um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço disponível para [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], use as ferramentas de geração de cliente de serviço Web: [Web Services Description Language Tool (Wsdl.exe)](http://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88), [(ferramenta de descoberta de serviços Web Disco.exe)](http://msdn.microsoft.com/library/acd88078-c581-42bc-94ca-6633e2851979)e o `Add Web Reference` recurso no Visual Studio; você deve habilitar a publicação de metadados.</span><span class="sxs-lookup"><span data-stu-id="ea30f-112">To make the metadata for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service available to [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](http://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88), [Web Services Discovery Tool (Disco.exe)](http://msdn.microsoft.com/library/acd88078-c581-42bc-94ca-6633e2851979), and the `Add Web Reference` feature in Visual Studio; you must enable metadata publication.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="ea30f-113"> [Publicar pontos de extremidade de metadados](../../../docs/framework/wcf/publishing-metadata-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="ea30f-113"> [Publishing Metadata Endpoints](../../../docs/framework/wcf/publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea30f-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ea30f-114">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ea30f-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="ea30f-115">Description</span></span>  
 <span data-ttu-id="ea30f-116">O exemplo de código a seguir demonstra como adicionar um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ponto de extremidade que é compatível com [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] clientes de serviço em código e, opcionalmente, em um arquivo de configuração da Web.</span><span class="sxs-lookup"><span data-stu-id="ea30f-116">The following example code demonstrates how to add a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] endpoint that is compatible with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ea30f-117">Código</span><span class="sxs-lookup"><span data-stu-id="ea30f-117">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ea30f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea30f-118">See Also</span></span>  
 [<span data-ttu-id="ea30f-119">Interoperabilidade com serviços Web do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ea30f-119">Interoperability with ASP.NET Web Services</span></span>](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
