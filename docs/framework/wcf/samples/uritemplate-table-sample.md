---
title: Exemplo de tabela de UriTemplate
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: 4543d4676344d10c3e380c3522a7ca5a6a8d6294
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006441"
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="4e920-102">Exemplo de tabela de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="4e920-102">UriTemplate Table Sample</span></span>
<span data-ttu-id="4e920-103">O <xref:System.UriTemplateTable> classe fornece uma estrutura de tabela associativa de dicionário semelhante para trabalhar com um conjunto de `UriTemplate` instâncias.</span><span class="sxs-lookup"><span data-stu-id="4e920-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="4e920-104">Específico identificadores de recurso uniformes (URIs) possam ser comparados com eficiência com todos os modelos na tabela e dados associados ao modelo correspondente podem ser recuperados.</span><span class="sxs-lookup"><span data-stu-id="4e920-104">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="4e920-105">Este exemplo demonstra os seguintes conceitos principais relacionados à `UriTemplateTable` classe:</span><span class="sxs-lookup"><span data-stu-id="4e920-105">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="4e920-106">Sintaxe para instanciar um `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="4e920-106">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="4e920-107">Populando um `UriTemplateTable` com um conjunto de pares chave/valor.</span><span class="sxs-lookup"><span data-stu-id="4e920-107">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
- <span data-ttu-id="4e920-108">Correspondência de um URI candidato contra a tabela usando <xref:System.UriTemplateTable.MatchSingle%2A>.</span><span class="sxs-lookup"><span data-stu-id="4e920-108">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4e920-109">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="4e920-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4e920-110">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4e920-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="4e920-111">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4e920-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4e920-112">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="4e920-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4e920-113">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="4e920-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4e920-114">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="4e920-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4e920-115">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="4e920-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="4e920-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4e920-116">See also</span></span>

- [<span data-ttu-id="4e920-117">Dispatcher de Tabela de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="4e920-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
- [<span data-ttu-id="4e920-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="4e920-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
