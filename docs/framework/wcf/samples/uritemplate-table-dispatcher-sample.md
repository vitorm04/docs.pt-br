---
title: Exemplos de distribuidor de tabela de UriTemplate
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: aa4259f8c823bebf38b9689df92c45992cb55723
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143675"
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="b7100-102">Exemplos de distribuidor de tabela de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="b7100-102">UriTemplate Table Dispatcher Sample</span></span>
<span data-ttu-id="b7100-103">A <xref:System.UriTemplateTable> classe fornece uma estrutura de tabela associativa <xref:System.UriTemplate> semelhante a um dicionário para trabalhar com um conjunto de instâncias.</span><span class="sxs-lookup"><span data-stu-id="b7100-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="b7100-104">Esta amostra demonstra um mecanismo `UriTemplateTable`de despacho básico construído `UriTemplateTable` usando , um cenário de uso comum para a classe.</span><span class="sxs-lookup"><span data-stu-id="b7100-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="b7100-105">Esta amostra demonstra os seguintes conceitos-chave para a `UriTemplateTable` classe:</span><span class="sxs-lookup"><span data-stu-id="b7100-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="b7100-106">Associando delegados `UriTemplates` em `UriTemplateTable`um .</span><span class="sxs-lookup"><span data-stu-id="b7100-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="b7100-107">Usando <xref:System.UriTemplateTable.MatchSingle%2A> para obter o delegado manipulador correto para um URI específico.</span><span class="sxs-lookup"><span data-stu-id="b7100-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
- <span data-ttu-id="b7100-108">Invocando o delegado manipulador para processar a solicitação.</span><span class="sxs-lookup"><span data-stu-id="b7100-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b7100-109">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="b7100-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b7100-110">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b7100-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="b7100-111">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b7100-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b7100-112">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="b7100-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b7100-113">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="b7100-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b7100-114">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="b7100-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b7100-115">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="b7100-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="b7100-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="b7100-116">See also</span></span>

- [<span data-ttu-id="b7100-117">Tabela de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="b7100-117">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="b7100-118">Uritemplate</span><span class="sxs-lookup"><span data-stu-id="b7100-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
