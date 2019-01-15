---
title: Migrando seu aplicativo da Windows Store para .NET Nativo
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27903899ca31166e160f32ca0175e353e54676cc
ms.sourcegitcommit: 75567a3cb437009db55949c6092f4e77ed1a9da4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54307559"
---
# <a name="migrating-your-windows-store-app-to-net-native"></a><span data-ttu-id="9b452-102">Migrando seu aplicativo da Windows Store para .NET Nativo</span><span class="sxs-lookup"><span data-stu-id="9b452-102">Migrating Your Windows Store App to .NET Native</span></span>
<span data-ttu-id="9b452-103">.NET native fornece compilação estática dos aplicativos na Store do Windows ou no computador do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="9b452-103">.NET Native provides static compilation of apps in the Windows Store or on the developer’s computer.</span></span> <span data-ttu-id="9b452-104">Isso difere da compilação dinâmica realizada para Aplicativos da Windows Store pelo compilador JIT (just-in-time) ou o [Gerador de Imagem Nativa (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9b452-104">This differs from the dynamic compilation performed for Windows Store apps by the just-in-time (JIT) compiler or the [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) on the device.</span></span> <span data-ttu-id="9b452-105">Apesar das diferenças, o .NET Native tenta manter a compatibilidade com o [aplicativos .NET para Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29).</span><span class="sxs-lookup"><span data-stu-id="9b452-105">Despite the differences, .NET Native tries to maintain compatibility with the [.NET for Windows Store apps](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29).</span></span> <span data-ttu-id="9b452-106">Na maior parte, as coisas que funcionam em aplicativos do .NET para Windows Store também funcionam com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9b452-106">For the most part, things that work on the .NET for Windows Store apps also work with .NET Native.</span></span>  <span data-ttu-id="9b452-107">No entanto, em alguns casos, você pode encontrar alterações de comportamento.</span><span class="sxs-lookup"><span data-stu-id="9b452-107">However, in some cases, you may encounter behavioral changes.</span></span> <span data-ttu-id="9b452-108">Este documento aborda essas diferenças entre os aplicativos padrão do .NET para Windows Store e o .NET nativo nas seguintes áreas:</span><span class="sxs-lookup"><span data-stu-id="9b452-108">This document discusses these differences between the standard .NET for Windows Store apps and .NET Native in the following areas:</span></span>  
  
-   [<span data-ttu-id="9b452-109">Diferenças de tempo de execução geral</span><span class="sxs-lookup"><span data-stu-id="9b452-109">General runtime differences</span></span>](#Runtime)  
  
-   [<span data-ttu-id="9b452-110">Diferenças de programação dinâmica</span><span class="sxs-lookup"><span data-stu-id="9b452-110">Dynamic programming differences</span></span>](#Dynamic)  
  
-   [<span data-ttu-id="9b452-111">Outras diferenças relacionadas à reflexão</span><span class="sxs-lookup"><span data-stu-id="9b452-111">Other reflection-related differences</span></span>](#Reflection)  
  
-   [<span data-ttu-id="9b452-112">Cenários e APIs sem suporte</span><span class="sxs-lookup"><span data-stu-id="9b452-112">Unsupported scenarios and APIs</span></span>](#Unsupported)  
  
-   [<span data-ttu-id="9b452-113">Diferenças do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9b452-113">Visual Studio differences</span></span>](#VS)  
  
<a name="Runtime"></a>   
## <a name="general-runtime-differences"></a><span data-ttu-id="9b452-114">Diferenças de tempo de execução geral</span><span class="sxs-lookup"><span data-stu-id="9b452-114">General runtime differences</span></span>  
  
-   <span data-ttu-id="9b452-115">Exceções, como <xref:System.TypeLoadException>, que são geradas pelo compilador JIT quando um aplicativo é executado sobre o common language runtime (CLR), geralmente resulta em erros de tempo de compilação quando processados por .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9b452-115">Exceptions, such as <xref:System.TypeLoadException>, that are thrown by the JIT compiler when an app runs on the common language runtime (CLR) generally result in compile-time errors when processed by .NET Native.</span></span>  
  
-   <span data-ttu-id="9b452-116">Não chame o método <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> de um thread de interface do usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9b452-116">Don't call the <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method from an app's UI thread.</span></span> <span data-ttu-id="9b452-117">Isso pode resultar em um deadlock no .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9b452-117">This can result in a deadlock on .NET Native.</span></span>  
  
-   <span data-ttu-id="9b452-118">Não conte com ordenação de invocação do construtor de classe estática.</span><span class="sxs-lookup"><span data-stu-id="9b452-118">Don't rely on static class constructor invocation ordering.</span></span> <span data-ttu-id="9b452-119">No .NET Native, a ordem de invocação é diferente da ordem de execução padrão.</span><span class="sxs-lookup"><span data-stu-id="9b452-119">In .NET Native, the invocation order is different from the order on the standard runtime.</span></span> <span data-ttu-id="9b452-120">(Mesmo com o tempo de execução padrão, você não deve confiar na ordem de execução de construtores de classe estáticos.)</span><span class="sxs-lookup"><span data-stu-id="9b452-120">(Even with the standard runtime, you shouldn't rely on the order of execution of static class constructors.)</span></span>  
  
-   <span data-ttu-id="9b452-121">Loops infinitos sem fazer uma chamada (por exemplo, `while(true);`) em qualquer thread interromper o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9b452-121">Infinite looping without making a call (for example, `while(true);`) on any thread may bring the app to a halt.</span></span> <span data-ttu-id="9b452-122">Da mesma forma, esperas grandes ou infinitas podem interromper o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9b452-122">Similarly, large or infinite waits may bring the app to a halt.</span></span>  
  
-   <span data-ttu-id="9b452-123">Certos ciclos de inicialização genéricos não geram exceções no .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9b452-123">Certain generic initialization cycles don't throw exceptions in .NET Native.</span></span> <span data-ttu-id="9b452-124">Por exemplo, o código a seguir gera uma exceção <xref:System.TypeLoadException> no CLR padrão.</span><span class="sxs-lookup"><span data-stu-id="9b452-124">For example, the following code throws a <xref:System.TypeLoadException> exception on the standard CLR.</span></span> <span data-ttu-id="9b452-125">No .NET Native, ele não sabe.</span><span class="sxs-lookup"><span data-stu-id="9b452-125">In .NET Native, it doesn't.</span></span>  
  
     [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]  
  
-   <span data-ttu-id="9b452-126">Em alguns casos, o .NET Native fornece diferentes implementações das bibliotecas de classes do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9b452-126">In some cases, .NET Native provides different implementations of .NET Framework class libraries.</span></span> <span data-ttu-id="9b452-127">Um objeto retornado de um método sempre implementará os membros do tipo retornado.</span><span class="sxs-lookup"><span data-stu-id="9b452-127">An object returned from a method will always implement the members of the returned type.</span></span> <span data-ttu-id="9b452-128">No entanto, desde que sua implementação de backup seja diferente, você não poderá convertê-lo para o mesmo conjunto de tipos como realizado em outras plataformas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9b452-128">However, since its backing implementation is different, you may not be able to cast it to the same set of types as you could on other .NET Framework platforms.</span></span> <span data-ttu-id="9b452-129">Por exemplo, em alguns casos, você não poderá converter o objeto de interface <xref:System.Collections.Generic.IEnumerable%601> retornado por métodos como <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> ou <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> para `T[]`.</span><span class="sxs-lookup"><span data-stu-id="9b452-129">For example, in some cases, you may not be able to cast the <xref:System.Collections.Generic.IEnumerable%601> interface object returned by methods such as <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> or <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> to `T[]`.</span></span>  
  
-   <span data-ttu-id="9b452-130">O cache de WinInet não é habilitado por padrão em aplicativos .NET para Windows Store, mas é sobre o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9b452-130">The WinInet cache isn't enabled by default on .NET for Windows Store apps, but it is on .NET Native.</span></span> <span data-ttu-id="9b452-131">Isso melhora o desempenho, mas tem implicações de conjunto de trabalho.</span><span class="sxs-lookup"><span data-stu-id="9b452-131">This improves performance but has working set implications.</span></span> <span data-ttu-id="9b452-132">Nenhuma ação do desenvolvedor é necessária.</span><span class="sxs-lookup"><span data-stu-id="9b452-132">No developer action is necessary.</span></span>  
  
<a name="Dynamic"></a>   
## <a name="dynamic-programming-differences"></a><span data-ttu-id="9b452-133">Diferenças de programação dinâmica</span><span class="sxs-lookup"><span data-stu-id="9b452-133">Dynamic programming differences</span></span>  
 <span data-ttu-id="9b452-134">.NET nativo vincula estaticamente no código do .NET Framework para tornar o código de aplicativo local para desempenho máximo.</span><span class="sxs-lookup"><span data-stu-id="9b452-134">.NET Native statically links in code from the .NET Framework to make the code app-local for maximum performance.</span></span> <span data-ttu-id="9b452-135">No entanto, os tamanhos binários precisam permanecer pequenos para que todo o .NET Framework não seja trazido.</span><span class="sxs-lookup"><span data-stu-id="9b452-135">However, binary sizes have to remain small, so the entire .NET Framework can't be brought in.</span></span> <span data-ttu-id="9b452-136">O compilador nativo .NET resolve essa limitação usando um redutor de dependência que remove referências ao código não utilizado.</span><span class="sxs-lookup"><span data-stu-id="9b452-136">The .NET Native compiler resolves this limitation by using a dependency reducer that removes references to unused code.</span></span> <span data-ttu-id="9b452-137">No entanto, o .NET Native pode não manter ou gerar algumas informações de tipo e código quando essas informações não podem ser deduzidas estaticamente no tempo de compilação, mas em vez disso, são recuperadas dinamicamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9b452-137">However, .NET Native might not maintain or generate some type information and code when that information can't be inferred statically at compile time, but instead is retrieved dynamically at runtime.</span></span>  
  
 <span data-ttu-id="9b452-138">.NET nativo habilita a reflexão e programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="9b452-138">.NET Native does enable reflection and dynamic programming.</span></span> <span data-ttu-id="9b452-139">No entanto, nem todos os tipos podem ser marcados para reflexão, porque isso tornaria o tamanho do código gerado grande demais (especialmente porque há suporte para reflexão nas APIs públicas do .NET Framework).</span><span class="sxs-lookup"><span data-stu-id="9b452-139">However, not all types can be marked for reflection, because this would make the generated code size too large (especially because reflecting on public APIs in the .NET Framework is supported).</span></span> <span data-ttu-id="9b452-140">O compilador nativo .NET faz escolhas inteligentes sobre quais tipos devem suportar a reflexão e mantém os metadados e gera código somente para esses tipos.</span><span class="sxs-lookup"><span data-stu-id="9b452-140">The .NET Native compiler makes smart choices about which types should support reflection, and it keeps the metadata and generates code only for those types.</span></span>  
  
 <span data-ttu-id="9b452-141">Por exemplo, a associação de dados necessita de um aplicativo para conseguir mapear nomes de propriedade às funções.</span><span class="sxs-lookup"><span data-stu-id="9b452-141">For example, data binding requires an app to be able to map property names to functions.</span></span> <span data-ttu-id="9b452-142">Nos aplicativos .NET para Windows Store, o Common Language Runtime usa reflexão automaticamente para fornecer esse recurso para tipos nativos gerenciados e disponíveis publicamente.</span><span class="sxs-lookup"><span data-stu-id="9b452-142">In .NET for Windows Store apps, the common language runtime automatically uses reflection to provide this capability for managed types and publicly available native types.</span></span> <span data-ttu-id="9b452-143">No .NET Native, o compilador inclui automaticamente os metadados para tipos aos quais você pode associar dados.</span><span class="sxs-lookup"><span data-stu-id="9b452-143">In .NET Native, the compiler automatically includes metadata for types to which you bind data.</span></span>  
  
 <span data-ttu-id="9b452-144">O compilador normalmente também pode lidar com .NET nativo usado a tipos genéricos, como <xref:System.Collections.Generic.List%601> e <xref:System.Collections.Generic.Dictionary%602>, que funcionam sem necessitar de quaisquer dicas ou diretivas.</span><span class="sxs-lookup"><span data-stu-id="9b452-144">The .NET Native compiler can also handle commonly used generic types such as <xref:System.Collections.Generic.List%601> and <xref:System.Collections.Generic.Dictionary%602>, which work without requiring any hints or directives.</span></span> <span data-ttu-id="9b452-145">A palavra-chave [dynamic](~/docs/csharp/language-reference/keywords/dynamic.md) também tem suporte dentro de certos limites.</span><span class="sxs-lookup"><span data-stu-id="9b452-145">The [dynamic](~/docs/csharp/language-reference/keywords/dynamic.md) keyword is also supported within certain limits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b452-146">Você deve testar todos os caminhos de código dinâmico completamente ao portar seu aplicativo para o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9b452-146">You should test all dynamic code paths thoroughly when porting your app to .NET Native.</span></span>  
  
 <span data-ttu-id="9b452-147">A configuração padrão do .NET Native é suficiente para a maioria dos desenvolvedores, mas alguns desenvolvedores talvez queira ajustar suas configurações usando um diretivas de tempo de execução (. RD. xml) arquivos.</span><span class="sxs-lookup"><span data-stu-id="9b452-147">The default configuration for .NET Native is sufficient for most developers, but some developers might want to fine- tune their configurations by using a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="9b452-148">Além disso, em alguns casos, o compilador do .NET nativo é não é possível determinar quais metadados devem estar disponíveis para reflexão e depende de dicas, particularmente nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="9b452-148">In addition, in some cases, the .NET Native compiler is unable to determine which metadata must be available for reflection and relies on hints, particularly in the following cases:</span></span>  
  
-   <span data-ttu-id="9b452-149">Algumas construções <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> e <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> não podem ser determinadas estaticamente.</span><span class="sxs-lookup"><span data-stu-id="9b452-149">Some constructs like <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> and <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> can't be determined statically.</span></span>  
  
-   <span data-ttu-id="9b452-150">Como o compilador não pode determinar as instanciações, um tipo genérico sobre o qual você deseja refletir deverá ser especificado por diretivas de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9b452-150">Because the compiler can't determine the instantiations, a generic type that you want to reflect on has to be specified by runtime directives.</span></span> <span data-ttu-id="9b452-151">Isso não é apenas porque todo o código deve ser incluído, mas sim porque a reflexão em tipos genéricos pode formar um ciclo infinito (por exemplo, quando um método genérico é invocado em um tipo genérico).</span><span class="sxs-lookup"><span data-stu-id="9b452-151">This isn't just because all code must be included, but because reflection on generic types can form an infinite cycle (for example, when a generic method is invoked on a generic type).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b452-152">Diretivas de tempo de execução são definidas em um arquivo de diretivas de tempo de execução (.rd.xml).</span><span class="sxs-lookup"><span data-stu-id="9b452-152">Runtime directives are defined in a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="9b452-153">Para obter mais informações sobre como usar essa arquivo, consulte [Introdução](../../../docs/framework/net-native/getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="9b452-153">For general information about using this file, see [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md).</span></span> <span data-ttu-id="9b452-154">Para obter informações sobre as diretivas de tempo de execução, consulte [Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="9b452-154">For information about the runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
 <span data-ttu-id="9b452-155">.NET native também inclui ferramentas que ajudam o desenvolvedor a determinar quais tipos de fora do conjunto padrão devem suportar a reflexão de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="9b452-155">.NET Native also includes profiling tools that help the developer determine which types outside the default set should support reflection.</span></span>  
  
<a name="Reflection"></a>   
## <a name="other-reflection-related-differences"></a><span data-ttu-id="9b452-156">Outras diferenças relacionadas à reflexão</span><span class="sxs-lookup"><span data-stu-id="9b452-156">Other reflection-related differences</span></span>  
 <span data-ttu-id="9b452-157">Há inúmeros outros individuais relacionadas à reflexão diferenças no comportamento entre os aplicativos do .NET para Windows Store e o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9b452-157">There are a number of other individual reflection-related differences in behavior between the .NET for Windows Store apps and .NET Native.</span></span>  
  
 <span data-ttu-id="9b452-158">No .NET Native:</span><span class="sxs-lookup"><span data-stu-id="9b452-158">In .NET Native:</span></span>  
  
-   <span data-ttu-id="9b452-159">Não há suporte para reflexão privada sobre tipos e membros da biblioteca de classes do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9b452-159">Private reflection over types and members in the .NET Framework class library is not supported.</span></span> <span data-ttu-id="9b452-160">No entanto, é possível refletir sobre seus próprios tipos e membros privados, bem como tipos e membros em bibliotecas de terceiros.</span><span class="sxs-lookup"><span data-stu-id="9b452-160">You can, however, reflect over your own private types and members, as well as types and members in third-party libraries.</span></span>  
  
-   <span data-ttu-id="9b452-161">A propriedade <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> retorna `false` corretamente para um objeto <xref:System.Reflection.ParameterInfo> que representa um valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="9b452-161">The <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> property correctly returns `false` for a <xref:System.Reflection.ParameterInfo> object that represents a return value.</span></span> <span data-ttu-id="9b452-162">Nos aplicativos .NET para Windows Store, ele retorna `true`.</span><span class="sxs-lookup"><span data-stu-id="9b452-162">In the .NET for Windows Store apps, it returns `true`.</span></span> <span data-ttu-id="9b452-163">A Linguagem intermediária (IL) não oferece suporte a isso diretamente e interpretações são deixada para a linguagem.</span><span class="sxs-lookup"><span data-stu-id="9b452-163">Intermediate language (IL) doesn’t support this directly, and interpretation is left to the language.</span></span>  
  
-   <span data-ttu-id="9b452-164">Membros públicos nas estruturas <xref:System.RuntimeFieldHandle> e <xref:System.RuntimeMethodHandle> não são suportadas.</span><span class="sxs-lookup"><span data-stu-id="9b452-164">Public members on the <xref:System.RuntimeFieldHandle> and <xref:System.RuntimeMethodHandle> structures aren't supported.</span></span> <span data-ttu-id="9b452-165">Esses tipos são suportados apenas para LINQ, árvores de expressão e inicialização de matriz estática.</span><span class="sxs-lookup"><span data-stu-id="9b452-165">These types are supported only for LINQ, expression trees, and static array initialization.</span></span>  
  
-   <span data-ttu-id="9b452-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> e <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> incluem membros ocultos em classes base e, portanto, podem ser substituídos sem substituições explícitas.</span><span class="sxs-lookup"><span data-stu-id="9b452-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> and <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> include hidden members in base classes and thus may be overridden without explicit overrides.</span></span> <span data-ttu-id="9b452-167">Isso também é verdadeiro para outros métodos [RuntimeReflectionExtensions.GetRuntime\*](xref:System.Reflection.RuntimeReflectionExtensions).</span><span class="sxs-lookup"><span data-stu-id="9b452-167">This is also true of other [RuntimeReflectionExtensions.GetRuntime\*](xref:System.Reflection.RuntimeReflectionExtensions) methods.</span></span>  
  
-   <span data-ttu-id="9b452-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> e <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> não falham quando você tentar criar certas combinações (por exemplo, uma matriz de byrefs).</span><span class="sxs-lookup"><span data-stu-id="9b452-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> don't fail when you try to create certain combinations (for example, an array of byrefs).</span></span>  
  
-   <span data-ttu-id="9b452-169">Você não pode usar reflexão para invocar os membros que têm parâmetros de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="9b452-169">You can't use reflection to invoke members that have pointer parameters.</span></span>  
  
-   <span data-ttu-id="9b452-170">Você não pode usar reflexão para obter ou definir um campo de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="9b452-170">You can't use reflection to get or set a pointer field.</span></span>  
  
-   <span data-ttu-id="9b452-171">Quando a contagem de argumentos está errada e o tipo de um dos argumentos está incorreto, o .NET Native gera uma <xref:System.ArgumentException> em vez de um <xref:System.Reflection.TargetParameterCountException>.</span><span class="sxs-lookup"><span data-stu-id="9b452-171">When the argument count is wrong and the type of one of the arguments is incorrect, .NET Native throws an <xref:System.ArgumentException> instead of a <xref:System.Reflection.TargetParameterCountException>.</span></span>  
  
-   <span data-ttu-id="9b452-172">A serialização binária de exceções geralmente não é suportada.</span><span class="sxs-lookup"><span data-stu-id="9b452-172">Binary serialization of exceptions is generally not supported.</span></span> <span data-ttu-id="9b452-173">Como resultado, objetos não serializáveis não podem ser adicionados ao dicionário <xref:System.Exception.Data%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9b452-173">As a result, non-serializable objects can be added to the <xref:System.Exception.Data%2A?displayProperty=nameWithType> dictionary.</span></span>  
  
<a name="Unsupported"></a>   
## <a name="unsupported-scenarios-and-apis"></a><span data-ttu-id="9b452-174">Cenários e APIs sem suporte</span><span class="sxs-lookup"><span data-stu-id="9b452-174">Unsupported scenarios and APIs</span></span>  
 <span data-ttu-id="9b452-175">As seções a seguir listam cenários não suportados e APIs de desenvolvimento geral, interoperabilidade e tecnologias como HTTPClient e Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="9b452-175">The following sections list unsupported scenarios and APIs for general development, interop, and technologies such as HTTPClient and Windows Communication Foundation (WCF):</span></span>  
  
-   [<span data-ttu-id="9b452-176">Desenvolvimento geral</span><span class="sxs-lookup"><span data-stu-id="9b452-176">General development</span></span>](#General)  
  
-   [<span data-ttu-id="9b452-177">HttpClient</span><span class="sxs-lookup"><span data-stu-id="9b452-177">HttpClient</span></span>](#HttpClient)  
  
-   [<span data-ttu-id="9b452-178">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="9b452-178">Interop</span></span>](#Interop)  
  
-   [<span data-ttu-id="9b452-179">APIs sem suporte</span><span class="sxs-lookup"><span data-stu-id="9b452-179">Unsupported APIs</span></span>](#APIs)  
  
<a name="General"></a>   
### <a name="general-development-differences"></a><span data-ttu-id="9b452-180">Diferenças de desenvolvimento geral</span><span class="sxs-lookup"><span data-stu-id="9b452-180">General development differences</span></span>  
 <span data-ttu-id="9b452-181">**Tipos de valor**</span><span class="sxs-lookup"><span data-stu-id="9b452-181">**Value types**</span></span>  
  
-   <span data-ttu-id="9b452-182">Se você substituir os métodos <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> e <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> para um tipo de valor, não chame as implementações de classe base.</span><span class="sxs-lookup"><span data-stu-id="9b452-182">If you override the <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> and <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> methods for a value type, don't call the base class implementations.</span></span> <span data-ttu-id="9b452-183">Em aplicativos .NET para Windows Store, esses métodos dependem de reflexão.</span><span class="sxs-lookup"><span data-stu-id="9b452-183">In .NET for Windows Store apps, these methods rely on reflection.</span></span> <span data-ttu-id="9b452-184">Em tempo de compilação, o .NET Native gera uma implementação que não depende de reflexão de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9b452-184">At compile time, .NET Native generates an implementation that doesn't rely on runtime reflection.</span></span> <span data-ttu-id="9b452-185">Isso significa que se você não substituir esses dois métodos, eles funcionarão conforme o esperado, porque o .NET Native gera a implementação em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="9b452-185">This means that if you don't override these two methods, they will work as expected, because .NET Native generates the implementation at compile time.</span></span> <span data-ttu-id="9b452-186">No entanto, substituir esses métodos, mas chamar a implementação de classe base, resulta em uma exceção.</span><span class="sxs-lookup"><span data-stu-id="9b452-186">However, overriding these methods but calling the base class implementation results in an exception.</span></span>  
  
-   <span data-ttu-id="9b452-187">Não há suporte para tipos de valor maior do que um megabyte.</span><span class="sxs-lookup"><span data-stu-id="9b452-187">Value types larger than one megabyte aren't supported.</span></span>  
  
-   <span data-ttu-id="9b452-188">Tipos de valor não podem ter um construtor padrão no .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9b452-188">Value types can't have a default constructor in .NET Native.</span></span> <span data-ttu-id="9b452-189">(C# e Visual Basic proíbem construtores padrão em tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="9b452-189">(C# and Visual Basic prohibit default constructors on value types.</span></span> <span data-ttu-id="9b452-190">No entanto, eles podem ser criados em IL.)</span><span class="sxs-lookup"><span data-stu-id="9b452-190">However, these can be created in IL.)</span></span>  
  
 <span data-ttu-id="9b452-191">**Matrizes**</span><span class="sxs-lookup"><span data-stu-id="9b452-191">**Arrays**</span></span>  
  
-   <span data-ttu-id="9b452-192">Não há suporte para matrizes com um limite inferior diferente de zero.</span><span class="sxs-lookup"><span data-stu-id="9b452-192">Arrays with a lower bound other than zero aren't supported.</span></span> <span data-ttu-id="9b452-193">Normalmente, esses conjuntos são criados ao chamar a sobrecarga <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9b452-193">Typically, these arrays are created by calling the <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> overload.</span></span>  
  
-   <span data-ttu-id="9b452-194">A criação dinâmica de matrizes multidimensionais não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="9b452-194">Dynamic creation of multidimensional arrays isn't supported.</span></span> <span data-ttu-id="9b452-195">Essas matrizes geralmente são criados chamando uma sobrecarga do método <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> que inclui um parâmetro `lengths` ou chamando o método <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9b452-195">Such arrays are typically created by calling an overload of the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method that includes a `lengths` parameter, or by calling the <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="9b452-196">Não há suporte para matrizes multidimensionais com quatro ou mais dimensões, ou seja, com valor da propriedade <xref:System.Array.Rank%2A?displayProperty=nameWithType> quatro ou superior.</span><span class="sxs-lookup"><span data-stu-id="9b452-196">Multidimensional arrays that have four or more dimensions aren't supported; that is, their <xref:System.Array.Rank%2A?displayProperty=nameWithType> property value is four or greater.</span></span> <span data-ttu-id="9b452-197">Use [matrizes denteadas](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (uma matriz de matrizes) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="9b452-197">Use [jagged arrays](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (an array of arrays) instead.</span></span> <span data-ttu-id="9b452-198">Por exemplo, `array[x,y,z]` é inválido, mas `array[x][y][z]` não é.</span><span class="sxs-lookup"><span data-stu-id="9b452-198">For example, `array[x,y,z]` is invalid, but `array[x][y][z]` isn't.</span></span>  
  
-   <span data-ttu-id="9b452-199">Variação de matrizes multidimensionais não é suportada e causa uma exceção <xref:System.InvalidCastException> no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9b452-199">Variance for multidimensional arrays isn't supported and causes an <xref:System.InvalidCastException> exception at run time.</span></span>  
  
 <span data-ttu-id="9b452-200">**Genéricos**</span><span class="sxs-lookup"><span data-stu-id="9b452-200">**Generics**</span></span>  
  
-   <span data-ttu-id="9b452-201">A expansão do tipo genérico infinito resulta em um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="9b452-201">Infinite generic type expansion results in a compiler error.</span></span> <span data-ttu-id="9b452-202">Por exemplo, esse código falha ao compilar:</span><span class="sxs-lookup"><span data-stu-id="9b452-202">For example, this code fails to compile:</span></span>  
  
     [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]  
  
 <span data-ttu-id="9b452-203">**Ponteiros**</span><span class="sxs-lookup"><span data-stu-id="9b452-203">**Pointers**</span></span>  
  
-   <span data-ttu-id="9b452-204">Não há suporte para matrizes de ponteiros.</span><span class="sxs-lookup"><span data-stu-id="9b452-204">Arrays of pointers aren't supported.</span></span>  
  
-   <span data-ttu-id="9b452-205">Você não pode usar reflexão para obter ou definir um campo de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="9b452-205">You can't use reflection to get or set a pointer field.</span></span>  
  
 <span data-ttu-id="9b452-206">**Serialização**</span><span class="sxs-lookup"><span data-stu-id="9b452-206">**Serialization**</span></span>  
  
 <span data-ttu-id="9b452-207">O atributo <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> não é suportado.</span><span class="sxs-lookup"><span data-stu-id="9b452-207">The <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> attribute isn't supported.</span></span> <span data-ttu-id="9b452-208">Use o atributo <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="9b452-208">Use the <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> attribute instead.</span></span>  
  
 <span data-ttu-id="9b452-209">**Recursos**</span><span class="sxs-lookup"><span data-stu-id="9b452-209">**Resources**</span></span>  
  
 <span data-ttu-id="9b452-210">O uso de recursos localizados com a classe <xref:System.Diagnostics.Tracing.EventSource> não é suportado.</span><span class="sxs-lookup"><span data-stu-id="9b452-210">The use of localized resources with the <xref:System.Diagnostics.Tracing.EventSource> class isn't supported.</span></span> <span data-ttu-id="9b452-211">A propriedade <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> não define os recursos localizados.</span><span class="sxs-lookup"><span data-stu-id="9b452-211">The <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> property doesn't define localized resources.</span></span>  
  
 <span data-ttu-id="9b452-212">**Delegados**</span><span class="sxs-lookup"><span data-stu-id="9b452-212">**Delegates**</span></span>  
  
 <span data-ttu-id="9b452-213">`Delegate.BeginInvoke` e `Delegate.EndInvoke` não são suportados.</span><span class="sxs-lookup"><span data-stu-id="9b452-213">`Delegate.BeginInvoke` and `Delegate.EndInvoke` aren't supported.</span></span>  
  
 <span data-ttu-id="9b452-214">**APIs diversas**</span><span class="sxs-lookup"><span data-stu-id="9b452-214">**Miscellaneous APIs**</span></span>  
  
-   <span data-ttu-id="9b452-215">A propriedade <xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=nameWithType> gera uma exceção <xref:System.PlatformNotSupportedException> se um atributo <xref:System.Runtime.InteropServices.GuidAttribute> não for aplicado ao tipo.</span><span class="sxs-lookup"><span data-stu-id="9b452-215">The <xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=nameWithType> property throws a <xref:System.PlatformNotSupportedException> exception if a <xref:System.Runtime.InteropServices.GuidAttribute> attribute isn't applied to the type.</span></span> <span data-ttu-id="9b452-216">O GUID é usado principalmente para suporte a COM.</span><span class="sxs-lookup"><span data-stu-id="9b452-216">The GUID is used primarily for COM support.</span></span>  
  
-   <span data-ttu-id="9b452-217">O <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> método analisa corretamente as cadeias de caracteres que contêm datas curtas em .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9b452-217">The <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> method correctly parses strings that contain short dates in .NET Native.</span></span> <span data-ttu-id="9b452-218">Contudo, ele não mantém a compatibilidade com as alterações na análise de data e hora descritas no artigos da Base de Dados de Conhecimento Microsoft [KB2803771](https://support.microsoft.com/kb/2803771) e [KB2803755](https://support.microsoft.com/kb/2803755).</span><span class="sxs-lookup"><span data-stu-id="9b452-218">However, it doesn't maintain compatibility with the changes in date and time parsing described in the Microsoft Knowledge Base articles [KB2803771](https://support.microsoft.com/kb/2803771) and [KB2803755](https://support.microsoft.com/kb/2803755).</span></span>  
  
-   <span data-ttu-id="9b452-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` é arredondado corretamente em .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9b452-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` is correctly rounded in .NET Native.</span></span> <span data-ttu-id="9b452-220">Em algumas versões do CLR, a cadeia de caracteres de resultado é truncada em vez de arredondada.</span><span class="sxs-lookup"><span data-stu-id="9b452-220">In some versions of the CLR, the result string is truncated instead of rounded.</span></span>  
  
<a name="HttpClient"></a>   
### <a name="httpclient-differences"></a><span data-ttu-id="9b452-221">Diferenças do HttpClient</span><span class="sxs-lookup"><span data-stu-id="9b452-221">HttpClient differences</span></span>  
 <span data-ttu-id="9b452-222">No .NET Native, o <xref:System.Net.Http.HttpClientHandler> classe usa internamente WinINet (por meio de <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> classe) em vez da <xref:System.Net.WebRequest> e <xref:System.Net.WebResponse> classes usadas nos aplicativos .NET para Windows Store.</span><span class="sxs-lookup"><span data-stu-id="9b452-222">In .NET Native, the <xref:System.Net.Http.HttpClientHandler> class internally uses WinINet (through the <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class) instead of the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes used in the standard .NET for Windows Store apps.</span></span>  <span data-ttu-id="9b452-223">O WinINet não oferece suporte a todas as opções de configuração que a classe <xref:System.Net.Http.HttpClientHandler> suporta.</span><span class="sxs-lookup"><span data-stu-id="9b452-223">WinINet doesn't support all the configuration options that the <xref:System.Net.Http.HttpClientHandler> class supports.</span></span>  <span data-ttu-id="9b452-224">Portanto:</span><span class="sxs-lookup"><span data-stu-id="9b452-224">As a result:</span></span>  
  
-   <span data-ttu-id="9b452-225">Algumas das propriedades do recurso em <xref:System.Net.Http.HttpClientHandler> retornar `false` sobre o .NET Native, considerando que retornam `true` nos aplicativos .NET para Windows Store.</span><span class="sxs-lookup"><span data-stu-id="9b452-225">Some of the capability properties on <xref:System.Net.Http.HttpClientHandler> return `false` on .NET Native, whereas they return `true` in the standard .NET for Windows Store apps.</span></span>  
  
-   <span data-ttu-id="9b452-226">Alguns da propriedade de configuração `get` acessadores sempre retornam um valor fixo no .NET nativo que é diferente do valor configurável de padrão em aplicativos .NET para Windows Store.</span><span class="sxs-lookup"><span data-stu-id="9b452-226">Some of the configuration property `get` accessors always return a fixed value on .NET Native that is different than the default configurable value in .NET for Windows Store apps.</span></span>  
  
 <span data-ttu-id="9b452-227">Algumas diferenças comportamentais adicionais são abrangidas nas subseções a seguir.</span><span class="sxs-lookup"><span data-stu-id="9b452-227">Some additional behavior differences are covered in the following subsections.</span></span>  
  
 <span data-ttu-id="9b452-228">**Proxy**</span><span class="sxs-lookup"><span data-stu-id="9b452-228">**Proxy**</span></span>  
  
 <span data-ttu-id="9b452-229">O <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> classe não suporta configuração ou substituir o proxy por solicitação.</span><span class="sxs-lookup"><span data-stu-id="9b452-229">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn’t support configuring or overriding the proxy on a per-request basis.</span></span>  <span data-ttu-id="9b452-230">Isso significa que todas as solicitações no .NET Native usam o servidor proxy configurado pelo sistema ou nenhum servidor proxy, dependendo do valor da <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="9b452-230">This means that all requests on .NET Native use the system-configured proxy server or no proxy server, depending on the value of the <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="9b452-231">Em aplicativos .NET para Windows Store, o servidor proxy é definido pela propriedade <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9b452-231">In .NET for Windows Store apps, the proxy server is defined by the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="9b452-232">No .NET Native, definindo o <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> com um valor diferente de `null` lança um <xref:System.PlatformNotSupportedException> exceção.</span><span class="sxs-lookup"><span data-stu-id="9b452-232">On .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> to a value other than `null` throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="9b452-233">O <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> propriedade retorna `false` sobre o .NET Native, considerando que retorna `true` nos aplicativos .NET Framework para Windows Store.</span><span class="sxs-lookup"><span data-stu-id="9b452-233">The <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in the standard .NET Framework for Windows Store apps.</span></span>  
  
 <span data-ttu-id="9b452-234">**Redirecionamento automático**</span><span class="sxs-lookup"><span data-stu-id="9b452-234">**Automatic redirection**</span></span>  
  
 <span data-ttu-id="9b452-235">O <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> classe não permite que o número máximo de redirecionamentos automáticos seja configurado.</span><span class="sxs-lookup"><span data-stu-id="9b452-235">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn't allow the maximum number of automatic redirections to be configured.</span></span>  <span data-ttu-id="9b452-236">O valor da propriedade <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> é 50 por padrão nos aplicativos .NET para Windows Store e pode ser modificada.</span><span class="sxs-lookup"><span data-stu-id="9b452-236">The value of the <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> property is 50 by default in the standard .NET for Windows Store apps and can be modified.</span></span> <span data-ttu-id="9b452-237">No .NET nativo, o valor dessa propriedade é 10 e tentar modificá-la gera uma <xref:System.PlatformNotSupportedException> exceção.</span><span class="sxs-lookup"><span data-stu-id="9b452-237">On .NET Native, the value of this property is 10, and trying to modify it throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="9b452-238">O <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> propriedade retorna `false` sobre o .NET Native, considerando que retorna `true` em aplicativos .NET para Windows Store.</span><span class="sxs-lookup"><span data-stu-id="9b452-238">The <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in .NET for Windows Store apps.</span></span>  
  
 <span data-ttu-id="9b452-239">**Descompactação automática**</span><span class="sxs-lookup"><span data-stu-id="9b452-239">**Automatic decompression**</span></span>  
  
 <span data-ttu-id="9b452-240">Aplicativos .NET para Windows Store permitem definir a propriedade <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> para <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, ambas <xref:System.Net.DecompressionMethods.Deflate> e <xref:System.Net.DecompressionMethods.GZip>, ou <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="9b452-240">.NET for Windows Store apps allows you to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> property to <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="9b452-241">.NET native só dá suporte a <xref:System.Net.DecompressionMethods.Deflate> junto com <xref:System.Net.DecompressionMethods.GZip>, ou <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="9b452-241">.NET Native only supports <xref:System.Net.DecompressionMethods.Deflate> together with <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="9b452-242">Tentar definir a propriedade <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> para <xref:System.Net.DecompressionMethods.Deflate> ou <xref:System.Net.DecompressionMethods.GZip> sozinho silenciosamente define-a para <xref:System.Net.DecompressionMethods.Deflate> e <xref:System.Net.DecompressionMethods.GZip>.</span><span class="sxs-lookup"><span data-stu-id="9b452-242">Trying to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> property to either <xref:System.Net.DecompressionMethods.Deflate> or <xref:System.Net.DecompressionMethods.GZip> alone silently sets it to both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>.</span></span>  
  
 <span data-ttu-id="9b452-243">**Cookies**</span><span class="sxs-lookup"><span data-stu-id="9b452-243">**Cookies**</span></span>  
  
 <span data-ttu-id="9b452-244">A manipulação de cookies é executada simultaneamente por <xref:System.Net.Http.HttpClient> e WinINet.</span><span class="sxs-lookup"><span data-stu-id="9b452-244">Cookie handling is performed simultaneously by <xref:System.Net.Http.HttpClient> and WinINet.</span></span>  <span data-ttu-id="9b452-245">Os cookies do <xref:System.Net.CookieContainer> são combinados com cookies no cache de cookies do WinINet.</span><span class="sxs-lookup"><span data-stu-id="9b452-245">Cookies from the <xref:System.Net.CookieContainer> are combined with cookies in the WinINet cookie cache.</span></span>  <span data-ttu-id="9b452-246">Remover um cookie do <xref:System.Net.CookieContainer> impede que <xref:System.Net.Http.HttpClient> envie o cookie, mas se o cookie já foi visto pelo WinINet e os cookies não foram excluídos pelo usuário, o WinINet o envia.</span><span class="sxs-lookup"><span data-stu-id="9b452-246">Removing a cookie from <xref:System.Net.CookieContainer> prevents <xref:System.Net.Http.HttpClient> from sending the cookie, but if the cookie was already seen by WinINet, and cookies weren't deleted by the user, WinINet sends it.</span></span>  <span data-ttu-id="9b452-247">Não é possível programar a remoção automática de um cookie do WinINet usando a API <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler> ou <xref:System.Net.CookieContainer>.</span><span class="sxs-lookup"><span data-stu-id="9b452-247">It isn't possible to programmatically remove a cookie from WinINet by using the <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, or <xref:System.Net.CookieContainer> API.</span></span>  <span data-ttu-id="9b452-248">Definir a propriedade <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> para `false` faz com que apenas <xref:System.Net.Http.HttpClient> pare de enviar cookies; o WinINet ainda pode incluir os cookies na solicitação.</span><span class="sxs-lookup"><span data-stu-id="9b452-248">Setting the <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> property to `false` causes only <xref:System.Net.Http.HttpClient> to stop sending cookies; WinINet might still include its cookies in the request.</span></span>  
  
 <span data-ttu-id="9b452-249">**Credenciais**</span><span class="sxs-lookup"><span data-stu-id="9b452-249">**Credentials**</span></span>  
  
 <span data-ttu-id="9b452-250">Em aplicativos .NET para Windows Store, as propriedades <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> e <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> funcionam de forma independente.</span><span class="sxs-lookup"><span data-stu-id="9b452-250">In .NET for Windows Store apps, the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> properties work independently.</span></span>  <span data-ttu-id="9b452-251">Além disso, a propriedade <xref:System.Net.Http.HttpClientHandler.Credentials%2A> aceita qualquer objeto que implemente a interface <xref:System.Net.ICredentials>.</span><span class="sxs-lookup"><span data-stu-id="9b452-251">Additionally, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property accepts any object that implements the <xref:System.Net.ICredentials> interface.</span></span>  <span data-ttu-id="9b452-252">No .NET Native, definindo o <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> propriedade para `true` faz com que o <xref:System.Net.Http.HttpClientHandler.Credentials%2A> propriedade se torne `null`.</span><span class="sxs-lookup"><span data-stu-id="9b452-252">In .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> property to `true` causes the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property to become `null`.</span></span>  <span data-ttu-id="9b452-253">Além disso, a propriedade <xref:System.Net.Http.HttpClientHandler.Credentials%2A> pode ser definida somente para `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A> ou um objeto do tipo <xref:System.Net.NetworkCredential>.</span><span class="sxs-lookup"><span data-stu-id="9b452-253">In addition, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property can be set only to `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, or an object of type <xref:System.Net.NetworkCredential>.</span></span>  <span data-ttu-id="9b452-254">Atribuir de qualquer outro objeto <xref:System.Net.ICredentials>, sendo o mais popular o <xref:System.Net.CredentialCache>, para a propriedade <xref:System.Net.Http.HttpClientHandler.Credentials%2A>, gera uma <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="9b452-254">Assigning any other <xref:System.Net.ICredentials> object, the most popular of which is <xref:System.Net.CredentialCache>, to the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property throws a <xref:System.PlatformNotSupportedException>.</span></span>  
  
 <span data-ttu-id="9b452-255">**Outros recursos sem suporte ou não configuráveis**</span><span class="sxs-lookup"><span data-stu-id="9b452-255">**Other unsupported or unconfigurable features**</span></span>  
  
 <span data-ttu-id="9b452-256">No .NET Native:</span><span class="sxs-lookup"><span data-stu-id="9b452-256">In .NET Native:</span></span>  
  
-   <span data-ttu-id="9b452-257">O valor da propriedade <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> sempre é <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span><span class="sxs-lookup"><span data-stu-id="9b452-257">The value of the <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> property is always <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span></span>  <span data-ttu-id="9b452-258">Em aplicativos .NET para Windows Store, o padrão é <xref:System.Net.Http.ClientCertificateOption.Manual>.</span><span class="sxs-lookup"><span data-stu-id="9b452-258">In .NET for Windows Store apps, the default is <xref:System.Net.Http.ClientCertificateOption.Manual>.</span></span>  
  
-   <span data-ttu-id="9b452-259">A propriedade <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> não é configurável.</span><span class="sxs-lookup"><span data-stu-id="9b452-259">The <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> property isn't configurable.</span></span>  
  
-   <span data-ttu-id="9b452-260">A propriedade <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> sempre é `true`.</span><span class="sxs-lookup"><span data-stu-id="9b452-260">The <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> property is always `true`.</span></span>  <span data-ttu-id="9b452-261">Em aplicativos .NET para Windows Store, o padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="9b452-261">In .NET for Windows Store apps, the default is `false`.</span></span>  
  
-   <span data-ttu-id="9b452-262">O cabeçalho `SetCookie2` em respostas será ignorado como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="9b452-262">The `SetCookie2` header in responses is ignored as obsolete.</span></span>  
  
<a name="Interop"></a>   
### <a name="interop-differences"></a><span data-ttu-id="9b452-263">Diferenças de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="9b452-263">Interop differences</span></span>  
 <span data-ttu-id="9b452-264">**APIs preteridas**</span><span class="sxs-lookup"><span data-stu-id="9b452-264">**Deprecated APIs**</span></span>  
  
 <span data-ttu-id="9b452-265">Várias APIs pouco usadas para a interoperabilidade com código gerenciado foram preteridas.</span><span class="sxs-lookup"><span data-stu-id="9b452-265">A number of infrequently used APIs for interoperability with managed code have been deprecated.</span></span> <span data-ttu-id="9b452-266">Quando usado com o .NET Native, essas APIs pode gerar uma <xref:System.NotImplementedException> ou <xref:System.PlatformNotSupportedException> exceção, ou resultar em um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="9b452-266">When used with .NET Native, these APIs may throw a <xref:System.NotImplementedException> or <xref:System.PlatformNotSupportedException> exception, or result in a compiler error.</span></span> <span data-ttu-id="9b452-267">Em aplicativos .NET para Windows Store, essas APIs são marcadas como obsoletas, embora chamá-las gere um aviso do compilador em vez de um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="9b452-267">In .NET for Windows Store apps, these APIs are marked as obsolete, although calling them generates a compiler warning rather than a compiler error.</span></span>  
  
 <span data-ttu-id="9b452-268">APIs preteridas para `VARIANT` marshaling incluem:</span><span class="sxs-lookup"><span data-stu-id="9b452-268">Deprecated APIs for `VARIANT` marshaling include:</span></span>  

- <xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>  
- <xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>  
- <xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>
  
 <span data-ttu-id="9b452-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> tem suporte, porém gera uma exceção em alguns cenários, por exemplo, quando usado com [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) ou variantes byref.</span><span class="sxs-lookup"><span data-stu-id="9b452-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> is supported, but it throws an exception in some scenarios, such as when it is used with [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) or byref variants.</span></span>  
  
 <span data-ttu-id="9b452-270">APIs preteridas para [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) suporte incluem:</span><span class="sxs-lookup"><span data-stu-id="9b452-270">Deprecated APIs for [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) support include:</span></span>  
  
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual?displayProperty=fullName> 
- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>  

<span data-ttu-id="9b452-271">APIs preteridas para eventos do COM clássico incluem:</span><span class="sxs-lookup"><span data-stu-id="9b452-271">Deprecated APIs for classic COM events include:</span></span>

- <xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>
  
<span data-ttu-id="9b452-272">APIs preteridas no <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, que não tem suporte no .NET Native, incluem:</span><span class="sxs-lookup"><span data-stu-id="9b452-272">Deprecated APIs in the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, which isn't supported in .NET Native, include:</span></span>  
  
- <span data-ttu-id="9b452-273"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (todos os membros)</span><span class="sxs-lookup"><span data-stu-id="9b452-273"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (all members)</span></span>  
- <span data-ttu-id="9b452-274"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (todos os membros)</span><span class="sxs-lookup"><span data-stu-id="9b452-274"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (all members)</span></span>  
- <span data-ttu-id="9b452-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (todos os membros)</span><span class="sxs-lookup"><span data-stu-id="9b452-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (all members)</span></span>  
- <xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>  
  
<span data-ttu-id="9b452-276">Outros recursos de interoperabilidade sem suporte incluem:</span><span class="sxs-lookup"><span data-stu-id="9b452-276">Other unsupported interop features include:</span></span>  
  
- <span data-ttu-id="9b452-277"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (todos os membros)</span><span class="sxs-lookup"><span data-stu-id="9b452-277"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (all members)</span></span>  
- <span data-ttu-id="9b452-278"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (todos os membros)</span><span class="sxs-lookup"><span data-stu-id="9b452-278"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (all members)</span></span>  
- <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.UnmanagedType.AsAny?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler?displayProperty=fullName>  
  
 <span data-ttu-id="9b452-279">APIs de marshalling raramente usadas:</span><span class="sxs-lookup"><span data-stu-id="9b452-279">Rarely used marshalling APIs:</span></span>  
  
- <xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29?displayProperty=fullName>  
  
 <span data-ttu-id="9b452-280">**Invocação de plataforma e compatibilidade de interoperabilidade COM**</span><span class="sxs-lookup"><span data-stu-id="9b452-280">**Platform invoke and COM interop compatibility**</span></span>  
  
 <span data-ttu-id="9b452-281">Invocação de plataforma a maioria das e cenários de interoperabilidade COM ainda são suportados no .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9b452-281">Most platform invoke and COM interop scenarios are still supported in .NET Native.</span></span> <span data-ttu-id="9b452-282">Em especial, toda a interoperabilidade com APIs do Tempo de Execução do Windows (WinRT) APIs e todo o marshaling necessário para o Tempo de Execução do Windows são suportados.</span><span class="sxs-lookup"><span data-stu-id="9b452-282">In particular, all interoperability with Windows Runtime (WinRT) APIs and all marshaling required for the Windows Runtime is supported.</span></span> <span data-ttu-id="9b452-283">Isso inclui suporte a marshaling para:</span><span class="sxs-lookup"><span data-stu-id="9b452-283">This includes marshaling support for:</span></span>  
  
-   <span data-ttu-id="9b452-284">Matrizes (incluindo <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span><span class="sxs-lookup"><span data-stu-id="9b452-284">Arrays (including <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span></span>  
  
-   `BStr`  
  
-   <span data-ttu-id="9b452-285">Representantes</span><span class="sxs-lookup"><span data-stu-id="9b452-285">Delegates</span></span>  
  
-   <span data-ttu-id="9b452-286">Cadeias de caracteres (Unicode, Ansi e HSTRING)</span><span class="sxs-lookup"><span data-stu-id="9b452-286">Strings (Unicode, Ansi, and HSTRING)</span></span>  
  
-   <span data-ttu-id="9b452-287">Estruturas (`byref` e `byval`)</span><span class="sxs-lookup"><span data-stu-id="9b452-287">Structs (`byref` and `byval`)</span></span>  
  
-   <span data-ttu-id="9b452-288">Uniões</span><span class="sxs-lookup"><span data-stu-id="9b452-288">Unions</span></span>  
  
-   <span data-ttu-id="9b452-289">Identificadores do Win32</span><span class="sxs-lookup"><span data-stu-id="9b452-289">Win32 handles</span></span>  
  
-   <span data-ttu-id="9b452-290">Todos os constructos do WinRT</span><span class="sxs-lookup"><span data-stu-id="9b452-290">All WinRT constructs</span></span>  
  
-   <span data-ttu-id="9b452-291">Suporte parcial aos tipos variantes de marshaling.</span><span class="sxs-lookup"><span data-stu-id="9b452-291">Partial support for marshaling variant types.</span></span> <span data-ttu-id="9b452-292">Há suporte para os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="9b452-292">The following are supported:</span></span>  
  
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
  
    -   [<span data-ttu-id="9b452-293">IUnknown</span><span class="sxs-lookup"><span data-stu-id="9b452-293">IUnknown</span></span>](/windows/desktop/api/unknwn/nn-unknwn-iunknown)  
  
 <span data-ttu-id="9b452-294">No entanto, o .NET Native não oferece suporte a seguir:</span><span class="sxs-lookup"><span data-stu-id="9b452-294">However, .NET Native doesn't support the following:</span></span>  
  
-   <span data-ttu-id="9b452-295">Usando os eventos clássicos do COM</span><span class="sxs-lookup"><span data-stu-id="9b452-295">Using classic COM events</span></span>  
  
-   <span data-ttu-id="9b452-296">Implementando a interface <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> em um tipo gerenciado</span><span class="sxs-lookup"><span data-stu-id="9b452-296">Implementing the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface on a managed type</span></span>  
  
-   <span data-ttu-id="9b452-297">Implementando a interface [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) em um tipo gerenciado por meio do atributo <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9b452-297">Implementing the [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) interface on a managed type through the <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="9b452-298">No entanto, observe que você não pode chamar objetos COM por meio de `IDispatch`, e o objeto gerenciado não pode implementar `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="9b452-298">However, note that you can't call COM objects through `IDispatch`, and your managed object can't implement `IDispatch`.</span></span>  
  
 <span data-ttu-id="9b452-299">Usar reflexão para invocar um método de invocação de plataforma não é suportado.</span><span class="sxs-lookup"><span data-stu-id="9b452-299">Using reflection to invoke a platform invoke method isn't supported.</span></span> <span data-ttu-id="9b452-300">Você pode contornar essa limitação envolvendo a chamada de método em outro método e usando reflexão para chamar o wrapper em vez disso.</span><span class="sxs-lookup"><span data-stu-id="9b452-300">You can work around this limitation by wrapping the method call in another method and using reflection to call the wrapper instead.</span></span>  
  
<a name="APIs"></a>   
### <a name="other-differences-from-net-apis-for-windows-store-apps"></a><span data-ttu-id="9b452-301">Outras diferenças das APIs .NET para Windows Store</span><span class="sxs-lookup"><span data-stu-id="9b452-301">Other differences from .NET APIs for Windows Store apps</span></span>  
 <span data-ttu-id="9b452-302">Esta seção lista as APIs restantes que não têm suporte no .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9b452-302">This section lists the remaining APIs that aren't supported in .NET Native.</span></span> <span data-ttu-id="9b452-303">O maior conjunto de APIs sem suporte são APIs do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9b452-303">The largest set of the unsupported APIs are Windows Communication Foundation (WCF) APIs.</span></span>  
  
 <span data-ttu-id="9b452-304">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span><span class="sxs-lookup"><span data-stu-id="9b452-304">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span></span>  
  
 <span data-ttu-id="9b452-305">Os tipos na <xref:System.ComponentModel.DataAnnotations> e <xref:System.ComponentModel.DataAnnotations.Schema> namespaces não têm suporte no .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9b452-305">The types in the <xref:System.ComponentModel.DataAnnotations> and <xref:System.ComponentModel.DataAnnotations.Schema> namespaces aren't supported in .NET Native.</span></span> <span data-ttu-id="9b452-306">Isso inclui os seguintes tipos que estão presentes nos aplicativos do .NET para Windows Store para Windows 8:</span><span class="sxs-lookup"><span data-stu-id="9b452-306">These include the following types that are present in .NET for Windows Store apps for Windows 8:</span></span>  
  
- <xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>
- <xref:System.ComponentModel.DataAnnotations.EditableAttribute>  
- <xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>  
- <xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>  
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>  
  
 <span data-ttu-id="9b452-307">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="9b452-307">**Visual Basic**</span></span>  
  
 <span data-ttu-id="9b452-308">Atualmente, não há suporte para Visual Basic no .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9b452-308">Visual Basic isn't currently supported in .NET Native.</span></span> <span data-ttu-id="9b452-309">Os seguintes tipos na <xref:Microsoft.VisualBasic> e <xref:Microsoft.VisualBasic.CompilerServices> namespaces não estão disponíveis no .NET Native:</span><span class="sxs-lookup"><span data-stu-id="9b452-309">The following types in the <xref:Microsoft.VisualBasic> and <xref:Microsoft.VisualBasic.CompilerServices> namespaces aren't available in .NET Native:</span></span>  

- <xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>  
- <xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>  
  
 <span data-ttu-id="9b452-310">**Contexto de reflexão (namespace System.Reflection.Context)**</span><span class="sxs-lookup"><span data-stu-id="9b452-310">**Reflection Context (System.Reflection.Context namespace)**</span></span>  
  
 <span data-ttu-id="9b452-311">O <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> classe não tem suporte no .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9b452-311">The <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> class isn't supported in .NET Native.</span></span>  
  
 <span data-ttu-id="9b452-312">**RTC (System.Net.Http.Rtc)**</span><span class="sxs-lookup"><span data-stu-id="9b452-312">**RTC (System.Net.Http.Rtc)**</span></span>  
  
 <span data-ttu-id="9b452-313">O `System.Net.Http.RtcRequestFactory` classe não tem suporte no .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9b452-313">The `System.Net.Http.RtcRequestFactory` class isn't supported in .NET Native.</span></span>  
  
 <span data-ttu-id="9b452-314">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span><span class="sxs-lookup"><span data-stu-id="9b452-314">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span></span>  
  
 <span data-ttu-id="9b452-315">Os tipos na [ServiceModel namespaces](xref:System.ServiceModel) não têm suporte no .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9b452-315">The types in the [System.ServiceModel.\* namespaces](xref:System.ServiceModel) aren't supported in .NET Native.</span></span> <span data-ttu-id="9b452-316">Eles incluem os seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="9b452-316">These includes the following types:</span></span>  
  
- <xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>  
- <xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>  
- <xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>  
- <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>  
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>  
- <xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>  
- <xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>  
- <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>  
- <xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>  
- <xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>  
- <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>  
- <xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>  
- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>  
- <xref:System.ServiceModel.FaultException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>  
- <xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>  
- <xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>  
- <xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>  
- <xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>  
- <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>  
- <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>  
- <xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>  
- <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>  
- <xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>  
- <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>  
- <xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>  
- <xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>  
- <xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>  
- <xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>  
- <xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>  
- <xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>  
- <xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>  
- <xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>  
- <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>  
- <xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>  
- <xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>  
- <xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>  
- <xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>  
- <xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>  
- <xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>  
- <xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>  
- <xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>  
- <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>  
  
### <a name="differences-in-serializers"></a><span data-ttu-id="9b452-317">Diferenças nos serializadores</span><span class="sxs-lookup"><span data-stu-id="9b452-317">Differences in serializers</span></span>  
 <span data-ttu-id="9b452-318">As seguintes diferenças envolvem serialização e desserialização com e classes <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> e <xref:System.Xml.Serialization.XmlSerializer>:</span><span class="sxs-lookup"><span data-stu-id="9b452-318">The following differences concern serialization and deserialization with the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes:</span></span>  
  
-   <span data-ttu-id="9b452-319">No .NET Native <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> falham ao serializar ou desserializar uma classe derivada que tem um membro de classe base cujo tipo não é um tipo de serialização de raiz.</span><span class="sxs-lookup"><span data-stu-id="9b452-319">In .NET Native, <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize or deserialize a derived class that has a base class member whose type isn't a root serialization type.</span></span> <span data-ttu-id="9b452-320">Por exemplo, no código a seguir, tentar serializar ou desserializar `Y` resulta em um erro:</span><span class="sxs-lookup"><span data-stu-id="9b452-320">For example, in the following code, trying to serialize or deserialize `Y` results in an error:</span></span>  
  
     [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]  
  
     <span data-ttu-id="9b452-321">O tipo `InnerType` não é conhecido pelo serializador, pois os membros da classe base não são percorridos durante a serialização.</span><span class="sxs-lookup"><span data-stu-id="9b452-321">Type `InnerType` isn't known to the serializer, because the members of the base class aren't traversed during serialization.</span></span>  
  
-   <span data-ttu-id="9b452-322"><xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> não conseguem serializar uma classe ou estrutura que implementa a interface <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="9b452-322"><xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize a class or structure that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="9b452-323">Por exemplo, os seguintes tipos falham ao serializar ou desserializar:</span><span class="sxs-lookup"><span data-stu-id="9b452-323">For example, the following types fail to serialize or deserialize:</span></span>  
  
  
  
-   <span data-ttu-id="9b452-324"><xref:System.Xml.Serialization.XmlSerializer> falha ao serializar o valor de objeto a seguir, porque não sabe o tipo exato de objeto a ser serializado:</span><span class="sxs-lookup"><span data-stu-id="9b452-324"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize the following object value, because it doesn't know the exact type of the object to be serialized:</span></span>  
  
  
  
-   <span data-ttu-id="9b452-325"><xref:System.Xml.Serialization.XmlSerializer> falha ao serializar ou desserializar se o tipo do objeto serializado é <xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="9b452-325"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize or deserialize if the type of the serialized object is <xref:System.Xml.XmlQualifiedName>.</span></span>  
  
-   <span data-ttu-id="9b452-326">Todos os serializadores (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> e <xref:System.Xml.Serialization.XmlSerializer>) falham ao gerar o código de serialização para tipo <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> ou para um tipo que contém <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="9b452-326">All serializers (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer>) fail to generate serialization code for type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> or for a type that contains <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="9b452-327">Eles exibem erros de tempo de compilação em vez disso.</span><span class="sxs-lookup"><span data-stu-id="9b452-327">They display build-time errors instead.</span></span>  
  
-   <span data-ttu-id="9b452-328">Não há garantia que os seguintes construtores dos tipos de serialização funcionem conforme o esperado:</span><span class="sxs-lookup"><span data-stu-id="9b452-328">The following constructors of the serialization types aren't guaranteed to work as expected:</span></span>  
  
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
  
-   <span data-ttu-id="9b452-329">O <xref:System.Xml.Serialization.XmlSerializer> falha ao gerar o código para um tipo que tem métodos atribuídos com qualquer um dos seguintes atributos:</span><span class="sxs-lookup"><span data-stu-id="9b452-329"><xref:System.Xml.Serialization.XmlSerializer> fails to generate code for a type that has methods attributed with any of the following attributes:</span></span>  
  
    -   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <span data-ttu-id="9b452-330">O <xref:System.Xml.Serialization.XmlSerializer> não aceita a interface de serialização personalizada <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="9b452-330"><xref:System.Xml.Serialization.XmlSerializer> doesn't honor the <xref:System.Xml.Serialization.IXmlSerializable> custom serialization interface.</span></span> <span data-ttu-id="9b452-331">Se você tiver uma classe que implementa essa interface, <xref:System.Xml.Serialization.XmlSerializer> considera o tipo como um objeto CLR (POCO) antigo simples, serializando apenas suas propriedades públicas.</span><span class="sxs-lookup"><span data-stu-id="9b452-331">If you have a class that implements this interface, <xref:System.Xml.Serialization.XmlSerializer> considers the type a plain old CLR object (POCO) type and serializes only its public properties.</span></span>  
  
-   <span data-ttu-id="9b452-332">Serializar um objeto <xref:System.Exception> simples, como a seguir, não funciona bem com <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:</span><span class="sxs-lookup"><span data-stu-id="9b452-332">Serializing a plain <xref:System.Exception> object, such as the following, doesn't work well with <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:</span></span>  
  
  
  
<a name="VS"></a>   
## <a name="visual-studio-differences"></a><span data-ttu-id="9b452-333">Diferenças do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9b452-333">Visual Studio differences</span></span>  
 <span data-ttu-id="9b452-334">**Exceções e depuração**</span><span class="sxs-lookup"><span data-stu-id="9b452-334">**Exceptions and debugging**</span></span>  
  
 <span data-ttu-id="9b452-335">Quando você estiver executando aplicativos compilados usando o .NET Native no depurador, exceções de primeira chance são habilitadas para os seguintes tipos de exceção:</span><span class="sxs-lookup"><span data-stu-id="9b452-335">When you're running apps compiled by using .NET Native in the debugger, first-chance exceptions are enabled for the following exception types:</span></span>  
  
-   <xref:System.MemberAccessException>  
  
-   <xref:System.TypeAccessException>  
  
 <span data-ttu-id="9b452-336">**Criando aplicativos**</span><span class="sxs-lookup"><span data-stu-id="9b452-336">**Building apps**</span></span>  
  
 <span data-ttu-id="9b452-337">Use as ferramentas de criação x86 usadas por padrão pelo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9b452-337">Use the x86 build tools that are used by default by Visual Studio.</span></span> <span data-ttu-id="9b452-338">Não recomendamos usar as ferramentas AMD64 MSBuild, que se encontram em C:\Program Files (x86)\MSBuild\12.0\bin\amd64, pois podem criar problemas de compilação.</span><span class="sxs-lookup"><span data-stu-id="9b452-338">We don't recommend using the AMD64 MSBuild tools, which are found in C:\Program Files (x86)\MSBuild\12.0\bin\amd64; these may create build problems.</span></span>  
  
 <span data-ttu-id="9b452-339">**Criadores de perfil**</span><span class="sxs-lookup"><span data-stu-id="9b452-339">**Profilers**</span></span>  
  
-   <span data-ttu-id="9b452-340">O criador de perfil de CPU do Visual Studio e o criador de perfil de memória XAML não exibem o Just-My-Code corretamente.</span><span class="sxs-lookup"><span data-stu-id="9b452-340">The Visual Studio CPU Profiler and XAML Memory Profiler don't display Just-My-Code correctly.</span></span>  
  
-   <span data-ttu-id="9b452-341">O gerador de perfil de memória XAML não exibe corretamente os dados da pilha gerenciada.</span><span class="sxs-lookup"><span data-stu-id="9b452-341">The XAML Memory Profiler doesn't accurately display managed heap data.</span></span>  
  
-   <span data-ttu-id="9b452-342">O gerador de perfil de CPU não identifica corretamente módulos e exibe nomes de função de prefixo.</span><span class="sxs-lookup"><span data-stu-id="9b452-342">The CPU Profiler doesn't correctly identify modules, and displays prefixed function names.</span></span>  
  
 <span data-ttu-id="9b452-343">**Projetos da biblioteca de teste de unidade**</span><span class="sxs-lookup"><span data-stu-id="9b452-343">**Unit Test Library projects**</span></span>  
  
 <span data-ttu-id="9b452-344">Habilitar o .NET nativo em uma biblioteca de teste de unidade para um projeto de aplicativos da Windows Store não é suportada e faz com que o projeto de compilação.</span><span class="sxs-lookup"><span data-stu-id="9b452-344">Enabling .NET Native on a Unit Test Library for a Windows Store apps project isn't supported and causes the project to fail to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b452-345">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b452-345">See Also</span></span>  
 [<span data-ttu-id="9b452-346">Introdução</span><span class="sxs-lookup"><span data-stu-id="9b452-346">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [<span data-ttu-id="9b452-347">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="9b452-347">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="9b452-348">Visão geral de aplicativos .NET para Windows Store</span><span class="sxs-lookup"><span data-stu-id="9b452-348">.NET For Windows Store apps overview</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)  
 [<span data-ttu-id="9b452-349">Suporte do .NET Framework para Aplicativos da Windows Store e Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="9b452-349">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
