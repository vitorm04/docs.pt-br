---
title: Migrando seu aplicativo da Windows Store para .NET Nativo
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ce23d66f79f94af74250cff137499f6c8b1582ac
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2018
---
# <a name="migrating-your-windows-store-app-to-net-native"></a><span data-ttu-id="cb6a6-102">Migrando seu aplicativo da Windows Store para .NET Nativo</span><span class="sxs-lookup"><span data-stu-id="cb6a6-102">Migrating Your Windows Store App to .NET Native</span></span>
[!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="cb6a6-103"> fornece compilação estática dos aplicativos na Windows Store ou no computador do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-103"> provides static compilation of apps in the Windows Store or on the developer’s computer.</span></span> <span data-ttu-id="cb6a6-104">Isso difere da compilação dinâmica realizada para Aplicativos da Windows Store pelo compilador JIT (just-in-time) ou o [Gerador de Imagem Nativa (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-104">This differs from the dynamic compilation performed for Windows Store apps by the just-in-time (JIT) compiler or the [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) on the device.</span></span> <span data-ttu-id="cb6a6-105">Apesar das diferenças, o [!INCLUDE[net_native](../../../includes/net-native-md.md)] tenta manter a compatibilidade com os [.NET para aplicativos da Windows Store](http://msdn.microsoft.com/library/windows/apps/br230302.aspx).</span><span class="sxs-lookup"><span data-stu-id="cb6a6-105">Despite the differences, [!INCLUDE[net_native](../../../includes/net-native-md.md)] tries to maintain compatibility with the [.NET for Windows Store apps](http://msdn.microsoft.com/library/windows/apps/br230302.aspx).</span></span> <span data-ttu-id="cb6a6-106">Em geral, as coisas que funcionam em aplicativos do .NET para Windows Store também funcionam com [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb6a6-106">For the most part, things that work on the .NET for Windows Store apps also work with [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  <span data-ttu-id="cb6a6-107">No entanto, em alguns casos, você pode encontrar alterações de comportamento.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-107">However, in some cases, you may encounter behavioral changes.</span></span> <span data-ttu-id="cb6a6-108">Este documento descreve essas diferenças entre os aplicativos padrão do .NET para Windows Store e o [!INCLUDE[net_native](../../../includes/net-native-md.md)] nas seguintes áreas:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-108">This document discusses these differences between the standard .NET for Windows Store apps and [!INCLUDE[net_native](../../../includes/net-native-md.md)] in the following areas:</span></span>  
  
-   [<span data-ttu-id="cb6a6-109">Diferenças de tempo de execução geral</span><span class="sxs-lookup"><span data-stu-id="cb6a6-109">General runtime differences</span></span>](#Runtime)  
  
-   [<span data-ttu-id="cb6a6-110">Diferenças de programação dinâmica</span><span class="sxs-lookup"><span data-stu-id="cb6a6-110">Dynamic programming differences</span></span>](#Dynamic)  
  
-   [<span data-ttu-id="cb6a6-111">Outras diferenças relacionadas à reflexão</span><span class="sxs-lookup"><span data-stu-id="cb6a6-111">Other reflection-related differences</span></span>](#Reflection)  
  
-   [<span data-ttu-id="cb6a6-112">Cenários e APIs sem suporte</span><span class="sxs-lookup"><span data-stu-id="cb6a6-112">Unsupported scenarios and APIs</span></span>](#Unsupported)  
  
-   [<span data-ttu-id="cb6a6-113">Diferenças do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cb6a6-113">Visual Studio differences</span></span>](#VS)  
  
<a name="Runtime"></a>   
## <a name="general-runtime-differences"></a><span data-ttu-id="cb6a6-114">Diferenças de tempo de execução geral</span><span class="sxs-lookup"><span data-stu-id="cb6a6-114">General runtime differences</span></span>  
  
-   <span data-ttu-id="cb6a6-115">Exceções, como <xref:System.TypeLoadException>, que são geradas pelo compilador JIT quando um aplicativo é executado no CLR (common language runtime), geralmente resulta em erros de tempo de compilação quando processados por [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb6a6-115">Exceptions, such as <xref:System.TypeLoadException>, that are thrown by the JIT compiler when an app runs on the common language runtime (CLR) generally result in compile-time errors when processed by [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
-   <span data-ttu-id="cb6a6-116">Não chame o método <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> de um thread de interface do usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-116">Don't call the <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method from an app's UI thread.</span></span> <span data-ttu-id="cb6a6-117">Isso pode resultar em um deadlock em [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb6a6-117">This can result in a deadlock on [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
-   <span data-ttu-id="cb6a6-118">Não conte com ordenação de invocação do construtor de classe estática.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-118">Don't rely on static class constructor invocation ordering.</span></span> <span data-ttu-id="cb6a6-119">No [!INCLUDE[net_native](../../../includes/net-native-md.md)], a ordem de invocação é diferente da ordem do tempo de execução padrão.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-119">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], the invocation order is different from the order on the standard runtime.</span></span> <span data-ttu-id="cb6a6-120">(Mesmo com o tempo de execução padrão, você não deve confiar na ordem de execução de construtores de classe estáticos.)</span><span class="sxs-lookup"><span data-stu-id="cb6a6-120">(Even with the standard runtime, you shouldn't rely on the order of execution of static class constructors.)</span></span>  
  
-   <span data-ttu-id="cb6a6-121">Loops infinitos sem fazer uma chamada (por exemplo, `while(true);`) em qualquer thread interromper o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-121">Infinite looping without making a call (for example, `while(true);`) on any thread may bring the app to a halt.</span></span> <span data-ttu-id="cb6a6-122">Da mesma forma, esperas grandes ou infinitas podem interromper o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-122">Similarly, large or infinite waits may bring the app to a halt.</span></span>  
  
-   <span data-ttu-id="cb6a6-123">Certos ciclos de inicialização genéricos não geram exceções em [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb6a6-123">Certain generic initialization cycles don't throw exceptions in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="cb6a6-124">Por exemplo, o código a seguir gera uma exceção <xref:System.TypeLoadException> no CLR padrão.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-124">For example, the following code throws a <xref:System.TypeLoadException> exception on the standard CLR.</span></span> <span data-ttu-id="cb6a6-125">No [!INCLUDE[net_native](../../../includes/net-native-md.md)], não.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-125">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], it doesn't.</span></span>  
  
     [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]  
  
-   <span data-ttu-id="cb6a6-126">Em alguns casos, o [!INCLUDE[net_native](../../../includes/net-native-md.md)] fornece diferentes implementações das Bibliotecas de Classe do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-126">In some cases, [!INCLUDE[net_native](../../../includes/net-native-md.md)] provides different implementations of .NET Framework class libraries.</span></span> <span data-ttu-id="cb6a6-127">Um objeto retornado de um método sempre implementará os membros do tipo retornado.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-127">An object returned from a method will always implement the members of the returned type.</span></span> <span data-ttu-id="cb6a6-128">No entanto, desde que sua implementação de backup seja diferente, você não poderá convertê-lo para o mesmo conjunto de tipos como realizado em outras plataformas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-128">However, since its backing implementation is different, you may not be able to cast it to the same set of types as you could on other .NET Framework platforms.</span></span> <span data-ttu-id="cb6a6-129">Por exemplo, em alguns casos, você não poderá converter o objeto de interface <xref:System.Collections.Generic.IEnumerable%601> retornado por métodos como <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> ou <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> para `T[]`.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-129">For example, in some cases, you may not be able to cast the <xref:System.Collections.Generic.IEnumerable%601> interface object returned by methods such as <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> or <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> to `T[]`.</span></span>  
  
-   <span data-ttu-id="cb6a6-130">O cache de WinInet não é habilitado por padrão em aplicativos .NET para Windows Store, mas é habilitado no [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb6a6-130">The WinInet cache isn't enabled by default on .NET for Windows Store apps, but it is on [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="cb6a6-131">Isso melhora o desempenho, mas tem implicações de conjunto de trabalho.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-131">This improves performance but has working set implications.</span></span> <span data-ttu-id="cb6a6-132">Nenhuma ação do desenvolvedor é necessária.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-132">No developer action is necessary.</span></span>  
  
<a name="Dynamic"></a>   
## <a name="dynamic-programming-differences"></a><span data-ttu-id="cb6a6-133">Diferenças de programação dinâmica</span><span class="sxs-lookup"><span data-stu-id="cb6a6-133">Dynamic programming differences</span></span>  
 <span data-ttu-id="cb6a6-134">O [!INCLUDE[net_native](../../../includes/net-native-md.md)] vincula estaticamente no código do .NET Framework para criar o código de aplicativo local para máximo desempenho.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-134">[!INCLUDE[net_native](../../../includes/net-native-md.md)] statically links in code from the .NET Framework to make the code app-local for maximum performance.</span></span> <span data-ttu-id="cb6a6-135">No entanto, os tamanhos binários precisam permanecer pequenos para que todo o .NET Framework não seja trazido.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-135">However, binary sizes have to remain small, so the entire .NET Framework can't be brought in.</span></span> <span data-ttu-id="cb6a6-136">O compilador [!INCLUDE[net_native](../../../includes/net-native-md.md)] resolve esta limitação usando um redutor de dependência que remove referências ao código não usado.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-136">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler resolves this limitation by using a dependency reducer that removes references to unused code.</span></span> <span data-ttu-id="cb6a6-137">No entanto, o [!INCLUDE[net_native](../../../includes/net-native-md.md)] pode não manter ou gerar algumas informações de tipo e código quando elas não podem ser deduzidas estaticamente no tempo de compilação, mas em vez disso, são recuperadas dinamicamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-137">However, [!INCLUDE[net_native](../../../includes/net-native-md.md)] might not maintain or generate some type information and code when that information can't be inferred statically at compile time, but instead is retrieved dynamically at runtime.</span></span>  
  
 <span data-ttu-id="cb6a6-138">O [!INCLUDE[net_native](../../../includes/net-native-md.md)] habilita a reflexão e programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-138">[!INCLUDE[net_native](../../../includes/net-native-md.md)] does enable reflection and dynamic programming.</span></span> <span data-ttu-id="cb6a6-139">No entanto, nem todos os tipos podem ser marcados para reflexão, porque isso tornaria o tamanho do código gerado grande demais (especialmente porque há suporte para reflexão nas APIs públicas do .NET Framework).</span><span class="sxs-lookup"><span data-stu-id="cb6a6-139">However, not all types can be marked for reflection, because this would make the generated code size too large (especially because reflecting on public APIs in the .NET Framework is supported).</span></span> <span data-ttu-id="cb6a6-140">O compilador [!INCLUDE[net_native](../../../includes/net-native-md.md)] faz escolhas inteligentes sobre quais tipos devem oferecer suporte à reflexão, mantém os metadados e gera código somente para esses tipos.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-140">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler makes smart choices about which types should support reflection, and it keeps the metadata and generates code only for those types.</span></span>  
  
 <span data-ttu-id="cb6a6-141">Por exemplo, a associação de dados necessita de um aplicativo para conseguir mapear nomes de propriedade às funções.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-141">For example, data binding requires an app to be able to map property names to functions.</span></span> <span data-ttu-id="cb6a6-142">Nos aplicativos .NET para Windows Store, o Common Language Runtime usa reflexão automaticamente para fornecer esse recurso para tipos nativos gerenciados e disponíveis publicamente.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-142">In .NET for Windows Store apps, the common language runtime automatically uses reflection to provide this capability for managed types and publicly available native types.</span></span> <span data-ttu-id="cb6a6-143">No [!INCLUDE[net_native](../../../includes/net-native-md.md)], o compilador inclui automaticamente os metadados para tipos aos quais você associa dados.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-143">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], the compiler automatically includes metadata for types to which you bind data.</span></span>  
  
 <span data-ttu-id="cb6a6-144">O compilador do [!INCLUDE[net_native](../../../includes/net-native-md.md)] também pode manipular tipos genéricos comumente usados como <xref:System.Collections.Generic.List%601> e <xref:System.Collections.Generic.Dictionary%602>, que funcionam sem necessitar de quaisquer dicas ou diretivas.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-144">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler can also handle commonly used generic types such as <xref:System.Collections.Generic.List%601> and <xref:System.Collections.Generic.Dictionary%602>, which work without requiring any hints or directives.</span></span> <span data-ttu-id="cb6a6-145">A palavra-chave [dynamic](~/docs/csharp/language-reference/keywords/dynamic.md) também tem suporte dentro de certos limites.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-145">The [dynamic](~/docs/csharp/language-reference/keywords/dynamic.md) keyword is also supported within certain limits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb6a6-146">Você deve testar todos os caminhos de código dinâmico completamente ao realizar a portabilidade do seu aplicativo para [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb6a6-146">You should test all dynamic code paths thoroughly when porting your app to [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="cb6a6-147">A configuração padrão do [!INCLUDE[net_native](../../../includes/net-native-md.md)] é suficiente para a maioria dos desenvolvedores, mas alguns talvez queiram ajustar suas configurações usando um arquivo de diretivas de tempo de execução (.rd.xml).</span><span class="sxs-lookup"><span data-stu-id="cb6a6-147">The default configuration for [!INCLUDE[net_native](../../../includes/net-native-md.md)] is sufficient for most developers, but some developers might want to fine- tune their configurations by using a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="cb6a6-148">Além disso, em alguns casos, o compilador [!INCLUDE[net_native](../../../includes/net-native-md.md)] não consegue determinar quais metadados devem estar disponíveis para reflexão baseia-se em dicas, particularmente nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-148">In addition, in some cases, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler is unable to determine which metadata must be available for reflection and relies on hints, particularly in the following cases:</span></span>  
  
-   <span data-ttu-id="cb6a6-149">Algumas construções <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> e <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> não podem ser determinadas estaticamente.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-149">Some constructs like <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> and <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> can't be determined statically.</span></span>  
  
-   <span data-ttu-id="cb6a6-150">Como o compilador não pode determinar as instanciações, um tipo genérico sobre o qual você deseja refletir deverá ser especificado por diretivas de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-150">Because the compiler can't determine the instantiations, a generic type that you want to reflect on has to be specified by runtime directives.</span></span> <span data-ttu-id="cb6a6-151">Isso não é apenas porque todo o código deve ser incluído, mas sim porque a reflexão em tipos genéricos pode formar um ciclo infinito (por exemplo, quando um método genérico é invocado em um tipo genérico).</span><span class="sxs-lookup"><span data-stu-id="cb6a6-151">This isn't just because all code must be included, but because reflection on generic types can form an infinite cycle (for example, when a generic method is invoked on a generic type).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb6a6-152">Diretivas de tempo de execução são definidas em um arquivo de diretivas de tempo de execução (.rd.xml).</span><span class="sxs-lookup"><span data-stu-id="cb6a6-152">Runtime directives are defined in a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="cb6a6-153">Para obter mais informações sobre como usar essa arquivo, consulte [Introdução](../../../docs/framework/net-native/getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="cb6a6-153">For general information about using this file, see [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md).</span></span> <span data-ttu-id="cb6a6-154">Para obter informações sobre as diretivas de tempo de execução, consulte [Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="cb6a6-154">For information about the runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
 <span data-ttu-id="cb6a6-155">O [!INCLUDE[net_native](../../../includes/net-native-md.md)] também inclui ferramentas de perfil que ajudam o desenvolvedor a determinar quais tipos de fora do conjunto padrão devem suportar a reflexão.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-155">[!INCLUDE[net_native](../../../includes/net-native-md.md)] also includes profiling tools that help the developer determine which types outside the default set should support reflection.</span></span>  
  
<a name="Reflection"></a>   
## <a name="other-reflection-related-differences"></a><span data-ttu-id="cb6a6-156">Outras diferenças relacionadas à reflexão</span><span class="sxs-lookup"><span data-stu-id="cb6a6-156">Other reflection-related differences</span></span>  
 <span data-ttu-id="cb6a6-157">Há uma série de outras diferenças individuais do comportamento relacionadas à reflexão entre aplicativos .NET para Windows Store e o [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb6a6-157">There are a number of other individual reflection-related differences in behavior between the .NET for Windows Store apps and [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="cb6a6-158">No [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-158">In [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span></span>  
  
-   <span data-ttu-id="cb6a6-159">Não há suporte para reflexão privada sobre tipos e membros da biblioteca de classes do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-159">Private reflection over types and members in the .NET Framework class library is not supported.</span></span> <span data-ttu-id="cb6a6-160">No entanto, é possível refletir sobre seus próprios tipos e membros privados, bem como tipos e membros em bibliotecas de terceiros.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-160">You can, however, reflect over your own private types and members, as well as types and members in third-party libraries.</span></span>  
  
-   <span data-ttu-id="cb6a6-161">A propriedade <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> retorna `false` corretamente para um objeto <xref:System.Reflection.ParameterInfo> que representa um valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-161">The <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> property correctly returns `false` for a <xref:System.Reflection.ParameterInfo> object that represents a return value.</span></span> <span data-ttu-id="cb6a6-162">Nos aplicativos .NET para Windows Store, ele retorna `true`.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-162">In the .NET for Windows Store apps, it returns `true`.</span></span> <span data-ttu-id="cb6a6-163">A Linguagem intermediária (IL) não oferece suporte a isso diretamente e interpretações são deixada para a linguagem.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-163">Intermediate language (IL) doesn’t support this directly, and interpretation is left to the language.</span></span>  
  
-   <span data-ttu-id="cb6a6-164">Membros públicos nas estruturas <xref:System.RuntimeFieldHandle> e <xref:System.RuntimeMethodHandle> não são suportadas.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-164">Public members on the <xref:System.RuntimeFieldHandle> and <xref:System.RuntimeMethodHandle> structures aren't supported.</span></span> <span data-ttu-id="cb6a6-165">Esses tipos são suportados apenas para LINQ, árvores de expressão e inicialização de matriz estática.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-165">These types are supported only for LINQ, expression trees, and static array initialization.</span></span>  
  
-   <span data-ttu-id="cb6a6-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> e <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> incluem membros ocultos em classes base e, portanto, podem ser substituídos sem substituições explícitas.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> and <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> include hidden members in base classes and thus may be overridden without explicit overrides.</span></span> <span data-ttu-id="cb6a6-167">Isso também é verdadeiro para outros métodos [RuntimeReflectionExtensions.GetRuntime\*](http://msdn.microsoft.com/library/system.reflection.runtimereflectionextensions_methods.aspx).</span><span class="sxs-lookup"><span data-stu-id="cb6a6-167">This is also true of other [RuntimeReflectionExtensions.GetRuntime\*](http://msdn.microsoft.com/library/system.reflection.runtimereflectionextensions_methods.aspx) methods.</span></span>  
  
-   <span data-ttu-id="cb6a6-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> e <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> não falham quando você tentar criar certas combinações (por exemplo, uma matriz de byrefs).</span><span class="sxs-lookup"><span data-stu-id="cb6a6-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> don't fail when you try to create certain combinations (for example, an array of byrefs).</span></span>  
  
-   <span data-ttu-id="cb6a6-169">Você não pode usar reflexão para invocar os membros que têm parâmetros de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-169">You can't use reflection to invoke members that have pointer parameters.</span></span>  
  
-   <span data-ttu-id="cb6a6-170">Você não pode usar reflexão para obter ou definir um campo de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-170">You can't use reflection to get or set a pointer field.</span></span>  
  
-   <span data-ttu-id="cb6a6-171">Quando a contagem de argumentos está incorreta e o tipo de um dos argumentos está incorreto, o [!INCLUDE[net_native](../../../includes/net-native-md.md)] gera um <xref:System.ArgumentException> em vez de um <xref:System.Reflection.TargetParameterCountException>.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-171">When the argument count is wrong and the type of one of the arguments is incorrect, [!INCLUDE[net_native](../../../includes/net-native-md.md)] throws an <xref:System.ArgumentException> instead of a <xref:System.Reflection.TargetParameterCountException>.</span></span>  
  
-   <span data-ttu-id="cb6a6-172">A serialização binária de exceções geralmente não é suportada.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-172">Binary serialization of exceptions is generally not supported.</span></span> <span data-ttu-id="cb6a6-173">Como resultado, objetos não serializáveis não podem ser adicionados ao dicionário <xref:System.Exception.Data%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-173">As a result, non-serializable objects can be added to the <xref:System.Exception.Data%2A?displayProperty=nameWithType> dictionary.</span></span>  
  
<a name="Unsupported"></a>   
## <a name="unsupported-scenarios-and-apis"></a><span data-ttu-id="cb6a6-174">Cenários e APIs sem suporte</span><span class="sxs-lookup"><span data-stu-id="cb6a6-174">Unsupported scenarios and APIs</span></span>  
 <span data-ttu-id="cb6a6-175">As seções a seguir listam cenários não suportados e APIs de desenvolvimento geral, interoperabilidade e tecnologias como HTTPClient e Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="cb6a6-175">The following sections list unsupported scenarios and APIs for general development, interop, and technologies such as HTTPClient and Windows Communication Foundation (WCF):</span></span>  
  
-   [<span data-ttu-id="cb6a6-176">Desenvolvimento geral</span><span class="sxs-lookup"><span data-stu-id="cb6a6-176">General development</span></span>](#General)  
  
-   [<span data-ttu-id="cb6a6-177">HttpClient</span><span class="sxs-lookup"><span data-stu-id="cb6a6-177">HttpClient</span></span>](#HttpClient)  
  
-   [<span data-ttu-id="cb6a6-178">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="cb6a6-178">Interop</span></span>](#Interop)  
  
-   [<span data-ttu-id="cb6a6-179">APIs sem suporte</span><span class="sxs-lookup"><span data-stu-id="cb6a6-179">Unsupported APIs</span></span>](#APIs)  
  
<a name="General"></a>   
### <a name="general-development-differences"></a><span data-ttu-id="cb6a6-180">Diferenças de desenvolvimento geral</span><span class="sxs-lookup"><span data-stu-id="cb6a6-180">General development differences</span></span>  
 <span data-ttu-id="cb6a6-181">**Tipos de valor**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-181">**Value types**</span></span>  
  
-   <span data-ttu-id="cb6a6-182">Se você substituir os métodos <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> e <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> para um tipo de valor, não chame as implementações de classe base.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-182">If you override the <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> and <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> methods for a value type, don't call the base class implementations.</span></span> <span data-ttu-id="cb6a6-183">Em aplicativos .NET para Windows Store, esses métodos dependem de reflexão.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-183">In .NET for Windows Store apps, these methods rely on reflection.</span></span> <span data-ttu-id="cb6a6-184">No tempo de compilação, o [!INCLUDE[net_native](../../../includes/net-native-md.md)] gera uma implementação que não depende de reflexão no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-184">At compile time, [!INCLUDE[net_native](../../../includes/net-native-md.md)] generates an implementation that doesn't rely on runtime reflection.</span></span> <span data-ttu-id="cb6a6-185">Isso significa que se você não substituir esses dois métodos, eles funcionarão conforme o esperado, porque [!INCLUDE[net_native](../../../includes/net-native-md.md)] gera a implementação no tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-185">This means that if you don't override these two methods, they will work as expected, because [!INCLUDE[net_native](../../../includes/net-native-md.md)] generates the implementation at compile time.</span></span> <span data-ttu-id="cb6a6-186">No entanto, substituir esses métodos, mas chamar a implementação de classe base, resulta em uma exceção.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-186">However, overriding these methods but calling the base class implementation results in an exception.</span></span>  
  
-   <span data-ttu-id="cb6a6-187">Não há suporte para tipos de valor maior do que um megabyte.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-187">Value types larger than one megabyte aren't supported.</span></span>  
  
-   <span data-ttu-id="cb6a6-188">Tipos de valor não podem ter um construtor padrão em [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb6a6-188">Value types can't have a default constructor in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="cb6a6-189">(C# e Visual Basic proíbem construtores padrão em tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-189">(C# and Visual Basic prohibit default constructors on value types.</span></span> <span data-ttu-id="cb6a6-190">No entanto, eles podem ser criados em IL.)</span><span class="sxs-lookup"><span data-stu-id="cb6a6-190">However, these can be created in IL.)</span></span>  
  
 <span data-ttu-id="cb6a6-191">**Matrizes**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-191">**Arrays**</span></span>  
  
-   <span data-ttu-id="cb6a6-192">Não há suporte para matrizes com um limite inferior diferente de zero.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-192">Arrays with a lower bound other than zero aren't supported.</span></span> <span data-ttu-id="cb6a6-193">Normalmente, esses conjuntos são criados ao chamar a sobrecarga <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-193">Typically, these arrays are created by calling the <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> overload.</span></span>  
  
-   <span data-ttu-id="cb6a6-194">A criação dinâmica de matrizes multidimensionais não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-194">Dynamic creation of multidimensional arrays isn't supported.</span></span> <span data-ttu-id="cb6a6-195">Essas matrizes geralmente são criados chamando uma sobrecarga do método <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> que inclui um parâmetro `lengths` ou chamando o método <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-195">Such arrays are typically created by calling an overload of the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method that includes a `lengths` parameter, or by calling the <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="cb6a6-196">Não há suporte para matrizes multidimensionais com quatro ou mais dimensões, ou seja, com valor da propriedade <xref:System.Array.Rank%2A?displayProperty=nameWithType> quatro ou superior.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-196">Multidimensional arrays that have four or more dimensions aren't supported; that is, their <xref:System.Array.Rank%2A?displayProperty=nameWithType> property value is four or greater.</span></span> <span data-ttu-id="cb6a6-197">Use [matrizes denteadas](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (uma matriz de matrizes) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-197">Use [jagged arrays](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (an array of arrays) instead.</span></span> <span data-ttu-id="cb6a6-198">Por exemplo, `array[x,y,z]` é inválido, mas `array[x][y][z]` não é.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-198">For example, `array[x,y,z]` is invalid, but `array[x][y][z]` isn't.</span></span>  
  
-   <span data-ttu-id="cb6a6-199">Variação de matrizes multidimensionais não é suportada e causa uma exceção <xref:System.InvalidCastException> no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-199">Variance for multidimensional arrays isn't supported and causes an <xref:System.InvalidCastException> exception at run time.</span></span>  
  
 <span data-ttu-id="cb6a6-200">**Genéricos**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-200">**Generics**</span></span>  
  
-   <span data-ttu-id="cb6a6-201">A expansão do tipo genérico infinito resulta em um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-201">Infinite generic type expansion results in a compiler error.</span></span> <span data-ttu-id="cb6a6-202">Por exemplo, esse código falha ao compilar:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-202">For example, this code fails to compile:</span></span>  
  
     [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]  
  
 <span data-ttu-id="cb6a6-203">**Ponteiros**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-203">**Pointers**</span></span>  
  
-   <span data-ttu-id="cb6a6-204">Não há suporte para matrizes de ponteiros.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-204">Arrays of pointers aren't supported.</span></span>  
  
-   <span data-ttu-id="cb6a6-205">Você não pode usar reflexão para obter ou definir um campo de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-205">You can't use reflection to get or set a pointer field.</span></span>  
  
 <span data-ttu-id="cb6a6-206">**Serialização**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-206">**Serialization**</span></span>  
  
 <span data-ttu-id="cb6a6-207">O atributo <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> não é suportado.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-207">The <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> attribute isn't supported.</span></span> <span data-ttu-id="cb6a6-208">Use o atributo <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-208">Use the <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> attribute instead.</span></span>  
  
 <span data-ttu-id="cb6a6-209">**Recursos**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-209">**Resources**</span></span>  
  
 <span data-ttu-id="cb6a6-210">O uso de recursos localizados com a classe <xref:System.Diagnostics.Tracing.EventSource> não é suportado.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-210">The use of localized resources with the <xref:System.Diagnostics.Tracing.EventSource> class isn't supported.</span></span> <span data-ttu-id="cb6a6-211">A propriedade <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> não define os recursos localizados.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-211">The <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> property doesn't define localized resources.</span></span>  
  
 <span data-ttu-id="cb6a6-212">**Delegados**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-212">**Delegates**</span></span>  
  
 <span data-ttu-id="cb6a6-213">`Delegate.BeginInvoke` e `Delegate.EndInvoke` não são suportados.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-213">`Delegate.BeginInvoke` and `Delegate.EndInvoke` aren't supported.</span></span>  
  
 <span data-ttu-id="cb6a6-214">**Async**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-214">**Async**</span></span>  
  
 <span data-ttu-id="cb6a6-215">A lógica de threading em sobrecargas da tarefa IAsync não é suportada.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-215">Threading logic in overloads of Task IAsync isn't supported.</span></span>  
  
 <span data-ttu-id="cb6a6-216">**APIs diversas**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-216">**Miscellaneous APIs**</span></span>  
  
-   <span data-ttu-id="cb6a6-217">A propriedade <xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=nameWithType> gera uma exceção <xref:System.PlatformNotSupportedException> se um atributo <xref:System.Runtime.InteropServices.GuidAttribute> não for aplicado ao tipo.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-217">The <xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=nameWithType> property throws a <xref:System.PlatformNotSupportedException> exception if a <xref:System.Runtime.InteropServices.GuidAttribute> attribute isn't applied to the type.</span></span> <span data-ttu-id="cb6a6-218">O GUID é usado principalmente para suporte a COM.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-218">The GUID is used primarily for COM support.</span></span>  
  
-   <span data-ttu-id="cb6a6-219">O método <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> analisa corretamente as cadeias de caracteres que contêm datas curtas em [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb6a6-219">The <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> method correctly parses strings that contain short dates in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="cb6a6-220">Contudo, ele não mantém a compatibilidade com as alterações na análise de data e hora descritas no artigos da Base de Dados de Conhecimento Microsoft [KB2803771](http://support.microsoft.com/kb/2803771) e [KB2803755](http://support.microsoft.com/kb/2803755).</span><span class="sxs-lookup"><span data-stu-id="cb6a6-220">However, it doesn't maintain compatibility with the changes in date and time parsing described in the Microsoft Knowledge Base articles [KB2803771](http://support.microsoft.com/kb/2803771) and [KB2803755](http://support.microsoft.com/kb/2803755).</span></span>  
  
-   <span data-ttu-id="cb6a6-221"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` é arredondado corretamente em [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb6a6-221"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` is correctly rounded in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="cb6a6-222">Em algumas versões do CLR, a cadeia de caracteres de resultado é truncada em vez de arredondada.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-222">In some versions of the CLR, the result string is truncated instead of rounded.</span></span>  
  
<a name="HttpClient"></a>   
### <a name="httpclient-differences"></a><span data-ttu-id="cb6a6-223">Diferenças do HttpClient</span><span class="sxs-lookup"><span data-stu-id="cb6a6-223">HttpClient differences</span></span>  
 <span data-ttu-id="cb6a6-224">Em [!INCLUDE[net_native](../../../includes/net-native-md.md)], a classe <xref:System.Net.Http.HttpClientHandler> usa internamente WinINet (por meio da classe [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx)) em vez das classes <xref:System.Net.WebRequest> e <xref:System.Net.WebResponse> usadas no .NET padrão para Aplicativos da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-224">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], the <xref:System.Net.Http.HttpClientHandler> class internally uses WinINet (through the [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) class) instead of the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes used in the standard .NET for Windows Store apps.</span></span>  <span data-ttu-id="cb6a6-225">O WinINet não oferece suporte a todas as opções de configuração que a classe <xref:System.Net.Http.HttpClientHandler> suporta.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-225">WinINet doesn't support all the configuration options that the <xref:System.Net.Http.HttpClientHandler> class supports.</span></span>  <span data-ttu-id="cb6a6-226">Portanto:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-226">As a result:</span></span>  
  
-   <span data-ttu-id="cb6a6-227">Algumas das propriedades do recurso em <xref:System.Net.Http.HttpClientHandler> retornam `false` em [!INCLUDE[net_native](../../../includes/net-native-md.md)], considerando que retornam `true` nos aplicativos padrão .NET para Windows Store.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-227">Some of the capability properties on <xref:System.Net.Http.HttpClientHandler> return `false` on [!INCLUDE[net_native](../../../includes/net-native-md.md)], whereas they return `true` in the standard .NET for Windows Store apps.</span></span>  
  
-   <span data-ttu-id="cb6a6-228">Algumas das propriedades de configuração dos acessadores `get` sempre retornam um valor fixo no [!INCLUDE[net_native](../../../includes/net-native-md.md)] diferente do valor configurável padrão nos aplicativos .NET da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-228">Some of the configuration property `get` accessors always return a fixed value on [!INCLUDE[net_native](../../../includes/net-native-md.md)] that is different than the default configurable value in .NET for Windows Store apps.</span></span>  
  
 <span data-ttu-id="cb6a6-229">Algumas diferenças comportamentais adicionais são abrangidas nas subseções a seguir.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-229">Some additional behavior differences are covered in the following subsections.</span></span>  
  
 <span data-ttu-id="cb6a6-230">**Proxy**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-230">**Proxy**</span></span>  
  
 <span data-ttu-id="cb6a6-231">A classe [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) não dá suporte para configurar ou substituir o proxy por solicitação.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-231">The [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) class doesn’t support configuring or overriding the proxy on a per-request basis.</span></span>  <span data-ttu-id="cb6a6-232">Isso significa que todas as solicitações no [!INCLUDE[net_native](../../../includes/net-native-md.md)] usam o servidor de proxy configurado pelo sistema ou nenhum servidor de proxy, dependendo do valor da propriedade <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-232">This means that all requests on [!INCLUDE[net_native](../../../includes/net-native-md.md)] use the system-configured proxy server or no proxy server, depending on the value of the <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="cb6a6-233">Em aplicativos .NET para Windows Store, o servidor proxy é definido pela propriedade <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-233">In .NET for Windows Store apps, the proxy server is defined by the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="cb6a6-234">Em [!INCLUDE[net_native](../../../includes/net-native-md.md)], definir <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> para um valor diferente de `null` gera uma exceção <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-234">On [!INCLUDE[net_native](../../../includes/net-native-md.md)], setting the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> to a value other than `null` throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="cb6a6-235">A propriedade <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> retorna `false` em [!INCLUDE[net_native](../../../includes/net-native-md.md)], considerando que retorna `true` nos aplicativos .NET Framework para Windows Store.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-235">The <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> property returns `false` on [!INCLUDE[net_native](../../../includes/net-native-md.md)], whereas it returns `true` in the standard .NET Framework for Windows Store apps.</span></span>  
  
 <span data-ttu-id="cb6a6-236">**Redirecionamento automático**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-236">**Automatic redirection**</span></span>  
  
 <span data-ttu-id="cb6a6-237">A classe [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) não permite que o número máximo de redirecionamentos automáticos seja configurado.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-237">The [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) class doesn't allow the maximum number of automatic redirections to be configured.</span></span>  <span data-ttu-id="cb6a6-238">O valor da propriedade <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> é 50 por padrão nos aplicativos .NET para Windows Store e pode ser modificada.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-238">The value of the <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> property is 50 by default in the standard .NET for Windows Store apps and can be modified.</span></span> <span data-ttu-id="cb6a6-239">Em [!INCLUDE[net_native](../../../includes/net-native-md.md)], o valor desta propriedade é 10 e tentar modificá-la gera uma exceção <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-239">On [!INCLUDE[net_native](../../../includes/net-native-md.md)], the value of this property is 10, and trying to modify it throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="cb6a6-240">A propriedade <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> retorna `false` em [!INCLUDE[net_native](../../../includes/net-native-md.md)], considerando que retorna `true` em aplicativos .NET para Windows Store.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-240">The <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> property returns `false` on [!INCLUDE[net_native](../../../includes/net-native-md.md)], whereas it returns `true` in .NET for Windows Store apps.</span></span>  
  
 <span data-ttu-id="cb6a6-241">**Descompactação automática**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-241">**Automatic decompression**</span></span>  
  
 <span data-ttu-id="cb6a6-242">Aplicativos .NET para Windows Store permitem definir a propriedade <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> para <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, ambas <xref:System.Net.DecompressionMethods.Deflate> e <xref:System.Net.DecompressionMethods.GZip>, ou <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-242">.NET for Windows Store apps allows you to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> property to <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="cb6a6-243"> somente suporta <xref:System.Net.DecompressionMethods.Deflate> junto com <xref:System.Net.DecompressionMethods.GZip> ou <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-243"> only supports <xref:System.Net.DecompressionMethods.Deflate> together with <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="cb6a6-244">Tentar definir a propriedade <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> para <xref:System.Net.DecompressionMethods.Deflate> ou <xref:System.Net.DecompressionMethods.GZip> sozinho silenciosamente define-a para <xref:System.Net.DecompressionMethods.Deflate> e <xref:System.Net.DecompressionMethods.GZip>.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-244">Trying to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> property to either <xref:System.Net.DecompressionMethods.Deflate> or <xref:System.Net.DecompressionMethods.GZip> alone silently sets it to both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>.</span></span>  
  
 <span data-ttu-id="cb6a6-245">**Cookies**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-245">**Cookies**</span></span>  
  
 <span data-ttu-id="cb6a6-246">A manipulação de cookies é executada simultaneamente por <xref:System.Net.Http.HttpClient> e WinINet.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-246">Cookie handling is performed simultaneously by <xref:System.Net.Http.HttpClient> and WinINet.</span></span>  <span data-ttu-id="cb6a6-247">Os cookies do <xref:System.Net.CookieContainer> são combinados com cookies no cache de cookies do WinINet.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-247">Cookies from the <xref:System.Net.CookieContainer> are combined with cookies in the WinINet cookie cache.</span></span>  <span data-ttu-id="cb6a6-248">Remover um cookie do <xref:System.Net.CookieContainer> impede que <xref:System.Net.Http.HttpClient> envie o cookie, mas se o cookie já foi visto pelo WinINet e os cookies não foram excluídos pelo usuário, o WinINet o envia.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-248">Removing a cookie from <xref:System.Net.CookieContainer> prevents <xref:System.Net.Http.HttpClient> from sending the cookie, but if the cookie was already seen by WinINet, and cookies weren't deleted by the user, WinINet sends it.</span></span>  <span data-ttu-id="cb6a6-249">Não é possível programar a remoção automática de um cookie do WinINet usando a API <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler> ou <xref:System.Net.CookieContainer>.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-249">It isn't possible to programmatically remove a cookie from WinINet by using the <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, or <xref:System.Net.CookieContainer> API.</span></span>  <span data-ttu-id="cb6a6-250">Definir a propriedade <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> para `false` faz com que apenas <xref:System.Net.Http.HttpClient> pare de enviar cookies; o WinINet ainda pode incluir os cookies na solicitação.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-250">Setting the <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> property to `false` causes only <xref:System.Net.Http.HttpClient> to stop sending cookies; WinINet might still include its cookies in the request.</span></span>  
  
 <span data-ttu-id="cb6a6-251">**Credenciais**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-251">**Credentials**</span></span>  
  
 <span data-ttu-id="cb6a6-252">Em aplicativos .NET para Windows Store, as propriedades <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> e <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> funcionam de forma independente.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-252">In .NET for Windows Store apps, the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> properties work independently.</span></span>  <span data-ttu-id="cb6a6-253">Além disso, a propriedade <xref:System.Net.Http.HttpClientHandler.Credentials%2A> aceita qualquer objeto que implemente a interface <xref:System.Net.ICredentials>.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-253">Additionally, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property accepts any object that implements the <xref:System.Net.ICredentials> interface.</span></span>  <span data-ttu-id="cb6a6-254">No [!INCLUDE[net_native](../../../includes/net-native-md.md)], definir a propriedade <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> para `true` faz com que a propriedade <xref:System.Net.Http.HttpClientHandler.Credentials%2A> torne-se `null`.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-254">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], setting the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> property to `true` causes the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property to become `null`.</span></span>  <span data-ttu-id="cb6a6-255">Além disso, a propriedade <xref:System.Net.Http.HttpClientHandler.Credentials%2A> pode ser definida somente para `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A> ou um objeto do tipo <xref:System.Net.NetworkCredential>.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-255">In addition, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property can be set only to `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, or an object of type <xref:System.Net.NetworkCredential>.</span></span>  <span data-ttu-id="cb6a6-256">Atribuir de qualquer outro objeto <xref:System.Net.ICredentials>, sendo o mais popular o <xref:System.Net.CredentialCache>, para a propriedade <xref:System.Net.Http.HttpClientHandler.Credentials%2A>, gera uma <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-256">Assigning any other <xref:System.Net.ICredentials> object, the most popular of which is <xref:System.Net.CredentialCache>, to the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property throws a <xref:System.PlatformNotSupportedException>.</span></span>  
  
 <span data-ttu-id="cb6a6-257">**Outros recursos sem suporte ou não configuráveis**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-257">**Other unsupported or unconfigurable features**</span></span>  
  
 <span data-ttu-id="cb6a6-258">No [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-258">In [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span></span>  
  
-   <span data-ttu-id="cb6a6-259">O valor da propriedade <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> sempre é <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-259">The value of the <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> property is always <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span></span>  <span data-ttu-id="cb6a6-260">Em aplicativos .NET para Windows Store, o padrão é <xref:System.Net.Http.ClientCertificateOption.Manual>.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-260">In .NET for Windows Store apps, the default is <xref:System.Net.Http.ClientCertificateOption.Manual>.</span></span>  
  
-   <span data-ttu-id="cb6a6-261">A propriedade <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> não é configurável.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-261">The <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> property isn't configurable.</span></span>  
  
-   <span data-ttu-id="cb6a6-262">A propriedade <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> sempre é `true`.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-262">The <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> property is always `true`.</span></span>  <span data-ttu-id="cb6a6-263">Em aplicativos .NET para Windows Store, o padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-263">In .NET for Windows Store apps, the default is `false`.</span></span>  
  
-   <span data-ttu-id="cb6a6-264">O cabeçalho `SetCookie2` em respostas será ignorado como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-264">The `SetCookie2` header in responses is ignored as obsolete.</span></span>  
  
<a name="Interop"></a>   
### <a name="interop-differences"></a><span data-ttu-id="cb6a6-265">Diferenças de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="cb6a6-265">Interop differences</span></span>  
 <span data-ttu-id="cb6a6-266">**APIs preteridas**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-266">**Deprecated APIs**</span></span>  
  
 <span data-ttu-id="cb6a6-267">Várias APIs pouco usadas para a interoperabilidade com código gerenciado foram preteridas.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-267">A number of infrequently used APIs for interoperability with managed code have been deprecated.</span></span> <span data-ttu-id="cb6a6-268">Quando usadas com [!INCLUDE[net_native](../../../includes/net-native-md.md)], essas APIs pode gerar uma exceção <xref:System.NotImplementedException> ou <xref:System.PlatformNotSupportedException>, ou resultar em um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-268">When used with [!INCLUDE[net_native](../../../includes/net-native-md.md)], these APIs may throw a <xref:System.NotImplementedException> or <xref:System.PlatformNotSupportedException> exception, or result in a compiler error.</span></span> <span data-ttu-id="cb6a6-269">Em aplicativos .NET para Windows Store, essas APIs são marcadas como obsoletas, embora chamá-las gere um aviso do compilador em vez de um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-269">In .NET for Windows Store apps, these APIs are marked as obsolete, although calling them generates a compiler warning rather than a compiler error.</span></span>  
  
 <span data-ttu-id="cb6a6-270">APIs preteridas para marshaling de `VARIANT`:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-270">Deprecated APIs for `VARIANT` marshaling:</span></span>  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>|  
  
 <span data-ttu-id="cb6a6-271"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> tem suporte, porém gera uma exceção em alguns cenários, por exemplo, quando usado com [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) ou variantes byref.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-271"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> is supported, but it throws an exception in some scenarios, such as when it is used with [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) or byref variants.</span></span>  
  
 <span data-ttu-id="cb6a6-272">APIs preteridas para suporte a [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx):</span><span class="sxs-lookup"><span data-stu-id="cb6a6-272">Deprecated APIs for [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) support:</span></span>  
  
|<span data-ttu-id="cb6a6-273">Tipo</span><span class="sxs-lookup"><span data-stu-id="cb6a6-273">Type</span></span>|<span data-ttu-id="cb6a6-274">Membro</span><span class="sxs-lookup"><span data-stu-id="cb6a6-274">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch>|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual>|  
|<xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>|<span data-ttu-id="cb6a6-275">Atributo não é suportado</span><span class="sxs-lookup"><span data-stu-id="cb6a6-275">Attribute isn't supported</span></span>|  
  
 <span data-ttu-id="cb6a6-276">APIs preteridas para eventos clássicos de COM:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-276">Deprecated APIs for classic COM events:</span></span>  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|  
  
 <span data-ttu-id="cb6a6-277">APIs preteridas na interface do <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>, sem suporte no [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-277">Deprecated APIs in the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, which isn't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span></span>  
  
|<span data-ttu-id="cb6a6-278">Tipo</span><span class="sxs-lookup"><span data-stu-id="cb6a6-278">Type</span></span>|<span data-ttu-id="cb6a6-279">Membro</span><span class="sxs-lookup"><span data-stu-id="cb6a6-279">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>|<span data-ttu-id="cb6a6-280">Todos os membros.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-280">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>|<span data-ttu-id="cb6a6-281">Todos os membros.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-281">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>|<span data-ttu-id="cb6a6-282">Todos os membros.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-282">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=nameWithType>|  
  
 <span data-ttu-id="cb6a6-283">Outros recursos de interoperabilidade sem suporte:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-283">Other unsupported interop features:</span></span>  
  
|<span data-ttu-id="cb6a6-284">Tipo</span><span class="sxs-lookup"><span data-stu-id="cb6a6-284">Type</span></span>|<span data-ttu-id="cb6a6-285">Membro</span><span class="sxs-lookup"><span data-stu-id="cb6a6-285">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>|<span data-ttu-id="cb6a6-286">Todos os membros.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-286">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>|<span data-ttu-id="cb6a6-287">Todos os membros.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-287">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.Currency>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.AsAny>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler>|  
  
 <span data-ttu-id="cb6a6-288">APIs de marshalling raramente usadas:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-288">Rarely used marshalling APIs:</span></span>  
  
|<span data-ttu-id="cb6a6-289">Tipo</span><span class="sxs-lookup"><span data-stu-id="cb6a6-289">Type</span></span>|<span data-ttu-id="cb6a6-290">Membro</span><span class="sxs-lookup"><span data-stu-id="cb6a6-290">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29>|  
  
 <span data-ttu-id="cb6a6-291">**Invocação de plataforma e compatibilidade de interoperabilidade COM**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-291">**Platform invoke and COM interop compatibility**</span></span>  
  
 <span data-ttu-id="cb6a6-292">A maioria dos cenários de invocação de plataforma e interoperabilidade COM ainda são suportados no [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb6a6-292">Most platform invoke and COM interop scenarios are still supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="cb6a6-293">Em especial, toda a interoperabilidade com APIs do Tempo de Execução do Windows (WinRT) APIs e todo o marshaling necessário para o Tempo de Execução do Windows são suportados.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-293">In particular, all interoperability with Windows Runtime (WinRT) APIs and all marshaling required for the Windows Runtime is supported.</span></span> <span data-ttu-id="cb6a6-294">Isso inclui suporte a marshaling para:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-294">This includes marshaling support for:</span></span>  
  
-   <span data-ttu-id="cb6a6-295">Matrizes (incluindo <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span><span class="sxs-lookup"><span data-stu-id="cb6a6-295">Arrays (including <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span></span>  
  
-   `BStr`  
  
-   <span data-ttu-id="cb6a6-296">Representantes</span><span class="sxs-lookup"><span data-stu-id="cb6a6-296">Delegates</span></span>  
  
-   <span data-ttu-id="cb6a6-297">Cadeias de caracteres (Unicode, Ansi e HSTRING)</span><span class="sxs-lookup"><span data-stu-id="cb6a6-297">Strings (Unicode, Ansi, and HSTRING)</span></span>  
  
-   <span data-ttu-id="cb6a6-298">Estruturas (`byref` e `byval`)</span><span class="sxs-lookup"><span data-stu-id="cb6a6-298">Structs (`byref` and `byval`)</span></span>  
  
-   <span data-ttu-id="cb6a6-299">Uniões</span><span class="sxs-lookup"><span data-stu-id="cb6a6-299">Unions</span></span>  
  
-   <span data-ttu-id="cb6a6-300">Identificadores do Win32</span><span class="sxs-lookup"><span data-stu-id="cb6a6-300">Win32 handles</span></span>  
  
-   <span data-ttu-id="cb6a6-301">Todos os constructos do WinRT</span><span class="sxs-lookup"><span data-stu-id="cb6a6-301">All WinRT constructs</span></span>  
  
-   <span data-ttu-id="cb6a6-302">Suporte parcial aos tipos variantes de marshaling.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-302">Partial support for marshaling variant types.</span></span> <span data-ttu-id="cb6a6-303">Há suporte para os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-303">The following are supported:</span></span>  
  
    -   <xref:System.Boolean>  
  
    -   <xref:System.Byte>  
  
    -   <xref:System.Decimal>  
  
    -   <xref:System.Double>  
  
    -   <xref:System.Int16>  
  
    -   <xref:System.Int32>  
  
    -   <xref:System.Int64>  
  
    -   <xref:System.SByte>  
  
    -   <xref:System.Single>  
  
    -   <xref:System.UInt16>  
  
    -   <xref:System.UInt32>  
  
    -   <xref:System.UInt64>  
  
    -   `BStr`  
  
    -   [<span data-ttu-id="cb6a6-304">IUnknown</span><span class="sxs-lookup"><span data-stu-id="cb6a6-304">IUnknown</span></span>](http://msdn.microsoft.com/library/windows/desktop/ms680509.aspx)  
  
 <span data-ttu-id="cb6a6-305">No entanto, o [!INCLUDE[net_native](../../../includes/net-native-md.md)] não oferece suporte aos seguintes:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-305">However, [!INCLUDE[net_native](../../../includes/net-native-md.md)] doesn't support the following:</span></span>  
  
-   <span data-ttu-id="cb6a6-306">Usando os eventos clássicos do COM</span><span class="sxs-lookup"><span data-stu-id="cb6a6-306">Using classic COM events</span></span>  
  
-   <span data-ttu-id="cb6a6-307">Implementando a interface <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> em um tipo gerenciado</span><span class="sxs-lookup"><span data-stu-id="cb6a6-307">Implementing the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface on a managed type</span></span>  
  
-   <span data-ttu-id="cb6a6-308">Implementando a interface [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) em um tipo gerenciado por meio do atributo <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-308">Implementing the [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) interface on a managed type through the <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="cb6a6-309">No entanto, observe que você não pode chamar objetos COM por meio de `IDispatch`, e o objeto gerenciado não pode implementar `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-309">However, note that you can't call COM objects through `IDispatch`, and your managed object can't implement `IDispatch`.</span></span>  
  
 <span data-ttu-id="cb6a6-310">Usar reflexão para invocar um método de invocação de plataforma não é suportado.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-310">Using reflection to invoke a platform invoke method isn't supported.</span></span> <span data-ttu-id="cb6a6-311">Você pode contornar essa limitação envolvendo a chamada de método em outro método e usando reflexão para chamar o wrapper em vez disso.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-311">You can work around this limitation by wrapping the method call in another method and using reflection to call the wrapper instead.</span></span>  
  
<a name="APIs"></a>   
### <a name="other-differences-from-net-apis-for-windows-store-apps"></a><span data-ttu-id="cb6a6-312">Outras diferenças das APIs .NET para Windows Store</span><span class="sxs-lookup"><span data-stu-id="cb6a6-312">Other differences from .NET APIs for Windows Store apps</span></span>  
 <span data-ttu-id="cb6a6-313">Esta seção lista as APIs restantes que não têm suporte em [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb6a6-313">This section lists the remaining APIs that aren't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="cb6a6-314">O maior conjunto de APIs sem suporte são APIs do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="cb6a6-314">The largest set of the unsupported APIs are Windows Communication Foundation (WCF) APIs.</span></span>  
  
 <span data-ttu-id="cb6a6-315">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-315">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span></span>  
  
 <span data-ttu-id="cb6a6-316">Os tipos nos namespaces <xref:System.ComponentModel.DataAnnotations> e <xref:System.ComponentModel.DataAnnotations.Schema> não têm suporte em [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb6a6-316">The types in the <xref:System.ComponentModel.DataAnnotations> and <xref:System.ComponentModel.DataAnnotations.Schema> namespaces aren't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="cb6a6-317">Eles incluem os seguintes tipos que estão presentes nos aplicativos .NET para Windows Store para o Windows 8:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-317">These include the following types that are present in the .NET for Windows Store apps for Windows 8:</span></span>  
  
||  
|-|  
|<xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EditableAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>|  
  
 <span data-ttu-id="cb6a6-318">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-318">**Visual Basic**</span></span>  
  
 <span data-ttu-id="cb6a6-319">Visual Basic não é suportada atualmente no [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb6a6-319">Visual Basic isn't currently supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="cb6a6-320">Os seguintes tipos nos namespaces <xref:Microsoft.VisualBasic> e <xref:Microsoft.VisualBasic.CompilerServices> não estão disponíveis em [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-320">The following types in the <xref:Microsoft.VisualBasic> and <xref:Microsoft.VisualBasic.CompilerServices> namespaces aren't available in [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span></span>  
  
||  
|-|  
|<xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>|  
  
 <span data-ttu-id="cb6a6-321">**Contexto de reflexão (namespace System.Reflection.Context)**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-321">**Reflection Context (System.Reflection.Context namespace)**</span></span>  
  
 <span data-ttu-id="cb6a6-322">A classe <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> não tem suporte em [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb6a6-322">The <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> class isn't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="cb6a6-323">**RTC (System.Net.Http.Rtc)**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-323">**RTC (System.Net.Http.Rtc)**</span></span>  
  
 <span data-ttu-id="cb6a6-324">A classe <xref:System.Net.Http.RtcRequestFactory?displayProperty=nameWithType> não tem suporte em [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb6a6-324">The <xref:System.Net.Http.RtcRequestFactory?displayProperty=nameWithType> class isn't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="cb6a6-325">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-325">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span></span>  
  
 <span data-ttu-id="cb6a6-326">Os tipos nos [namespaces System.ServiceModel.\*](http://msdn.microsoft.com/library/gg145010.aspx) não têm suporte em [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb6a6-326">The types in the [System.ServiceModel.\* namespaces](http://msdn.microsoft.com/library/gg145010.aspx) aren't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="cb6a6-327">Eles incluem os seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-327">These includes the following types:</span></span>  
  
||  
|-|  
|<xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>|  
  
### <a name="differences-in-serializers"></a><span data-ttu-id="cb6a6-328">Diferenças nos serializadores</span><span class="sxs-lookup"><span data-stu-id="cb6a6-328">Differences in serializers</span></span>  
 <span data-ttu-id="cb6a6-329">As seguintes diferenças envolvem serialização e desserialização com e classes <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> e <xref:System.Xml.Serialization.XmlSerializer>:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-329">The following differences concern serialization and deserialization with the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes:</span></span>  
  
-   <span data-ttu-id="cb6a6-330">No [!INCLUDE[net_native](../../../includes/net-native-md.md)], <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> não conseguem serializar ou desserializar uma classe derivada que tem um membro da classe base cujo tipo não é um tipo de serialização de raiz.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-330">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize or deserialize a derived class that has a base class member whose type isn't a root serialization type.</span></span> <span data-ttu-id="cb6a6-331">Por exemplo, no código a seguir, tentar serializar ou desserializar `Y` resulta em um erro:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-331">For example, in the following code, trying to serialize or deserialize `Y` results in an error:</span></span>  
  
     [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]  
  
     <span data-ttu-id="cb6a6-332">O tipo `InnerType` não é conhecido pelo serializador, pois os membros da classe base não são percorridos durante a serialização.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-332">Type `InnerType` isn't known to the serializer, because the members of the base class aren't traversed during serialization.</span></span>  
  
-   <span data-ttu-id="cb6a6-333"><xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> não conseguem serializar uma classe ou estrutura que implementa a interface <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-333"><xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize a class or structure that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="cb6a6-334">Por exemplo, os seguintes tipos falham ao serializar ou desserializar:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-334">For example, the following types fail to serialize or deserialize:</span></span>  
  
  
  
-   <span data-ttu-id="cb6a6-335"><xref:System.Xml.Serialization.XmlSerializer> falha ao serializar o valor de objeto a seguir, porque não sabe o tipo exato de objeto a ser serializado:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-335"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize the following object value, because it doesn't know the exact type of the object to be serialized:</span></span>  
  
  
  
-   <span data-ttu-id="cb6a6-336"><xref:System.Xml.Serialization.XmlSerializer> falha ao serializar ou desserializar se o tipo do objeto serializado é <xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-336"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize or deserialize if the type of the serialized object is <xref:System.Xml.XmlQualifiedName>.</span></span>  
  
-   <span data-ttu-id="cb6a6-337">Todos os serializadores (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> e <xref:System.Xml.Serialization.XmlSerializer>) falham ao gerar o código de serialização para tipo <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> ou para um tipo que contém <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-337">All serializers (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer>) fail to generate serialization code for type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> or for a type that contains <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="cb6a6-338">Eles exibem erros de tempo de compilação em vez disso.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-338">They display build-time errors instead.</span></span>  
  
-   <span data-ttu-id="cb6a6-339">Não há garantia que os seguintes construtores dos tipos de serialização funcionem conforme o esperado:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-339">The following constructors of the serialization types aren't guaranteed to work as expected:</span></span>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29?displayProperty=nameWithType>  
  
-   <span data-ttu-id="cb6a6-340">O <xref:System.Xml.Serialization.XmlSerializer> falha ao gerar o código para um tipo que tem métodos atribuídos com qualquer um dos seguintes atributos:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-340"><xref:System.Xml.Serialization.XmlSerializer> fails to generate code for a type that has methods attributed with any of the following attributes:</span></span>  
  
    -   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <span data-ttu-id="cb6a6-341">O <xref:System.Xml.Serialization.XmlSerializer> não aceita a interface de serialização personalizada <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-341"><xref:System.Xml.Serialization.XmlSerializer> doesn't honor the <xref:System.Xml.Serialization.IXmlSerializable> custom serialization interface.</span></span> <span data-ttu-id="cb6a6-342">Se você tiver uma classe que implementa essa interface, <xref:System.Xml.Serialization.XmlSerializer> considera o tipo como um objeto CLR (POCO) antigo simples, serializando apenas suas propriedades públicas.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-342">If you have a class that implements this interface, <xref:System.Xml.Serialization.XmlSerializer> considers the type a plain old CLR object (POCO) type and serializes only its public properties.</span></span>  
  
-   <span data-ttu-id="cb6a6-343">Serializar um objeto <xref:System.Exception> simples, como a seguir, não funciona bem com <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-343">Serializing a plain <xref:System.Exception> object, such as the following, doesn't work well with <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:</span></span>  
  
  
  
<a name="VS"></a>   
## <a name="visual-studio-differences"></a><span data-ttu-id="cb6a6-344">Diferenças do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cb6a6-344">Visual Studio differences</span></span>  
 <span data-ttu-id="cb6a6-345">**Exceções e depuração**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-345">**Exceptions and debugging**</span></span>  
  
 <span data-ttu-id="cb6a6-346">Quando você estiver executando aplicativos compilados usando [!INCLUDE[net_native](../../../includes/net-native-md.md)] no depurador, as exceções de primeira chance são habilitadas para os seguintes tipos de exceção:</span><span class="sxs-lookup"><span data-stu-id="cb6a6-346">When you're running apps compiled by using [!INCLUDE[net_native](../../../includes/net-native-md.md)] in the debugger, first-chance exceptions are enabled for the following exception types:</span></span>  
  
-   <xref:System.MemberAccessException>  
  
-   <xref:System.TypeAccessException>  
  
 <span data-ttu-id="cb6a6-347">**Criando aplicativos**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-347">**Building apps**</span></span>  
  
 <span data-ttu-id="cb6a6-348">Use as ferramentas de criação x86 usadas por padrão pelo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-348">Use the x86 build tools that are used by default by Visual Studio.</span></span> <span data-ttu-id="cb6a6-349">Não recomendamos usar as ferramentas AMD64 MSBuild, que se encontram em C:\Program Files (x86)\MSBuild\12.0\bin\amd64, pois podem criar problemas de compilação.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-349">We don't recommend using the AMD64 MSBuild tools, which are found in C:\Program Files (x86)\MSBuild\12.0\bin\amd64; these may create build problems.</span></span>  
  
 <span data-ttu-id="cb6a6-350">**Criadores de perfil**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-350">**Profilers**</span></span>  
  
-   <span data-ttu-id="cb6a6-351">O criador de perfil de CPU do Visual Studio e o criador de perfil de memória XAML não exibem o Just-My-Code corretamente.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-351">The Visual Studio CPU Profiler and XAML Memory Profiler don't display Just-My-Code correctly.</span></span>  
  
-   <span data-ttu-id="cb6a6-352">O gerador de perfil de memória XAML não exibe corretamente os dados da pilha gerenciada.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-352">The XAML Memory Profiler doesn't accurately display managed heap data.</span></span>  
  
-   <span data-ttu-id="cb6a6-353">O gerador de perfil de CPU não identifica corretamente módulos e exibe nomes de função de prefixo.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-353">The CPU Profiler doesn't correctly identify modules, and displays prefixed function names.</span></span>  
  
 <span data-ttu-id="cb6a6-354">**Projetos da biblioteca de teste de unidade**</span><span class="sxs-lookup"><span data-stu-id="cb6a6-354">**Unit Test Library projects**</span></span>  
  
 <span data-ttu-id="cb6a6-355">Habilitar [!INCLUDE[net_native](../../../includes/net-native-md.md)] em uma biblioteca de teste de unidade para aplicativos da Windows Store não é suportado e causa erros de compilação no projeto.</span><span class="sxs-lookup"><span data-stu-id="cb6a6-355">Enabling [!INCLUDE[net_native](../../../includes/net-native-md.md)] on a Unit Test Library for a Windows Store apps project isn't supported and causes the project to fail to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb6a6-356">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb6a6-356">See Also</span></span>  
 [<span data-ttu-id="cb6a6-357">Introdução</span><span class="sxs-lookup"><span data-stu-id="cb6a6-357">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [<span data-ttu-id="cb6a6-358">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="cb6a6-358">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="cb6a6-359">Visão geral de aplicativos .NET da Windows Store</span><span class="sxs-lookup"><span data-stu-id="cb6a6-359">.NET For Windows Store apps overview</span></span>](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 [<span data-ttu-id="cb6a6-360">Suporte do .NET Framework para Aplicativos da Windows Store e Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="cb6a6-360">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
