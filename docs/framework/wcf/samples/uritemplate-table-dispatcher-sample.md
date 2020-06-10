---
title: Exemplos de distribuidor de tabela de UriTemplate
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: 97e916aaf9d137eb7931470f9565797b03620d28
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591066"
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="7f76e-102">Exemplos de distribuidor de tabela de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="7f76e-102">UriTemplate Table Dispatcher Sample</span></span>
<span data-ttu-id="7f76e-103">A <xref:System.UriTemplateTable> classe fornece uma estrutura de tabela associativa semelhante a um dicionário para trabalhar com um conjunto de <xref:System.UriTemplate> instâncias.</span><span class="sxs-lookup"><span data-stu-id="7f76e-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="7f76e-104">Este exemplo demonstra um mecanismo de expedição básico criado usando `UriTemplateTable` o, um cenário de uso comum para a `UriTemplateTable` classe.</span><span class="sxs-lookup"><span data-stu-id="7f76e-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="7f76e-105">Este exemplo demonstra os seguintes conceitos principais para a `UriTemplateTable` classe:</span><span class="sxs-lookup"><span data-stu-id="7f76e-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="7f76e-106">Associando delegados a `UriTemplates` em um `UriTemplateTable` .</span><span class="sxs-lookup"><span data-stu-id="7f76e-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="7f76e-107">Usando <xref:System.UriTemplateTable.MatchSingle%2A> para obter o delegado de manipulador correto para um URI específico.</span><span class="sxs-lookup"><span data-stu-id="7f76e-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
- <span data-ttu-id="7f76e-108">Invocar o delegado de manipulador para processar a solicitação.</span><span class="sxs-lookup"><span data-stu-id="7f76e-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7f76e-109">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="7f76e-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7f76e-110">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7f76e-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="7f76e-111">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7f76e-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7f76e-112">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="7f76e-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7f76e-113">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="7f76e-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7f76e-114">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="7f76e-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7f76e-115">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="7f76e-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="7f76e-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="7f76e-116">See also</span></span>

- [<span data-ttu-id="7f76e-117">Tabela de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="7f76e-117">UriTemplate Table</span></span>](uritemplate-table-sample.md)
- [<span data-ttu-id="7f76e-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="7f76e-118">UriTemplate</span></span>](uritemplate-sample.md)
