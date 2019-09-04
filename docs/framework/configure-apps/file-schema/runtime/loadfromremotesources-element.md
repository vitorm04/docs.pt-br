---
title: Elemento <loadFromRemoteSources>
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83980d315c83aa5cc23944dbd271c29e0ed83206
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252474"
---
# <a name="loadfromremotesources-element"></a><span data-ttu-id="7840e-102">\<elemento de > loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="7840e-102">\<loadFromRemoteSources> element</span></span>
<span data-ttu-id="7840e-103">Especifica se os assemblies carregados de fontes remotas devem receber confiança total no .NET Framework 4 e posterior.</span><span class="sxs-lookup"><span data-stu-id="7840e-103">Specifies whether assemblies loaded from remote sources should be granted full trust in .NET Framework 4 and later.</span></span>
  
> [!NOTE]
> <span data-ttu-id="7840e-104">Se você foi direcionado para este artigo devido a uma mensagem de erro na lista de erros do projeto do Visual Studio ou um [erro de compilação, consulte Como: Use um assembly da Web no Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="7840e-104">If you were directed to this article because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span></span>  
  
<span data-ttu-id="7840e-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7840e-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7840e-106">&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="7840e-106">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="7840e-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<> loadFromRemoteSources**</span><span class="sxs-lookup"><span data-stu-id="7840e-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<loadFromRemoteSources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7840e-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7840e-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7840e-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7840e-109">Attributes and elements</span></span>
 <span data-ttu-id="7840e-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7840e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7840e-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="7840e-111">Attributes</span></span>  
  
|<span data-ttu-id="7840e-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="7840e-112">Attribute</span></span>|<span data-ttu-id="7840e-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="7840e-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="7840e-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="7840e-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="7840e-115">Especifica se um assembly que é carregado de uma fonte remota deve receber confiança total.</span><span class="sxs-lookup"><span data-stu-id="7840e-115">Specifies whether an assembly that is loaded from a remote source should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7840e-116">atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="7840e-116">enabled attribute</span></span>  
  
|<span data-ttu-id="7840e-117">Valor</span><span class="sxs-lookup"><span data-stu-id="7840e-117">Value</span></span>|<span data-ttu-id="7840e-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="7840e-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="7840e-119">Não conceda confiança total a aplicativos de fontes remotas.</span><span class="sxs-lookup"><span data-stu-id="7840e-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="7840e-120">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="7840e-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="7840e-121">Conceda confiança total a aplicativos de fontes remotas.</span><span class="sxs-lookup"><span data-stu-id="7840e-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7840e-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7840e-122">Child elements</span></span>  
 <span data-ttu-id="7840e-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7840e-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7840e-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7840e-124">Parent elements</span></span>  
  
|<span data-ttu-id="7840e-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="7840e-125">Element</span></span>|<span data-ttu-id="7840e-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="7840e-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7840e-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7840e-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7840e-128">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7840e-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7840e-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="7840e-129">Remarks</span></span>

<span data-ttu-id="7840e-130">No .NET Framework 3,5 e versões anteriores, se você carregar um assembly de um local remoto, o código no assembly será executado em confiança parcial com um conjunto de concessão que depende da zona da qual ele está carregado.</span><span class="sxs-lookup"><span data-stu-id="7840e-130">In the .NET Framework 3.5 and earlier versions, if you load an assembly from a remote location, code in the assembly runs in partial trust with a grant set that depends on the zone from which it is loaded.</span></span> <span data-ttu-id="7840e-131">Por exemplo, se você carregar um assembly de um site, ele será carregado na zona da Internet e terá o conjunto de permissões da Internet.</span><span class="sxs-lookup"><span data-stu-id="7840e-131">For example, if you load an assembly from a website, it is loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="7840e-132">Em outras palavras, ele é executado em uma área restrita da Internet.</span><span class="sxs-lookup"><span data-stu-id="7840e-132">In other words, it executes in an Internet sandbox.</span></span>

<span data-ttu-id="7840e-133">A partir do .NET Framework 4, a política de CAS (segurança de acesso ao código) é desabilitada e os assemblies são carregados em confiança total.</span><span class="sxs-lookup"><span data-stu-id="7840e-133">Starting with the .NET Framework 4, code access security (CAS) policy is disabled and assemblies are loaded in full trust.</span></span> <span data-ttu-id="7840e-134">Normalmente, isso concederia confiança total a assemblies carregados com o <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> método que anteriormente estava na área restrita.</span><span class="sxs-lookup"><span data-stu-id="7840e-134">Ordinarily, this would grant full trust to assemblies loaded with the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method that previously had been sandboxed.</span></span> <span data-ttu-id="7840e-135">Para evitar isso, a capacidade de executar código em assemblies carregados de uma fonte remota é desabilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="7840e-135">To prevent this, the ability to run code in assemblies loaded from a remote source is disabled by default.</span></span> <span data-ttu-id="7840e-136">Por padrão, se você tentar carregar um assembly remoto, um <xref:System.IO.FileLoadException> com uma mensagem de exceção semelhante à seguinte será lançada:</span><span class="sxs-lookup"><span data-stu-id="7840e-136">By default, if you attempt to load a remote assembly, a <xref:System.IO.FileLoadException> with an exception message like the following is thrown:</span></span>

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported. 
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' ---> 
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly 
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default, 
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch. 
```

<span data-ttu-id="7840e-137">Para carregar o assembly e executar seu código, você deve:</span><span class="sxs-lookup"><span data-stu-id="7840e-137">To load the assembly and execute its code, you must either:</span></span>

- <span data-ttu-id="7840e-138">Crie explicitamente uma área restrita para o assembly ( [consulte Como: Executar código parcialmente confiável em uma área](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)restrita).</span><span class="sxs-lookup"><span data-stu-id="7840e-138">Explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span></span>

- <span data-ttu-id="7840e-139">Execute o código do assembly em confiança total.</span><span class="sxs-lookup"><span data-stu-id="7840e-139">Run the assembly's code in full trust.</span></span> <span data-ttu-id="7840e-140">Você faz isso Configurando `<loadFromRemoteSources>` o elemento.</span><span class="sxs-lookup"><span data-stu-id="7840e-140">You do this by configuring the `<loadFromRemoteSources>` element.</span></span> <span data-ttu-id="7840e-141">Ele permite que você especifique que os assemblies que são executados em confiança parcial em versões anteriores do .NET Framework agora são executados com confiança total no .NET Framework 4 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="7840e-141">It lets you specify that the assemblies that run in partial trust in earlier versions of the .NET Framework now run in full trust in the .NET Framework 4 and later versions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7840e-142">Se o assembly não deve ser executado com confiança total, não defina este elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="7840e-142">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="7840e-143">Em vez disso, crie uma <xref:System.AppDomain> área restrita na qual carregar o assembly.</span><span class="sxs-lookup"><span data-stu-id="7840e-143">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>

<span data-ttu-id="7840e-144">O `enabled` atributo para o `<loadFromRemoteSources>` elemento é efetivo somente quando a segurança de acesso ao código (CAS) está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="7840e-144">The `enabled` attribute for the `<loadFromRemoteSources>` element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="7840e-145">Por padrão, a política de CAS é desabilitada no .NET Framework 4 e em versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="7840e-145">By default, CAS policy is disabled in the .NET Framework 4 and later versions.</span></span> <span data-ttu-id="7840e-146">Se você definir `enabled` como `true`, os assemblies remotos recebem confiança total.</span><span class="sxs-lookup"><span data-stu-id="7840e-146">If you set `enabled` to `true`, remote assemblies are granted full trust.</span></span>

<span data-ttu-id="7840e-147">Se `enabled` não estiver definido como `true`, um <xref:System.IO.FileLoadException> será lançado sob uma das seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="7840e-147">If `enabled` is not set to `true`, a <xref:System.IO.FileLoadException> is thrown under the either of the following conditions:</span></span>

- <span data-ttu-id="7840e-148">O comportamento de área restrita do domínio atual é diferente do seu comportamento no .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="7840e-148">The sandboxing behavior of the current domain is different from its behavior in the .NET Framework 3.5.</span></span> <span data-ttu-id="7840e-149">Isso requer que a política de CAS seja desabilitada e o domínio atual não seja colocado em área restrita.</span><span class="sxs-lookup"><span data-stu-id="7840e-149">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>

- <span data-ttu-id="7840e-150">O assembly que está sendo carregado não é `MyComputer` da zona.</span><span class="sxs-lookup"><span data-stu-id="7840e-150">The assembly being loaded is not from the `MyComputer` zone.</span></span>

<span data-ttu-id="7840e-151">Definindo o `<loadFromRemoteSources>` elemento para `true` impedir que essa exceção seja gerada.</span><span class="sxs-lookup"><span data-stu-id="7840e-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="7840e-152">Ele permite que você especifique que você não depende do Common Language Runtime para colocar os assemblies carregados em área restrita para segurança e que eles podem ter permissão para serem executados em confiança total.</span><span class="sxs-lookup"><span data-stu-id="7840e-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute in full trust.</span></span>

## <a name="notes"></a><span data-ttu-id="7840e-153">Observações</span><span class="sxs-lookup"><span data-stu-id="7840e-153">Notes</span></span>

- <span data-ttu-id="7840e-154">No .NET Framework 4,5 e versões posteriores, os assemblies em compartilhamentos de rede local são executados em confiança total por padrão; Você não precisa habilitar o `<loadFromRemoteSources>` elemento.</span><span class="sxs-lookup"><span data-stu-id="7840e-154">In the .NET Framework 4.5 and later versions, assemblies on local network shares run in full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>

- <span data-ttu-id="7840e-155">Se um aplicativo tiver sido copiado da Web, ele será sinalizado pelo Windows como sendo um aplicativo Web, mesmo que ele resida no computador local.</span><span class="sxs-lookup"><span data-stu-id="7840e-155">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="7840e-156">Você pode alterar essa designação alterando suas propriedades de arquivo ou pode usar o `<loadFromRemoteSources>` elemento para conceder confiança total ao assembly.</span><span class="sxs-lookup"><span data-stu-id="7840e-156">You can change that designation by changing its file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="7840e-157">Como alternativa, você pode usar o <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> método para carregar um assembly local que o sistema operacional tenha sinalizado como tendo sido carregado da Web.</span><span class="sxs-lookup"><span data-stu-id="7840e-157">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>

- <span data-ttu-id="7840e-158">Você pode obter um <xref:System.IO.FileLoadException> em um aplicativo que está sendo executado em um aplicativo do Windows Virtual PC.</span><span class="sxs-lookup"><span data-stu-id="7840e-158">You may get a <xref:System.IO.FileLoadException> in an application that is running in a Windows Virtual PC application.</span></span> <span data-ttu-id="7840e-159">Isso pode acontecer quando você tenta carregar um arquivo de pastas vinculadas no computador host.</span><span class="sxs-lookup"><span data-stu-id="7840e-159">This can happen when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="7840e-160">Ele também pode ocorrer quando você tenta carregar um arquivo de uma pasta vinculada por [serviços de área de trabalho remota](https://go.microsoft.com/fwlink/?LinkId=182775) (serviços de terminal).</span><span class="sxs-lookup"><span data-stu-id="7840e-160">It can also occur when you try to load a file from a folder linked over [Remote Desktop Services](https://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Services).</span></span> <span data-ttu-id="7840e-161">Para evitar a exceção, defina `enabled` como `true`.</span><span class="sxs-lookup"><span data-stu-id="7840e-161">To avoid the exception, set `enabled` to `true`.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="7840e-162">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="7840e-162">Configuration file</span></span>

<span data-ttu-id="7840e-163">Esse elemento é normalmente usado no arquivo de configuração do aplicativo, mas pode ser usado em outros arquivos de configuração, dependendo do contexto.</span><span class="sxs-lookup"><span data-stu-id="7840e-163">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="7840e-164">Para obter mais informações, consulte o artigo [usos mais implícitos da política de CAS: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) no blog de segurança do .net.</span><span class="sxs-lookup"><span data-stu-id="7840e-164">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) in the .NET Security blog.</span></span>  

## <a name="example"></a><span data-ttu-id="7840e-165">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7840e-165">Example</span></span>

<span data-ttu-id="7840e-166">O exemplo a seguir mostra como conceder confiança total a assemblies carregados de fontes remotas.</span><span class="sxs-lookup"><span data-stu-id="7840e-166">The following example shows how to grant full trust to assemblies loaded from remote sources.</span></span>

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a><span data-ttu-id="7840e-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7840e-167">See also</span></span>

- [<span data-ttu-id="7840e-168">Mais usos implícitos da política de CAS: loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="7840e-168">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=266839)
- [<span data-ttu-id="7840e-169">Como: Executar o código parcialmente confiável em uma área restrita</span><span class="sxs-lookup"><span data-stu-id="7840e-169">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="7840e-170">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="7840e-170">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7840e-171">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="7840e-171">Configuration File Schema</span></span>](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
