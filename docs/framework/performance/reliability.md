---
title: Confiabilidade
description: Entenda a confiabilidade no .NET. Proteja-se contra exceções assíncronas em hosts em execução no .NET, como SQL Server.
ms.date: 03/30/2017
helpviewer_keywords:
- SQL Server [.NET Framework]
- managed code, reliability
- reliability [.NET Framework]
- writing reliable code
- code, reliability
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
ms.openlocfilehash: ce9ffbb7f58c2f5dc016c56c0e2ce13b45c30f26
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474248"
---
# <a name="reliability"></a><span data-ttu-id="90565-104">Confiabilidade</span><span class="sxs-lookup"><span data-stu-id="90565-104">Reliability</span></span>
<span data-ttu-id="90565-105">É importante que o código em execução em ambientes de servidor como o SQL Server proteja contra exceções assíncronas.</span><span class="sxs-lookup"><span data-stu-id="90565-105">It is important that code executing in server environments such as SQL Server protect against asynchronous exceptions.</span></span> <span data-ttu-id="90565-106">A confiabilidade, conforme discutido aqui, não é específica para o SQL Server, mas sim para escrever código confiável para qualquer host executando em um ambiente do .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="90565-106">Reliability, as discussed here, is not specific to SQL Server but to writing reliable code for any host executing in a .NET Framework version 2.0 environment.</span></span> <span data-ttu-id="90565-107">No entanto, o SQL Server é o primeiro serviço fazendo uso amplo dos novos recursos de confiabilidade da versão 2.0, então ele é usado como exemplo.</span><span class="sxs-lookup"><span data-stu-id="90565-107">However, SQL Server is the first service making extensive use of the new reliability features of version 2.0, so it is used as an example.</span></span>  
  
 <span data-ttu-id="90565-108">Código em execução no SQL Server deve lidar com diretrizes de confiabilidade mais rígidas que as encontradas em outros ambientes de servidor.</span><span class="sxs-lookup"><span data-stu-id="90565-108">Code running in SQL Server must deal with more stringent reliability guidelines than other server environments.</span></span> <span data-ttu-id="90565-109">Isso ocorre devido à operação estável do SQL Server na borda de consumo de recursos.</span><span class="sxs-lookup"><span data-stu-id="90565-109">This is due to SQL Server’s steady operation at the edge of resource consumption.</span></span>  <span data-ttu-id="90565-110">Exceções <xref:System.OutOfMemoryException> e <xref:System.Threading.ThreadAbortException> não são incomuns no ambiente do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="90565-110"><xref:System.OutOfMemoryException> and <xref:System.Threading.ThreadAbortException> exceptions are not uncommon in the SQL Server environment.</span></span> <span data-ttu-id="90565-111">Em linhas gerais, essas diretrizes concentram-se menos em confiabilidade e mais em permitir que código gerenciado totalmente confiável falhe de maneira elegante ao enfrentar uma reciclagem de nível de <xref:System.AppDomain>, que é a principal maneira pela qual o servidor mantém a consistência e a disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="90565-111">These guidelines in general are focused less on reliability and more on allowing fully trusted managed code to fail gracefully in the face of <xref:System.AppDomain>-level recycling, which is the primary way the server maintains consistency and availability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90565-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="90565-112">In This Section</span></span>  
 [<span data-ttu-id="90565-113">Programação em SQL Server e atributos de proteção de host</span><span class="sxs-lookup"><span data-stu-id="90565-113">SQL Server Programming and Host Protection Attributes</span></span>](sql-server-programming-and-host-protection-attributes.md)  
 <span data-ttu-id="90565-114">Descreve como o atributo <xref:System.Security.Permissions.HostProtectionAttribute> é usado pelo SQL Server para restringir a execução de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="90565-114">Describes how the <xref:System.Security.Permissions.HostProtectionAttribute> attribute is used by SQL Server to restrict the execution of managed code.</span></span>  
  
 [<span data-ttu-id="90565-115">Práticas recomendadas de confiabilidade</span><span class="sxs-lookup"><span data-stu-id="90565-115">Reliability Best Practices</span></span>](reliability-best-practices.md)  
 <span data-ttu-id="90565-116">Fornece diretrizes para escrever código que atende aos requisitos de confiabilidade.</span><span class="sxs-lookup"><span data-stu-id="90565-116">Provides guidelines for writing code that meets reliability requirements.</span></span>  
  
 [<span data-ttu-id="90565-117">Regiões de execução restrita</span><span class="sxs-lookup"><span data-stu-id="90565-117">Constrained Execution Regions</span></span>](constrained-execution-regions.md)  
 <span data-ttu-id="90565-118">Descreve a função e o comportamento de CERs (regiões de execução restrita).</span><span class="sxs-lookup"><span data-stu-id="90565-118">Describes the function and behavior of constrained execution regions (CERs).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="90565-119">Referência</span><span class="sxs-lookup"><span data-stu-id="90565-119">Reference</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
