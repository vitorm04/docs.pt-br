---
title: Adicione uma referência de serviço em um projeto de subconjunto portátil
ms.date: 03/30/2017
ms.assetid: 61ccfe0f-a34b-40ca-8f5e-725fa1b8095e
ms.openlocfilehash: 764ce487d8f2673eb2c75f8cd05da4ccbae3c935
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320847"
---
# <a name="add-service-reference-in-a-portable-subset-project"></a><span data-ttu-id="6c852-102">Adicione uma referência de serviço em um projeto de subconjunto portátil</span><span class="sxs-lookup"><span data-stu-id="6c852-102">Add Service Reference in a Portable Subset Project</span></span>
<span data-ttu-id="6c852-103">Os projetos de subconjuntos portáteis permitem que os programadores de assembly .NET mantenham uma única árvore de origem e um sistema de compilação enquanto ainda dão suporte a várias implementações do .NET (desktop, Silverlight, Windows Phone e XBOX).</span><span class="sxs-lookup"><span data-stu-id="6c852-103">Portable subset projects enable .NET assembly programmers to maintain a single source tree and build system while still supporting multiple .NET implementations (desktop, Silverlight, Windows Phone, and XBOX).</span></span> <span data-ttu-id="6c852-104">Os projetos de subconjuntos portáteis só fazem referência a bibliotecas portáteis .NET que são um assembly do .NET Framework que pode ser usado em qualquer implementação do .NET.</span><span class="sxs-lookup"><span data-stu-id="6c852-104">Portable subset projects only reference .NET portable libraries which are a .NET framework assembly that can be used on any .NET implementation.</span></span>  
  
## <a name="add-service-reference-details"></a><span data-ttu-id="6c852-105">Detalhes de Adicionar Referência de Serviço</span><span class="sxs-lookup"><span data-stu-id="6c852-105">Add Service Reference Details</span></span>  
 <span data-ttu-id="6c852-106">Ao adicionar uma referência de serviço em um projeto de subconjunto portátil, as seguintes restrições são aplicadas:</span><span class="sxs-lookup"><span data-stu-id="6c852-106">When adding a service reference in a portable subset project the following restrictions are enforced:</span></span>  
  
1. <span data-ttu-id="6c852-107">Para <xref:System.Xml.Serialization.XmlSerializer>, somente as codificações literais são permitidas.</span><span class="sxs-lookup"><span data-stu-id="6c852-107">For <xref:System.Xml.Serialization.XmlSerializer>, only literal encodings are allowed.</span></span> <span data-ttu-id="6c852-108">As codificações SOAP geram um erro durante a importação.</span><span class="sxs-lookup"><span data-stu-id="6c852-108">SOAP encodings generate an error during import.</span></span>  
  
2. <span data-ttu-id="6c852-109">Para os serviços que usam cenários de <xref:System.Runtime.Serialization.DataContractSerializer>, um contrato de dados substituto é fornecido para garantir que os tipos reutilizados venham somente do subconjunto portátil.</span><span class="sxs-lookup"><span data-stu-id="6c852-109">For services that use <xref:System.Runtime.Serialization.DataContractSerializer> scenarios, a data contract surrogate is provided to ensure that reused types come only from the portable subset.</span></span>  
  
3. <span data-ttu-id="6c852-110">Os pontos de extremidade que se baseiam em associações não têm suporte em bibliotecas portáteis (todas as associações exceto <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> sem fluxo de transações, sessões confiáveis ou codificação de MTOM e associações personalizadas equivalentes) são ignorados.</span><span class="sxs-lookup"><span data-stu-id="6c852-110">Endpoints which rely on bindings not supported in portable libraries (all bindings except <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> without transaction flow, reliable sessions, or MTOM encoding, and equivalent custom bindings) are ignored.</span></span>  
  
4. <span data-ttu-id="6c852-111">Os cabeçalhos de mensagem são excluídos de todas as descrições de mensagem em todas as operações antes da importação.</span><span class="sxs-lookup"><span data-stu-id="6c852-111">Message headers are deleted from all message descriptions in all operations before import.</span></span>  
  
5. <span data-ttu-id="6c852-112">Os atributos não portáteis <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute> e <xref:System.ServiceModel.TransactionFlowAttribute> são removidos do código de proxy cliente gerado.</span><span class="sxs-lookup"><span data-stu-id="6c852-112">Non-portable attributes <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute>, and <xref:System.ServiceModel.TransactionFlowAttribute> are removed from generated client proxy code.</span></span>  
  
6. <span data-ttu-id="6c852-113">As propriedades não portáteis ProtectionLevel, SessionMode, IsInitiating, IsTerminating são removidas de <xref:System.ServiceModel.ServiceContractAttribute>, de <xref:System.ServiceModel.OperationContractAttribute> e de <xref:System.ServiceModel.FaultContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="6c852-113">Non-portable properties ProtectionLevel, SessionMode, IsInitiating, IsTerminating are removed from <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, and <xref:System.ServiceModel.FaultContractAttribute>.</span></span>  
  
7. <span data-ttu-id="6c852-114">Todas as operações de serviço são geradas como operações assíncronas no proxy do cliente.</span><span class="sxs-lookup"><span data-stu-id="6c852-114">All service operations are generated as asynchronous operations on the client proxy.</span></span>  
  
8. <span data-ttu-id="6c852-115">Os construtores de cliente gerados que usam tipos não portáteis são removidos.</span><span class="sxs-lookup"><span data-stu-id="6c852-115">Generated client constructors which use non-portable types are removed.</span></span>  
  
9. <span data-ttu-id="6c852-116">Uma instância <xref:System.Net.CookieContainer> é exposta no cliente gerado.</span><span class="sxs-lookup"><span data-stu-id="6c852-116">A <xref:System.Net.CookieContainer> instance is exposed on the generated client.</span></span>  
  
10. <span data-ttu-id="6c852-117">Um comentário é inserido na parte superior do arquivo identificando o assembly e a versão do gerador de código:`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`</span><span class="sxs-lookup"><span data-stu-id="6c852-117">A comment is inserted at the top of the file identifying the assembly and version of the code generator:`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`</span></span>  
  
11. <span data-ttu-id="6c852-118">A interface do <xref:System.Runtime.Serialization.ISerializable> não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="6c852-118">The <xref:System.Runtime.Serialization.ISerializable> interface is not supported.</span></span>  
  
12. <span data-ttu-id="6c852-119">As associações de Net.Tcp e PollingDuplex não têm suporte</span><span class="sxs-lookup"><span data-stu-id="6c852-119">Net.Tcp and PollingDuplex bindings are not supported</span></span>  
  
13. <span data-ttu-id="6c852-120">O <xref:System.Runtime.Serialization.DataContractSerializer> sempre será usado para falhas.</span><span class="sxs-lookup"><span data-stu-id="6c852-120">The <xref:System.Runtime.Serialization.DataContractSerializer> will always be used for faults.</span></span>  
  
14. <span data-ttu-id="6c852-121">O <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> não tem suporte em projetos de subconjunto portáteis.</span><span class="sxs-lookup"><span data-stu-id="6c852-121"><xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is not supported in portable subset projects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c852-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c852-122">See also</span></span>

- [<span data-ttu-id="6c852-123">Usando um cliente do WCF para acessar serviços</span><span class="sxs-lookup"><span data-stu-id="6c852-123">Accessing Services Using a WCF Client</span></span>](accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="6c852-124">Biblioteca de classes portátil</span><span class="sxs-lookup"><span data-stu-id="6c852-124">Portable Class Library</span></span>](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
