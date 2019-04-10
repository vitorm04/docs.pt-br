---
title: Exemplos de distribuidor de tabela de UriTemplate
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: 800765c6b01e49b730414132ac64ab8eed3e9e5f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330825"
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="e4afb-102">Exemplos de distribuidor de tabela de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="e4afb-102">UriTemplate Table Dispatcher Sample</span></span>
<span data-ttu-id="e4afb-103">O <xref:System.UriTemplateTable> classe fornece uma estrutura de tabela associativa de dicionário semelhante para trabalhar com um conjunto de <xref:System.UriTemplate> instâncias.</span><span class="sxs-lookup"><span data-stu-id="e4afb-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="e4afb-104">Este exemplo demonstra um mecanismo básico de expedição criado usando `UriTemplateTable`, um cenário de uso comum para o `UriTemplateTable` classe.</span><span class="sxs-lookup"><span data-stu-id="e4afb-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="e4afb-105">Este exemplo demonstra os seguintes conceitos principais para o `UriTemplateTable` classe:</span><span class="sxs-lookup"><span data-stu-id="e4afb-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
-   <span data-ttu-id="e4afb-106">Associando delegados com `UriTemplates` em um `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="e4afb-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
-   <span data-ttu-id="e4afb-107">Usando <xref:System.UriTemplateTable.MatchSingle%2A> para obter o delegado do manipulador correto para um URI específico.</span><span class="sxs-lookup"><span data-stu-id="e4afb-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
-   <span data-ttu-id="e4afb-108">Invocar o delegado de manipulador para processar a solicitação.</span><span class="sxs-lookup"><span data-stu-id="e4afb-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e4afb-109">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="e4afb-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e4afb-110">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e4afb-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="e4afb-111">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e4afb-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e4afb-112">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e4afb-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e4afb-113">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e4afb-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e4afb-114">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="e4afb-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e4afb-115">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e4afb-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="e4afb-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4afb-116">See also</span></span>

- [<span data-ttu-id="e4afb-117">Tabela de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="e4afb-117">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="e4afb-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="e4afb-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
