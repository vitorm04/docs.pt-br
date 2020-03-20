---
title: Exemplo de tabela de UriTemplate
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: c0aed1a49faf74ab9fd463769aab66ad72e74038
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183258"
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="87db3-102">Exemplo de tabela de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="87db3-102">UriTemplate Table Sample</span></span>
<span data-ttu-id="87db3-103">A <xref:System.UriTemplateTable> classe fornece uma estrutura de tabela associativa `UriTemplate` semelhante a um dicionário para trabalhar com um conjunto de instâncias.</span><span class="sxs-lookup"><span data-stu-id="87db3-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="87db3-104">Os URIs (Uniform Resource Identifiers, identificadores uniformes específicos) podem ser combinados eficientemente com todos os modelos da tabela, e os dados associados ao modelo combinado podem ser recuperados.</span><span class="sxs-lookup"><span data-stu-id="87db3-104">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="87db3-105">Esta amostra demonstra os seguintes `UriTemplateTable` conceitos-chave relacionados à classe:</span><span class="sxs-lookup"><span data-stu-id="87db3-105">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="87db3-106">Sintaxe para instanciar um `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="87db3-106">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="87db3-107">Povoando `UriTemplateTable` um com um conjunto de pares de chave/valor.</span><span class="sxs-lookup"><span data-stu-id="87db3-107">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
- <span data-ttu-id="87db3-108">Combinando um URI candidato <xref:System.UriTemplateTable.MatchSingle%2A>contra a tabela usando .</span><span class="sxs-lookup"><span data-stu-id="87db3-108">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="87db3-109">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="87db3-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="87db3-110">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="87db3-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="87db3-111">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="87db3-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="87db3-112">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="87db3-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="87db3-113">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="87db3-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="87db3-114">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="87db3-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="87db3-115">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="87db3-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="87db3-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="87db3-116">See also</span></span>

- [<span data-ttu-id="87db3-117">Dispatcher de Tabela de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="87db3-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
- [<span data-ttu-id="87db3-118">Uritemplate</span><span class="sxs-lookup"><span data-stu-id="87db3-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
