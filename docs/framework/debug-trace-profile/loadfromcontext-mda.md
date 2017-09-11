---
title: MDA loadFromContext
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
caps.latest.revision: 8
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d693272adeb0b1bcfea196edb1a23e8b448516cb
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="loadfromcontext-mda"></a><span data-ttu-id="0c773-102">MDA loadFromContext</span><span class="sxs-lookup"><span data-stu-id="0c773-102">loadFromContext MDA</span></span>
<span data-ttu-id="0c773-103">O MDA (Assistente de Depuração Gerenciado) de `loadFromContext` é ativado se um assembly é carregado no contexto `LoadFrom`.</span><span class="sxs-lookup"><span data-stu-id="0c773-103">The `loadFromContext` managed debugging assistant (MDA) is activated if an assembly is loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="0c773-104">Essa situação pode ocorrer como resultado da chamar <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName> ou outros métodos semelhantes.</span><span class="sxs-lookup"><span data-stu-id="0c773-104">This situation can occur as a result of calling <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName> or other similar methods.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="0c773-105">Sintomas</span><span class="sxs-lookup"><span data-stu-id="0c773-105">Symptoms</span></span>  
 <span data-ttu-id="0c773-106">O uso de alguns métodos de carregador pode resultar em assemblies que estão sendo carregados no contexto `LoadFrom`.</span><span class="sxs-lookup"><span data-stu-id="0c773-106">The use of some loader methods can result in assemblies being loaded in the `LoadFrom` context.</span></span> <span data-ttu-id="0c773-107">O uso desse contexto pode resultar em comportamento inesperado para serialização, conversão e resolução de dependência.</span><span class="sxs-lookup"><span data-stu-id="0c773-107">The use of this context can result in unexpected behavior for serialization, casting, and dependency resolution.</span></span> <span data-ttu-id="0c773-108">Em geral, é recomendável que os assemblies sejam carregados no contexto `Load` para evitar esses problemas.</span><span class="sxs-lookup"><span data-stu-id="0c773-108">In general, it is recommended that assemblies be loaded into the `Load` context to avoid these problems.</span></span> <span data-ttu-id="0c773-109">É difícil determinar qual contexto de um assembly foi carregado sem esse MDA.</span><span class="sxs-lookup"><span data-stu-id="0c773-109">It is difficult to determine which context an assembly has been loaded into without this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="0c773-110">Causa</span><span class="sxs-lookup"><span data-stu-id="0c773-110">Cause</span></span>  
 <span data-ttu-id="0c773-111">Em geral, um assembly foi carregado para o contexto de `LoadFrom` se ele foi carregado de um caminho fora do contexto `Load`, tal como o cache de assembly global ou a propriedade <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="0c773-111">Generally, an assembly was loaded into the `LoadFrom` context if it was loaded from a path outside the `Load` context, such as the global assembly cache or the <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=fullName> property.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="0c773-112">Resolução</span><span class="sxs-lookup"><span data-stu-id="0c773-112">Resolution</span></span>  
 <span data-ttu-id="0c773-113">Configure os aplicativos de modo que as chamadas <xref:System.Reflection.Assembly.LoadFrom%2A> não sejam mais necessárias.</span><span class="sxs-lookup"><span data-stu-id="0c773-113">Configure applications such that <xref:System.Reflection.Assembly.LoadFrom%2A> calls are no longer needed.</span></span> <span data-ttu-id="0c773-114">Você pode usar as seguintes técnicas para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="0c773-114">You can use the following techniques for doing so:</span></span>  
  
-   <span data-ttu-id="0c773-115">Instale assemblies no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="0c773-115">Install assemblies in the global assembly cache.</span></span>  
  
-   <span data-ttu-id="0c773-116">Coloque os assemblies no diretório <xref:System.AppDomainSetup.ApplicationBase%2A> para o <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="0c773-116">Place assemblies in the <xref:System.AppDomainSetup.ApplicationBase%2A> directory for the <xref:System.AppDomain>.</span></span> <span data-ttu-id="0c773-117">No caso do domínio padrão, o diretório <xref:System.AppDomainSetup.ApplicationBase%2A> é aquele que contém o arquivo executável que iniciou o processo.</span><span class="sxs-lookup"><span data-stu-id="0c773-117">In the case of the default domain, the <xref:System.AppDomainSetup.ApplicationBase%2A> directory is the one that contains the executable file that started the process.</span></span> <span data-ttu-id="0c773-118">Isso também poderá exigir a criação de um novo <xref:System.AppDomain>, se não for conveniente mover o assembly.</span><span class="sxs-lookup"><span data-stu-id="0c773-118">This might also require creating a new <xref:System.AppDomain> if it is not convenient to move the assembly.</span></span>  
  
-   <span data-ttu-id="0c773-119">Adicione um caminho de sondagem para o arquivo (.config) de configuração do aplicativo ou para domínios de aplicativo secundários se assemblies dependentes estão em diretórios filhos em relação ao executável.</span><span class="sxs-lookup"><span data-stu-id="0c773-119">Add a probing path to your application configuration (.config) file or to secondary  application domains if dependent assemblies are in child directories relative to the executable.</span></span>  
  
 <span data-ttu-id="0c773-120">Em cada caso, o código pode ser alterado para usar o método <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="0c773-120">In each case, the code can be changed to use the <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="0c773-121">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="0c773-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="0c773-122">O MDA não tem nenhum efeito no CLR.</span><span class="sxs-lookup"><span data-stu-id="0c773-122">The MDA does not have any effect on the CLR.</span></span> <span data-ttu-id="0c773-123">Informa o contexto que foi usado como resultado de uma solicitação de carregamento.</span><span class="sxs-lookup"><span data-stu-id="0c773-123">It reports the context that was used as a result of a load request.</span></span>  
  
## <a name="output"></a><span data-ttu-id="0c773-124">Saída</span><span class="sxs-lookup"><span data-stu-id="0c773-124">Output</span></span>  
 <span data-ttu-id="0c773-125">O MDA informa que o assembly foi carregado para o contexto `LoadFrom`.</span><span class="sxs-lookup"><span data-stu-id="0c773-125">The MDA reports that the assembly was loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="0c773-126">Especifica o nome simples do assembly e o caminho.</span><span class="sxs-lookup"><span data-stu-id="0c773-126">It specifies the simple name of the assembly and the path.</span></span> <span data-ttu-id="0c773-127">Também sugere atenuantes para evitar o uso do contexto `LoadFrom`.</span><span class="sxs-lookup"><span data-stu-id="0c773-127">It also suggests mitigations to avoid using the `LoadFrom` context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="0c773-128">Configuração</span><span class="sxs-lookup"><span data-stu-id="0c773-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="0c773-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0c773-129">Example</span></span>  
 <span data-ttu-id="0c773-130">O seguinte exemplo de código demonstra uma situação que pode ativar esse MDA:</span><span class="sxs-lookup"><span data-stu-id="0c773-130">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
```  
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // The following call caused the LoadFrom context to be used  
            // because the assembly is loaded using LoadFrom and the path is   
            // located outside of the Load context probing path.   
            Assembly.LoadFrom(@"C:\Text\Test.dll");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0c773-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c773-131">See Also</span></span>  
 [<span data-ttu-id="0c773-132">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="0c773-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

