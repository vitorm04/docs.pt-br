---
title: Substituído em Windows Workflow Foundation
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: d41bf147cd079a3d6d3714da5595732de3dcb7de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774043"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a><span data-ttu-id="d5631-102">Substituído em Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="d5631-102">Deprecated types in Windows Workflow Foundation</span></span>
<span data-ttu-id="d5631-103">Em .NET 4 a equipe de fluxo de trabalho liberou qualquer novo mecanismo de fluxo de trabalho no espaço de <xref:System.Activities> .</span><span class="sxs-lookup"><span data-stu-id="d5631-103">In .NET 4 the Workflow Team released an all new Workflow engine in the <xref:System.Activities> namespace.</span></span> <span data-ttu-id="d5631-104">Com o lançamento do .NET Beta 4.5 nós estamos marcando a maioria dos tipos em "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, e <xref:System.Workflow.Runtime> namespaces como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="d5631-104">With the release of .NET 4.5 Beta we are marking most of the types in the "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, and  <xref:System.Workflow.Runtime> namespaces as obsolete.</span></span>  
  
## <a name="obsolete-namespaces-and-tools"></a><span data-ttu-id="d5631-105">Namespaces e ferramentas obsoletas</span><span class="sxs-lookup"><span data-stu-id="d5631-105">Obsolete namespaces and tools</span></span>  
 <span data-ttu-id="d5631-106">Os seguintes conjuntos possuem um ou mais tipos públicos que serão substituídos:</span><span class="sxs-lookup"><span data-stu-id="d5631-106">The following assemblies have one or more public types that will be deprecated:</span></span>  
  
- <span data-ttu-id="d5631-107">System.Workflow.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="d5631-107">System.Workflow.Activities.dll</span></span>  
  
- <span data-ttu-id="d5631-108">System.Workflow.ComponentModel.dll</span><span class="sxs-lookup"><span data-stu-id="d5631-108">System.Workflow.ComponentModel.dll</span></span>  
  
- <span data-ttu-id="d5631-109">System.Workflow.Runtime.dll</span><span class="sxs-lookup"><span data-stu-id="d5631-109">System.Workflow.Runtime.dll</span></span>  
  
- <span data-ttu-id="d5631-110">System.WorkflowServices.dll</span><span class="sxs-lookup"><span data-stu-id="d5631-110">System.WorkflowServices.dll</span></span>  
  
- <span data-ttu-id="d5631-111">Microsoft.Workflow.DebugController.dll</span><span class="sxs-lookup"><span data-stu-id="d5631-111">Microsoft.Workflow.DebugController.dll</span></span>  
  
- <span data-ttu-id="d5631-112">Microsoft.Workflow.Compiler.exe</span><span class="sxs-lookup"><span data-stu-id="d5631-112">Microsoft.Workflow.Compiler.exe</span></span>  
  
- <span data-ttu-id="d5631-113">Wfc.exe</span><span class="sxs-lookup"><span data-stu-id="d5631-113">Wfc.exe</span></span>  
  
 <span data-ttu-id="d5631-114">Como resultado, os clientes que são substituídos usando APIs de WF 3 encontrarão avisos de compilação com uma mensagem semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="d5631-114">As a result, customers who are using the deprecated WF 3 APIs will encounter build warnings with a message similar to the following:</span></span>  
  
 <span data-ttu-id="d5631-115">**BC40000 de aviso: X é obsoleto: O WF 3 foram preteridos. Use o WF 4.**</span><span class="sxs-lookup"><span data-stu-id="d5631-115">**Warning BC40000: X is obsolete: WF 3 types are deprecated. Please use WF 4 instead.**</span></span> <span data-ttu-id="d5631-116">Nós removeremos os tipos do.NET Framework em uma versão futura, mas nós não determinamos ainda esse o prazo (não em 4,5).</span><span class="sxs-lookup"><span data-stu-id="d5631-116">We will remove the types from the .NET Framework in a future release, but we have not yet determined that timeframe (not in 4.5).</span></span> <span data-ttu-id="d5631-117">Esta etapa atual permite que nós comuniquem a direção a nossos clientes e permitam-lhes a abundância hora de mover para o novo modelo WF4.</span><span class="sxs-lookup"><span data-stu-id="d5631-117">This current step allows us to communicate our direction to our customers and allow them plenty of time to move to the new WF4 model.</span></span> <span data-ttu-id="d5631-118">Claro, continuaremos a dar suporte a esses tipos de WF 3 sob o [política de ciclo de vida do suporte da Microsoft](https://aka.ms/MicrosoftSupportLifecycle).</span><span class="sxs-lookup"><span data-stu-id="d5631-118">We will, of course, continue to support these WF 3 types under the [Microsoft Support Lifecycle Policy](https://aka.ms/MicrosoftSupportLifecycle).</span></span> <span data-ttu-id="d5631-119">Os aplicativos WF3 existentes serão executados sem problema no .NET 4.5 e Visual Studio 2012 oferecerá suporte a soluções WF3-based novas e existentes.</span><span class="sxs-lookup"><span data-stu-id="d5631-119">Existing WF3 applications will run without issue on .NET 4.5, and Visual Studio 2012 will support new and existing WF3-based solutions.</span></span>  
  
 <span data-ttu-id="d5631-120">As regras tipos relacionados ao espaço de <xref:System.Workflow.Activities.Rules> , que não têm uma substituição em WF 4,5, não foram substituídas dentro.</span><span class="sxs-lookup"><span data-stu-id="d5631-120">Rules related types in the <xref:System.Workflow.Activities.Rules> namespace, which do not have a replacement in WF 4.5, have not been deprecated.</span></span>  
  
 <span data-ttu-id="d5631-121">Os clientes que desejam migrar seus aplicativos para o WF 4 localizarão a Ajuda do [diretrizes de migração do fluxo de trabalho 4](migration-guidance.md).</span><span class="sxs-lookup"><span data-stu-id="d5631-121">Customers who want to migrate their applications to WF 4 will find help in the [Workflow 4 Migration Guidance](migration-guidance.md).</span></span>
