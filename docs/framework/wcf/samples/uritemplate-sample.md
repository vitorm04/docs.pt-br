---
title: Exemplo de UriTemplate
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: e08333235b22e3c24fc6f4855fec43ef8b95fa5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183277"
---
# <a name="uritemplate-sample"></a><span data-ttu-id="3fd54-102">Exemplo de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="3fd54-102">UriTemplate Sample</span></span>
<span data-ttu-id="3fd54-103">A <xref:System.UriTemplate> classe fornece métodos para trabalhar com conjuntos de URIs que compartilham uma estrutura comum.</span><span class="sxs-lookup"><span data-stu-id="3fd54-103">The <xref:System.UriTemplate> class provides methods for working with sets of URIs that share a common structure.</span></span> <span data-ttu-id="3fd54-104">Esta amostra demonstra os seguintes `UriTemplate`conceitos-chave relacionados a:</span><span class="sxs-lookup"><span data-stu-id="3fd54-104">This sample demonstrates the following key concepts relating to `UriTemplate`:</span></span>  
  
- <span data-ttu-id="3fd54-105">Sintaxe para criação de modelos.</span><span class="sxs-lookup"><span data-stu-id="3fd54-105">Syntax for creating templates.</span></span>  
  
- <span data-ttu-id="3fd54-106">Instanciar URIs `UriTemplate` a <xref:System.UriTemplate.BindByName%2A> <xref:System.UriTemplate.BindByPosition%2A>partir de um uso e .</span><span class="sxs-lookup"><span data-stu-id="3fd54-106">Instantiating URIs from a `UriTemplate` using <xref:System.UriTemplate.BindByName%2A> and <xref:System.UriTemplate.BindByPosition%2A>.</span></span>  
  
- <span data-ttu-id="3fd54-107"><xref:System.UriTemplateTable.Match%2A>, que é a `BindByName` operação `BindByPosition`inversa de e .</span><span class="sxs-lookup"><span data-stu-id="3fd54-107"><xref:System.UriTemplateTable.Match%2A>, which is the inverse operation of `BindByName` and `BindByPosition`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3fd54-108">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="3fd54-108">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3fd54-109">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3fd54-109">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="3fd54-110">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3fd54-110">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3fd54-111">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="3fd54-111">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3fd54-112">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="3fd54-112">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3fd54-113">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="3fd54-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3fd54-114">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="3fd54-114">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a><span data-ttu-id="3fd54-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="3fd54-115">See also</span></span>

- [<span data-ttu-id="3fd54-116">Tabela de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="3fd54-116">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="3fd54-117">Dispatcher de Tabela de UriTemplate</span><span class="sxs-lookup"><span data-stu-id="3fd54-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
