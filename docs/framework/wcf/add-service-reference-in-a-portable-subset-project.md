---
title: Adicione uma referência de serviço em um projeto de subconjunto portátil
ms.date: 03/30/2017
ms.assetid: 61ccfe0f-a34b-40ca-8f5e-725fa1b8095e
ms.openlocfilehash: e1d65df46c0ed6d9d271727ad04a661c5e34a1ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145425"
---
# <a name="add-service-reference-in-a-portable-subset-project"></a><span data-ttu-id="d03e1-102">Adicione uma referência de serviço em um projeto de subconjunto portátil</span><span class="sxs-lookup"><span data-stu-id="d03e1-102">Add Service Reference in a Portable Subset Project</span></span>
<span data-ttu-id="d03e1-103">Projetos de subconjunto portáteis permitem que os programadores do assembly .NET manter uma única árvore de origem e o sistema de compilação e ainda dar suporte a várias implementações do .NET (área de trabalho, Silverlight, Windows Phone e XBOX).</span><span class="sxs-lookup"><span data-stu-id="d03e1-103">Portable subset projects enable .NET assembly programmers to maintain a single source tree and build system while still supporting multiple .NET implementations (desktop, Silverlight, Windows Phone, and XBOX).</span></span> <span data-ttu-id="d03e1-104">Projetos de subconjunto portáteis somente fazem referência a bibliotecas portáteis .NET, que são um assembly do framework .NET que pode ser usado em qualquer implementação do .NET.</span><span class="sxs-lookup"><span data-stu-id="d03e1-104">Portable subset projects only reference .NET portable libraries which are a .NET framework assembly that can be used on any .NET implementation.</span></span>  
  
## <a name="add-service-reference-details"></a><span data-ttu-id="d03e1-105">Detalhes de Adicionar Referência de Serviço</span><span class="sxs-lookup"><span data-stu-id="d03e1-105">Add Service Reference Details</span></span>  
 <span data-ttu-id="d03e1-106">Ao adicionar uma referência de serviço em um projeto de subconjunto portátil, as seguintes restrições são aplicadas:</span><span class="sxs-lookup"><span data-stu-id="d03e1-106">When adding a service reference in a portable subset project the following restrictions are enforced:</span></span>  
  
1.  <span data-ttu-id="d03e1-107">Para <xref:System.Xml.Serialization.XmlSerializer>, somente as codificações literais são permitidas.</span><span class="sxs-lookup"><span data-stu-id="d03e1-107">For <xref:System.Xml.Serialization.XmlSerializer>, only literal encodings are allowed.</span></span> <span data-ttu-id="d03e1-108">As codificações SOAP geram um erro durante a importação.</span><span class="sxs-lookup"><span data-stu-id="d03e1-108">SOAP encodings generate an error during import.</span></span>  
  
2.  <span data-ttu-id="d03e1-109">Para os serviços que usam cenários de <xref:System.Runtime.Serialization.DataContractSerializer>, um contrato de dados substituto é fornecido para garantir que os tipos reutilizados venham somente do subconjunto portátil.</span><span class="sxs-lookup"><span data-stu-id="d03e1-109">For services that use <xref:System.Runtime.Serialization.DataContractSerializer> scenarios, a data contract surrogate is provided to ensure that reused types come only from the portable subset.</span></span>  
  
3.  <span data-ttu-id="d03e1-110">Os pontos de extremidade que se baseiam em associações não têm suporte em bibliotecas portáteis (todas as associações exceto <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> sem fluxo de transações, sessões confiáveis ou codificação de MTOM e associações personalizadas equivalentes) são ignorados.</span><span class="sxs-lookup"><span data-stu-id="d03e1-110">Endpoints which rely on bindings not supported in portable libraries (all bindings except <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> without transaction flow, reliable sessions, or MTOM encoding, and equivalent custom bindings) are ignored.</span></span>  
  
4.  <span data-ttu-id="d03e1-111">Os cabeçalhos de mensagem são excluídos de todas as descrições de mensagem em todas as operações antes da importação.</span><span class="sxs-lookup"><span data-stu-id="d03e1-111">Message headers are deleted from all message descriptions in all operations before import.</span></span>  
  
5.  <span data-ttu-id="d03e1-112">Os atributos não portáteis <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute> e <xref:System.ServiceModel.TransactionFlowAttribute> são removidos do código de proxy cliente gerado.</span><span class="sxs-lookup"><span data-stu-id="d03e1-112">Non-portable attributes <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute>, and <xref:System.ServiceModel.TransactionFlowAttribute> are removed from generated client proxy code.</span></span>  
  
6.  <span data-ttu-id="d03e1-113">As propriedades não portáteis ProtectionLevel, SessionMode, IsInitiating, IsTerminating são removidas de <xref:System.ServiceModel.ServiceContractAttribute>, de <xref:System.ServiceModel.OperationContractAttribute> e de <xref:System.ServiceModel.FaultContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d03e1-113">Non-portable properties ProtectionLevel, SessionMode, IsInitiating, IsTerminating are removed from <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, and <xref:System.ServiceModel.FaultContractAttribute>.</span></span>  
  
7.  <span data-ttu-id="d03e1-114">Todas as operações de serviço são geradas como operações assíncronas no proxy do cliente.</span><span class="sxs-lookup"><span data-stu-id="d03e1-114">All service operations are generated as asynchronous operations on the client proxy.</span></span>  
  
8.  <span data-ttu-id="d03e1-115">Os construtores de cliente gerados que usam tipos não portáteis são removidos.</span><span class="sxs-lookup"><span data-stu-id="d03e1-115">Generated client constructors which use non-portable types are removed.</span></span>  
  
9. <span data-ttu-id="d03e1-116">Uma instância <xref:System.Net.CookieContainer> é exposta no cliente gerado.</span><span class="sxs-lookup"><span data-stu-id="d03e1-116">A <xref:System.Net.CookieContainer> instance is exposed on the generated client.</span></span>  
  
10. <span data-ttu-id="d03e1-117">Um comentário é inserido na parte superior do arquivo identificando o assembly e a versão do gerador de código:</span><span class="sxs-lookup"><span data-stu-id="d03e1-117">A comment is inserted at the top of the file identifying the assembly and version of the code generator:</span></span>`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`  
  
11. <span data-ttu-id="d03e1-118">A interface do <xref:System.Runtime.Serialization.ISerializable> não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="d03e1-118">The <xref:System.Runtime.Serialization.ISerializable> interface is not supported.</span></span>  
  
12. <span data-ttu-id="d03e1-119">As associações de Net.Tcp e PollingDuplex não têm suporte</span><span class="sxs-lookup"><span data-stu-id="d03e1-119">Net.Tcp and PollingDuplex bindings are not supported</span></span>  
  
13. <span data-ttu-id="d03e1-120">O <xref:System.Runtime.Serialization.DataContractSerializer> sempre será usado para falhas.</span><span class="sxs-lookup"><span data-stu-id="d03e1-120">The <xref:System.Runtime.Serialization.DataContractSerializer> will always be used for faults.</span></span>  
  
14. <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> <span data-ttu-id="d03e1-121">Não há suporte em projetos de subconjunto portátil.</span><span class="sxs-lookup"><span data-stu-id="d03e1-121">is not supported in portable subset projects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d03e1-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d03e1-122">See also</span></span>

- [<span data-ttu-id="d03e1-123">Usando um cliente WCF para acessar um serviço</span><span class="sxs-lookup"><span data-stu-id="d03e1-123">Accessing Services Using a WCF Client</span></span>](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="d03e1-124">Biblioteca de Classes Portátil</span><span class="sxs-lookup"><span data-stu-id="d03e1-124">Portable Class Library</span></span>](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
