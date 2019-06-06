---
title: O que está obsoleto na biblioteca de classes do .NET Framework
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7db411e9ef38adb42c8df2059d166d1fa4184f95
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378369"
---
# <a name="whats-obsolete-in-the-net-framework-class-library"></a><span data-ttu-id="a3a54-102">O que está obsoleto na biblioteca de classes do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a3a54-102">What's obsolete in the .NET Framework class library</span></span>

<span data-ttu-id="a3a54-103">O .NET Framework muda com o passar do tempo.</span><span class="sxs-lookup"><span data-stu-id="a3a54-103">The .NET Framework changes over time.</span></span> <span data-ttu-id="a3a54-104">Cada nova versão adiciona novos tipos e membros de tipo que oferecem uma nova funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="a3a54-104">Each new version adds new types and type members that provide new functionality.</span></span> <span data-ttu-id="a3a54-105">Tipos existentes e seus membros também mudam com o passar do tempo.</span><span class="sxs-lookup"><span data-stu-id="a3a54-105">Existing types and their members also change over time.</span></span> <span data-ttu-id="a3a54-106">Por exemplo, alguns tipos se tornam menos importantes conforme a tecnologia compatível é substituída por uma nova tecnologia e alguns métodos são substituídos por métodos mais novos que sejam mais práticos ou mais repletos de recursos.</span><span class="sxs-lookup"><span data-stu-id="a3a54-106">For example, some types become less important as the technology they support is replaced by a new technology, and some methods are superseded by newer methods that are either more convenient or more full-featured.</span></span>

<span data-ttu-id="a3a54-107">O .NET Framework e o Common Language Runtime procuram dar suporte à compatibilidade com versões anteriores (permitindo que aplicativos desenvolvidos com uma versão do .NET Framework sejam executados na próxima versão do .NET Framework).</span><span class="sxs-lookup"><span data-stu-id="a3a54-107">The .NET Framework and the common language runtime strive to support backward compatibility (allowing applications that were developed with one version of the .NET Framework to run on the next version of the .NET Framework).</span></span> <span data-ttu-id="a3a54-108">Isso dificulta a simples remoção de um tipo ou de um membro de tipo.</span><span class="sxs-lookup"><span data-stu-id="a3a54-108">This makes it difficult to simply remove a type or a type member.</span></span> <span data-ttu-id="a3a54-109">Em vez disso, o .NET Framework indica que um tipo ou um membro de tipo não deve mais ser usado marcando-o como obsoleto ou substituído.</span><span class="sxs-lookup"><span data-stu-id="a3a54-109">Instead, the .NET Framework indicates that a type or a type member should no longer be used by marking it as obsolete or deprecated.</span></span> <span data-ttu-id="a3a54-110">A substituição de um tipo ou membro envolve marcá-lo para que os desenvolvedores estejam cientes de que eles sumirão e tenham tempo para responder a essa remoção.</span><span class="sxs-lookup"><span data-stu-id="a3a54-110">Deprecating a type or a member involves marking it so that developers are aware it will go away and have time to respond to its removal.</span></span> <span data-ttu-id="a3a54-111">No entanto, o código existente que usa o tipo ou o membro continua sendo executado na nova versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a3a54-111">However, existing code that uses the type or member continues to run in the new version of the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="a3a54-112">Os termos *obsoleto* e *preterido* têm o mesmo significado quando aplicados aos tipos e membros do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a3a54-112">The terms *obsolete* and *deprecated* have the same meaning when applied to the types and members of the .NET Framework.</span></span>

## <a name="the-obsoleteattribute-attribute"></a><span data-ttu-id="a3a54-113">O atributo ObsoleteAttribute</span><span class="sxs-lookup"><span data-stu-id="a3a54-113">The ObsoleteAttribute attribute</span></span>

<span data-ttu-id="a3a54-114">O .NET Framework indica que um tipo ou um membro de tipo está obsoleto marcando-o com o atributo <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a3a54-114">The .NET Framework indicates that a type or type member is obsolete by marking it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="a3a54-115">A aplicação do atributo a um tipo ou um membro indica que esse tipo ou membro será removido em qualquer versão futura do .NET Framework sem interromper o código compilado que usa esse membro.</span><span class="sxs-lookup"><span data-stu-id="a3a54-115">Applying the attribute to a type or member indicates that type or member will be removed in some future version of the .NET Framework without breaking compiled code that uses that member.</span></span>

<span data-ttu-id="a3a54-116">Além de indicar que um tipo ou membro de tipo é obsoleto, <xref:System.ObsoleteAttribute> define como o compilador identifica o código-fonte que inclui esse tipo ou membro.</span><span class="sxs-lookup"><span data-stu-id="a3a54-116">In addition to indicating that a type or a type member is obsolete, <xref:System.ObsoleteAttribute> defines how the compiler handles source code that includes that type or member.</span></span> <span data-ttu-id="a3a54-117">O compilador pode compilar o código, mas emite uma mensagem de aviso, ou pode tratar o uso do tipo ou do membro como um erro.</span><span class="sxs-lookup"><span data-stu-id="a3a54-117">The compiler can compile the code but emit a warning message, or it can treat the use of the type or member as an error.</span></span> <span data-ttu-id="a3a54-118">No primeiro caso, o código pode ser compilado com êxito, mas uma mensagem de aviso indica que o tipo ou o membro é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="a3a54-118">In the first case, the code can successfully compile, but a warning message indicates that the type or member is obsolete.</span></span> <span data-ttu-id="a3a54-119">No segundo caso, a compilação falha.</span><span class="sxs-lookup"><span data-stu-id="a3a54-119">In the second case, compilation fails.</span></span>

<span data-ttu-id="a3a54-120">Mesmo se a compilação produzir um erro em vez de uma mensagem de aviso, o <xref:System.ObsoleteAttribute> não afetará o comportamento do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a3a54-120">Even if compilation produces an error instead of a warning message, <xref:System.ObsoleteAttribute> does not affect run-time behavior.</span></span> <span data-ttu-id="a3a54-121">Ou seja, os aplicativos que usam o tipo ou o membro e que são compilados com êxito sempre terão êxito.</span><span class="sxs-lookup"><span data-stu-id="a3a54-121">That is, applications that use the type or member and that have compiled successfully will always run successfully.</span></span> <span data-ttu-id="a3a54-122">Somente a tentativa de recompilar um aplicativo que use o tipo ou o membro falha.</span><span class="sxs-lookup"><span data-stu-id="a3a54-122">Only the attempt to recompile an application that uses the type or member fails.</span></span>

## <a name="how-to-handle-obsolete-types-and-members"></a><span data-ttu-id="a3a54-123">Como lidar com tipos e membros obsoletos</span><span class="sxs-lookup"><span data-stu-id="a3a54-123">How to handle obsolete types and members</span></span>

<span data-ttu-id="a3a54-124">Quando você atualiza e depois recompila o código existente, o uso de um tipo ou de um membro obsoleto que produza um aviso do compilador em seu aplicativo é perfeitamente aceitável.</span><span class="sxs-lookup"><span data-stu-id="a3a54-124">When you upgrade and recompile existing code, using an obsolete type or member that produces a compiler warning in your application is perfectly acceptable.</span></span> <span data-ttu-id="a3a54-125">No entanto, você deve examinar a mensagem de aviso do compilador para determinar se você deve alterar o código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a3a54-125">However, you should review the compiler warning message to determine whether you should change your application code.</span></span> <span data-ttu-id="a3a54-126">Se a mensagem não apontar para uma alternativa adequada, você deverá fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a3a54-126">If the message does not point to a suitable alternative, you should do either of the following:</span></span>

- <span data-ttu-id="a3a54-127">Altere seu código removendo o uso do tipo ou do membro, se possível.</span><span class="sxs-lookup"><span data-stu-id="a3a54-127">Change your code by removing the use of the type or member, if possible.</span></span>

     <span data-ttu-id="a3a54-128">- ou -</span><span class="sxs-lookup"><span data-stu-id="a3a54-128">-or-</span></span>

- <span data-ttu-id="a3a54-129">Examine a documentação dessa área de tecnologia para determinar como responder à substituição.</span><span class="sxs-lookup"><span data-stu-id="a3a54-129">Review the documentation for this technology area to determine how to respond to the deprecation.</span></span>

<span data-ttu-id="a3a54-130">Você pode optar por não recompilar o código existente em comparação com uma versão posterior do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a3a54-130">You may choose not to recompile existing code against a later version of the .NET Framework.</span></span> <span data-ttu-id="a3a54-131">Em vez disso, você pode especificar a versão do .NET Framework na qual o código existente compilado é executado.</span><span class="sxs-lookup"><span data-stu-id="a3a54-131">Instead, you can specify the version of the .NET Framework against which your existing compiled code runs.</span></span> <span data-ttu-id="a3a54-132">Por exemplo, vamos supor que você tenha um aplicativo chamado app1.exe compilado no [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], mas queira que o aplicativo seja executado no .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="a3a54-132">For example, suppose that you have an application named app1.exe that was compiled against the [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], but you want the application to run against the .NET Framework 4.5.</span></span> <span data-ttu-id="a3a54-133">Isso exige as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="a3a54-133">This requires the following steps:</span></span>

1. <span data-ttu-id="a3a54-134">Crie um arquivo de configuração para o executável principal e denomine-o *appName*.exe.config, em que *appName* é o nome do executável do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a3a54-134">Create a configuration file for your main executable and name it *appName*.exe.config, where *appName* is the name of the application executable.</span></span> <span data-ttu-id="a3a54-135">Para o aplicativo chamado app1.exe em nosso exemplo, você criaria um arquivo de configuração chamado app1.exe.config.</span><span class="sxs-lookup"><span data-stu-id="a3a54-135">For the application named app1.exe in our example, you would create a configuration file named app1.exe.config.</span></span>

2. <span data-ttu-id="a3a54-136">Adicione o seguinte ao arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="a3a54-136">Add the following to the configuration file.</span></span>

    ```xml
    <configuration>
       <startup> 
          <supportedRuntime version="v4.0" />
       </startup>
    </configuration>
    ```

<span data-ttu-id="a3a54-137">A tabela a seguir lista os valores da cadeia de caracteres que você pode atribuir ao atributo `version` para segmentar uma versão específica do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="a3a54-137">The following table lists the string values that you can assign to the `version` attribute to target a specific version of the .NET Framework:</span></span>

|<span data-ttu-id="a3a54-138">Versão do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a3a54-138">.NET Framework version</span></span>|<span data-ttu-id="a3a54-139">Cadeia de caracteres `version`</span><span class="sxs-lookup"><span data-stu-id="a3a54-139">`version` string</span></span>|
|-|-|
|<span data-ttu-id="a3a54-140">4.8</span><span class="sxs-lookup"><span data-stu-id="a3a54-140">4.8</span></span>|<span data-ttu-id="a3a54-141">v4.0</span><span class="sxs-lookup"><span data-stu-id="a3a54-141">v4.0</span></span>|
|<span data-ttu-id="a3a54-142">4.7 (incluindo 4.7.1 e 4.7.2)</span><span class="sxs-lookup"><span data-stu-id="a3a54-142">4.7 (including 4.7.1 and 4.7.2)</span></span>|<span data-ttu-id="a3a54-143">v4.0</span><span class="sxs-lookup"><span data-stu-id="a3a54-143">v4.0</span></span>|
|<span data-ttu-id="a3a54-144">4.6 (incluindo 4.6.1 e 4.6.2)</span><span class="sxs-lookup"><span data-stu-id="a3a54-144">4.6 (including 4.6.1 and 4.6.2)</span></span>|<span data-ttu-id="a3a54-145">v4.0</span><span class="sxs-lookup"><span data-stu-id="a3a54-145">v4.0</span></span>|
|<span data-ttu-id="a3a54-146">4.5 (incluindo 4.5.1 e 4.5.2)</span><span class="sxs-lookup"><span data-stu-id="a3a54-146">4.5 (including 4.5.1 and 4.5.2)</span></span>|<span data-ttu-id="a3a54-147">v4.0</span><span class="sxs-lookup"><span data-stu-id="a3a54-147">v4.0</span></span>|
|<span data-ttu-id="a3a54-148">4</span><span class="sxs-lookup"><span data-stu-id="a3a54-148">4</span></span>|<span data-ttu-id="a3a54-149">v4.0</span><span class="sxs-lookup"><span data-stu-id="a3a54-149">v4.0</span></span>|
|<span data-ttu-id="a3a54-150">3.5</span><span class="sxs-lookup"><span data-stu-id="a3a54-150">3.5</span></span>|<span data-ttu-id="a3a54-151">v2.0.50727</span><span class="sxs-lookup"><span data-stu-id="a3a54-151">v2.0.50727</span></span>|
|<span data-ttu-id="a3a54-152">2.0</span><span class="sxs-lookup"><span data-stu-id="a3a54-152">2.0</span></span>|<span data-ttu-id="a3a54-153">v2.0.50727</span><span class="sxs-lookup"><span data-stu-id="a3a54-153">v2.0.50727</span></span>|
|<span data-ttu-id="a3a54-154">1.1</span><span class="sxs-lookup"><span data-stu-id="a3a54-154">1.1</span></span>|<span data-ttu-id="a3a54-155">v1.1.4322</span><span class="sxs-lookup"><span data-stu-id="a3a54-155">v1.1.4322</span></span>|
|<span data-ttu-id="a3a54-156">1.0</span><span class="sxs-lookup"><span data-stu-id="a3a54-156">1.0</span></span>|<span data-ttu-id="a3a54-157">v1.0.3705</span><span class="sxs-lookup"><span data-stu-id="a3a54-157">v1.0.3705</span></span>|

## <a name="obsolete-lists-for-the-net-framework-45-and-later-versions"></a><span data-ttu-id="a3a54-158">Listas obsoletas para o .NET Framework 4.5 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="a3a54-158">Obsolete lists for the .NET Framework 4.5 and later versions</span></span>

- [<span data-ttu-id="a3a54-159">Tipos obsoletos</span><span class="sxs-lookup"><span data-stu-id="a3a54-159">Obsolete Types</span></span>](obsolete-types.md)
- [<span data-ttu-id="a3a54-160">Membros obsoletos</span><span class="sxs-lookup"><span data-stu-id="a3a54-160">Obsolete Members</span></span>](obsolete-members.md)

## <a name="obsolete-lists-for-previous-versions"></a><span data-ttu-id="a3a54-161">Listas obsoletas de versões anteriores</span><span class="sxs-lookup"><span data-stu-id="a3a54-161">Obsolete lists for previous versions</span></span>

- <span data-ttu-id="a3a54-162">[Tipos obsoletos no .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a3a54-162">[Obsolete Types in the .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))</span></span>

- <span data-ttu-id="a3a54-163">[Membros obsoletos no .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a3a54-163">[Obsolete Members in the .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))</span></span>

- <span data-ttu-id="a3a54-164">[Lista obsoleta do .NET Framework 3.5](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="a3a54-164">[.NET Framework 3.5 Obsolete List](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))</span></span>

- <span data-ttu-id="a3a54-165">[Lista obsoleta do .NET Framework 2.0](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="a3a54-165">[.NET Framework 2.0 Obsolete List](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))</span></span>

## <a name="see-also"></a><span data-ttu-id="a3a54-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3a54-166">See also</span></span>

- <span data-ttu-id="a3a54-167">Elemento [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md)</span><span class="sxs-lookup"><span data-stu-id="a3a54-167">[\<supportedRuntime> Element](../configure-apps/file-schema/startup/supportedruntime-element.md)</span></span>
