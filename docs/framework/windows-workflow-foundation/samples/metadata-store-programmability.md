---
title: Programabilidade de Store de metadados
ms.date: 03/30/2017
ms.assetid: 5b613661-f3f9-4e07-8e88-28c9ea2fd8f8
ms.openlocfilehash: 4ea6117686b985a9ea18ce4e5cc4ea2b5c25524c
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45512524"
---
# <a name="metadata-store-programmability"></a><span data-ttu-id="e9f6c-102">Programabilidade de Store de metadados</span><span class="sxs-lookup"><span data-stu-id="e9f6c-102">Metadata Store Programmability</span></span>
<span data-ttu-id="e9f6c-103">O armazenamento de metadados é um recurso de [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] que permite a associação de metadados arbitrários, na forma de atributos CLR, para tipos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e9f6c-103">The metadata store is a [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] feature that allows for the association of arbitrary metadata, in the form of CLR attributes, to types at runtime.</span></span> <span data-ttu-id="e9f6c-104">Isso permite que um acoplamento fraco entre os componentes de tempo de execução e suas contrapartes em tempo de design, bem como a capacidade alterar os componentes de tempo de design sem afetar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e9f6c-104">This allows for a loose coupling between the run-time components and their design-time counterparts, as well as the ability to change the design-time components without affecting the runtime.</span></span> <span data-ttu-id="e9f6c-105">O exemplo mostra como programar no armazenamento de metadados aplicando atributos para um tipo de tempo de execução, a fonte para que nós não tem controle sobre.</span><span class="sxs-lookup"><span data-stu-id="e9f6c-105">The sample shows how to program against the metadata store by applying attributes to a run-time type, the source for which we have no control over.</span></span> <span data-ttu-id="e9f6c-106">A terminologia usada normalmente é que um aplicativo hospedeiro registra os metadados para um conjunto de tipos.</span><span class="sxs-lookup"><span data-stu-id="e9f6c-106">The terminology typically used is that a hosting application registers the metadata for a set of types.</span></span>  
  
 <span data-ttu-id="e9f6c-107">Dentro de saída, você pode perceber um atributo adicional, inesperado, <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`.</span><span class="sxs-lookup"><span data-stu-id="e9f6c-107">Within the output, you may notice an additional, unexpected attribute, <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`.</span></span> <span data-ttu-id="e9f6c-108">Isso é adicionado ao usar os metadados API e não tem impacto no exemplo.</span><span class="sxs-lookup"><span data-stu-id="e9f6c-108">This is added when using the Metadata API and has no impact on the running of the sample.</span></span>  
  
 <span data-ttu-id="e9f6c-109">Este exemplo demonstra:</span><span class="sxs-lookup"><span data-stu-id="e9f6c-109">This sample demonstrates:</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="e9f6c-110">Demonstra</span><span class="sxs-lookup"><span data-stu-id="e9f6c-110">Demonstrates</span></span>  
  
-   <span data-ttu-id="e9f6c-111">A inclusão de atributo que usa metadados armazena API.</span><span class="sxs-lookup"><span data-stu-id="e9f6c-111">Attribute injection using the metadata store API.</span></span>  
  
-   <span data-ttu-id="e9f6c-112">Usando um mecanismo de retorno de chamada para adiar o registro de metadados.</span><span class="sxs-lookup"><span data-stu-id="e9f6c-112">Using a callback mechanism to defer metadata registration.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e9f6c-113">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="e9f6c-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e9f6c-114">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de ProgrammingMetadataStore.sln.</span><span class="sxs-lookup"><span data-stu-id="e9f6c-114">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ProgrammingMetadataStore.sln solution file.</span></span>  
  
2.  <span data-ttu-id="e9f6c-115">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="e9f6c-115">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="e9f6c-116">Para executar a solução, pressione F5.</span><span class="sxs-lookup"><span data-stu-id="e9f6c-116">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e9f6c-117">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e9f6c-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e9f6c-118">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e9f6c-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e9f6c-119">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="e9f6c-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e9f6c-120">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e9f6c-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\MetadataStore`