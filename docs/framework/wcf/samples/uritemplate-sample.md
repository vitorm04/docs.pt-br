---
title: Exemplo de UriTemplate
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: 0dfb2cdc27460f3bc30a1c4302206bf43f7ef007
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518864"
---
# <a name="uritemplate-sample"></a><span data-ttu-id="03c7c-102">Exemplo de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="03c7c-102">UriTemplate Sample</span></span>
<span data-ttu-id="03c7c-103">O <xref:System.UriTemplate> classe fornece métodos para trabalhar com conjuntos de URIs que compartilham uma estrutura comum.</span><span class="sxs-lookup"><span data-stu-id="03c7c-103">The <xref:System.UriTemplate> class provides methods for working with sets of URIs that share a common structure.</span></span> <span data-ttu-id="03c7c-104">Este exemplo demonstra os seguintes conceitos principais relacionados ao `UriTemplate`:</span><span class="sxs-lookup"><span data-stu-id="03c7c-104">This sample demonstrates the following key concepts relating to `UriTemplate`:</span></span>  
  
-   <span data-ttu-id="03c7c-105">Sintaxe para criação de modelos.</span><span class="sxs-lookup"><span data-stu-id="03c7c-105">Syntax for creating templates.</span></span>  
  
-   <span data-ttu-id="03c7c-106">Criando uma instância de URIs de um `UriTemplate` usando <xref:System.UriTemplate.BindByName%2A> e <xref:System.UriTemplate.BindByPosition%2A>.</span><span class="sxs-lookup"><span data-stu-id="03c7c-106">Instantiating URIs from a `UriTemplate` using <xref:System.UriTemplate.BindByName%2A> and <xref:System.UriTemplate.BindByPosition%2A>.</span></span>  
  
-   <span data-ttu-id="03c7c-107"><xref:System.UriTemplateTable.Match%2A>, que é o inverso da operação de `BindByName` e `BindByPosition`.</span><span class="sxs-lookup"><span data-stu-id="03c7c-107"><xref:System.UriTemplateTable.Match%2A>, which is the inverse operation of `BindByName` and `BindByPosition`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="03c7c-108">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="03c7c-108">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="03c7c-109">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="03c7c-109">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="03c7c-110">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="03c7c-110">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="03c7c-111">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="03c7c-111">The samples may already be installed on your computer.</span></span> <span data-ttu-id="03c7c-112">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="03c7c-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="03c7c-113">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="03c7c-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="03c7c-114">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="03c7c-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a><span data-ttu-id="03c7c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03c7c-115">See Also</span></span>  
 [<span data-ttu-id="03c7c-116">Tabela de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="03c7c-116">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [<span data-ttu-id="03c7c-117">Dispatcher de Tabela de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="03c7c-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
