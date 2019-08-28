---
title: Exemplo de tabela de UriTemplate
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: 9d60de39c8c025b31c45c79309442906fc3aab4e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044567"
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="8decf-102">Exemplo de tabela de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="8decf-102">UriTemplate Table Sample</span></span>
<span data-ttu-id="8decf-103">A <xref:System.UriTemplateTable> classe fornece uma estrutura de tabela associativa semelhante a um dicionário para trabalhar com um `UriTemplate` conjunto de instâncias.</span><span class="sxs-lookup"><span data-stu-id="8decf-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="8decf-104">Identificadores de recursos uniformes (URIs) específicos podem ser correspondidos com eficiência em todos os modelos na tabela, e os dados associados ao modelo correspondente podem ser recuperados.</span><span class="sxs-lookup"><span data-stu-id="8decf-104">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="8decf-105">Este exemplo demonstra os seguintes conceitos principais relacionados à `UriTemplateTable` classe:</span><span class="sxs-lookup"><span data-stu-id="8decf-105">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="8decf-106">Sintaxe para instanciar um `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="8decf-106">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="8decf-107">Populando um `UriTemplateTable` com um conjunto de pares chave/valor.</span><span class="sxs-lookup"><span data-stu-id="8decf-107">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
- <span data-ttu-id="8decf-108">Correspondendo um URI candidato à tabela usando <xref:System.UriTemplateTable.MatchSingle%2A>.</span><span class="sxs-lookup"><span data-stu-id="8decf-108">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8decf-109">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="8decf-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8decf-110">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8decf-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="8decf-111">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8decf-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8decf-112">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="8decf-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8decf-113">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="8decf-113">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="8decf-114">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="8decf-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8decf-115">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="8decf-115">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="8decf-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8decf-116">See also</span></span>

- [<span data-ttu-id="8decf-117">Dispatcher de Tabela de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="8decf-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
- [<span data-ttu-id="8decf-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="8decf-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
