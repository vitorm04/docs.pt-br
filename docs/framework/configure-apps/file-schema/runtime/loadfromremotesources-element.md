---
title: Elemento <loadFromRemoteSources>
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7568129f30267b212737ec8aa688cf882e19bbff
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675303"
---
# <a name="loadfromremotesources-element"></a><span data-ttu-id="32a3a-102">\<loadFromRemoteSources > elemento</span><span class="sxs-lookup"><span data-stu-id="32a3a-102">\<loadFromRemoteSources> element</span></span>
<span data-ttu-id="32a3a-103">Especifica se os assemblies carregados de fontes remotas devem receber confiança total no .NET Framework 4 e posterior.</span><span class="sxs-lookup"><span data-stu-id="32a3a-103">Specifies whether assemblies loaded from remote sources should be granted full trust in .NET Framework 4 and later.</span></span>
  
> [!NOTE]
>  <span data-ttu-id="32a3a-104">Caso tenha sido direcionado para este artigo devido a uma mensagem de erro na lista de erros do projeto do Visual Studio ou um erro de compilação, consulte [como: Usar um Assembly da Web no Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="32a3a-104">If you were directed to this article because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span></span>  
  
 <span data-ttu-id="32a3a-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="32a3a-105">\<configuration></span></span>  
<span data-ttu-id="32a3a-106">\<runtime></span><span class="sxs-lookup"><span data-stu-id="32a3a-106">\<runtime></span></span>  
<span data-ttu-id="32a3a-107">\<loadFromRemoteSources></span><span class="sxs-lookup"><span data-stu-id="32a3a-107">\<loadFromRemoteSources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32a3a-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32a3a-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32a3a-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="32a3a-109">Attributes and elements</span></span>
 <span data-ttu-id="32a3a-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="32a3a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32a3a-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="32a3a-111">Attributes</span></span>  
  
|<span data-ttu-id="32a3a-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="32a3a-112">Attribute</span></span>|<span data-ttu-id="32a3a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="32a3a-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="32a3a-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="32a3a-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="32a3a-115">Especifica se um assembly que é carregado de uma fonte remota deve receber confiança total.</span><span class="sxs-lookup"><span data-stu-id="32a3a-115">Specifies whether an assembly that is loaded from a remote source should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="32a3a-116">atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="32a3a-116">enabled attribute</span></span>  
  
|<span data-ttu-id="32a3a-117">Valor</span><span class="sxs-lookup"><span data-stu-id="32a3a-117">Value</span></span>|<span data-ttu-id="32a3a-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="32a3a-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="32a3a-119">Não conceda confiança total para aplicativos de fontes remotas.</span><span class="sxs-lookup"><span data-stu-id="32a3a-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="32a3a-120">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="32a3a-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="32a3a-121">Conceder confiança total para aplicativos de fontes remotas.</span><span class="sxs-lookup"><span data-stu-id="32a3a-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32a3a-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="32a3a-122">Child elements</span></span>  
 <span data-ttu-id="32a3a-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="32a3a-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="32a3a-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="32a3a-124">Parent elements</span></span>  
  
|<span data-ttu-id="32a3a-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="32a3a-125">Element</span></span>|<span data-ttu-id="32a3a-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="32a3a-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="32a3a-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="32a3a-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="32a3a-128">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="32a3a-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32a3a-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="32a3a-129">Remarks</span></span>

<span data-ttu-id="32a3a-130">No .NET Framework 3.5 e versões anteriores, se você carregar um assembly de um local remoto, o código no assembly é executado em confiança parcial com um conjunto de concessões que depende da zona da qual ele é carregado.</span><span class="sxs-lookup"><span data-stu-id="32a3a-130">In the .NET Framework 3.5 and earlier versions, if you load an assembly from a remote location, code in the assembly runs in partial trust with a grant set that depends on the zone from which it is loaded.</span></span> <span data-ttu-id="32a3a-131">Por exemplo, se você carregar um assembly de um site, ele é carregado na zona da Internet e concedeu o conjunto de permissões de Internet.</span><span class="sxs-lookup"><span data-stu-id="32a3a-131">For example, if you load an assembly from a website, it is loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="32a3a-132">Em outras palavras, ele executa em uma área de segurança de Internet.</span><span class="sxs-lookup"><span data-stu-id="32a3a-132">In other words, it executes in an Internet sandbox.</span></span>

<span data-ttu-id="32a3a-133">Começando com o .NET Framework 4, a política de CAS (segurança) de acesso do código está desabilitada e os assemblies são carregados em confiança total.</span><span class="sxs-lookup"><span data-stu-id="32a3a-133">Starting with the .NET Framework 4, code access security (CAS) policy is disabled and assemblies are loaded in full trust.</span></span> <span data-ttu-id="32a3a-134">Normalmente, isso seria conceder confiança total para os assemblies carregados com o <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> método que anteriormente havia sido em área restrita.</span><span class="sxs-lookup"><span data-stu-id="32a3a-134">Ordinarily, this would grant full trust to assemblies loaded with the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method that previously had been sandboxed.</span></span> <span data-ttu-id="32a3a-135">Para evitar isso, a capacidade de executar o código em assemblies carregados de uma fonte remota está desabilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="32a3a-135">To prevent this, the ability to run code in assemblies loaded from a remote source is disabled by default.</span></span> <span data-ttu-id="32a3a-136">Por padrão, se você tentar carregar um assembly remoto, um <xref:System.IO.FileLoadException> com uma mensagem de exceção, como o seguinte é gerado:</span><span class="sxs-lookup"><span data-stu-id="32a3a-136">By default, if you attempt to load a remote assembly, a <xref:System.IO.FileLoadException> with an exception message like the following is thrown:</span></span>

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported. 
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' ---> 
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly 
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default, 
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch. 
```

<span data-ttu-id="32a3a-137">Para carregar o assembly e executar seu código, você deve:</span><span class="sxs-lookup"><span data-stu-id="32a3a-137">To load the assembly and execute its code, you must either:</span></span>

- <span data-ttu-id="32a3a-138">Criar explicitamente uma área restrita para o assembly (consulte [como: Executar código parcialmente confiável em uma área restrita](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span><span class="sxs-lookup"><span data-stu-id="32a3a-138">Explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span></span>

- <span data-ttu-id="32a3a-139">Execute o código do assembly em confiança total.</span><span class="sxs-lookup"><span data-stu-id="32a3a-139">Run the assembly's code in full trust.</span></span> <span data-ttu-id="32a3a-140">Você pode fazer isso configurando a `<loadFromRemoteSources>` elemento.</span><span class="sxs-lookup"><span data-stu-id="32a3a-140">You do this by configuring the `<loadFromRemoteSources>` element.</span></span> <span data-ttu-id="32a3a-141">Ele permite que você especifique os assemblies que são executados em confiança parcial em versões anteriores do .NET Framework agora executar em confiança total no .NET Framework 4 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="32a3a-141">It lets you specify that the assemblies that run in partial trust in earlier versions of the .NET Framework now run in full trust in the .NET Framework 4 and later versions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="32a3a-142">Se o assembly não deve ser executado em confiança total, não defina este elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="32a3a-142">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="32a3a-143">Em vez disso, crie uma área restrita e <xref:System.AppDomain> no qual carregar o assembly.</span><span class="sxs-lookup"><span data-stu-id="32a3a-143">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>

<span data-ttu-id="32a3a-144">O `enabled` de atributo para o `<loadFromRemoteSources>` elemento é eficaz apenas quando a segurança de acesso do código (CAS) está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="32a3a-144">The `enabled` attribute for the `<loadFromRemoteSources>` element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="32a3a-145">Por padrão, a política de CAS está desabilitada no .NET Framework 4 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="32a3a-145">By default, CAS policy is disabled in the .NET Framework 4 and later versions.</span></span> <span data-ttu-id="32a3a-146">Se você definir `enabled` para `true`, assemblies remotos recebem confiança total.</span><span class="sxs-lookup"><span data-stu-id="32a3a-146">If you set `enabled` to `true`, remote assemblies are granted full trust.</span></span>

<span data-ttu-id="32a3a-147">Se `enabled` não está definido como `true`, um <xref:System.IO.FileLoadException> é lançada sob a qualquer uma das seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="32a3a-147">If `enabled` is not set to `true`, a <xref:System.IO.FileLoadException> is thrown under the either of the following conditions:</span></span>

- <span data-ttu-id="32a3a-148">O comportamento de modo seguro do domínio atual é diferente de seu comportamento no .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="32a3a-148">The sandboxing behavior of the current domain is different from its behavior in the .NET Framework 3.5.</span></span> <span data-ttu-id="32a3a-149">Isso requer a política de CAS seja desabilitado e o domínio atual não devem ser em área restrita.</span><span class="sxs-lookup"><span data-stu-id="32a3a-149">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>

- <span data-ttu-id="32a3a-150">O assembly que está sendo carregado não é do `MyComputer` zona.</span><span class="sxs-lookup"><span data-stu-id="32a3a-150">The assembly being loaded is not from the `MyComputer` zone.</span></span>

<span data-ttu-id="32a3a-151">Definindo o `<loadFromRemoteSources>` elemento para `true` impede essa exceção de que está sendo gerada.</span><span class="sxs-lookup"><span data-stu-id="32a3a-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="32a3a-152">Ele permite que você especifique que você não depender do common language runtime para a área restrita os assemblies carregados para a segurança e que pode ser permitidos para execução no total confiança.</span><span class="sxs-lookup"><span data-stu-id="32a3a-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute in full trust.</span></span>

## <a name="notes"></a><span data-ttu-id="32a3a-153">Observações</span><span class="sxs-lookup"><span data-stu-id="32a3a-153">Notes</span></span>

- <span data-ttu-id="32a3a-154">No .NET Framework 4.5 e versões posteriores, os assemblies em compartilhamentos de rede local são executados em confiança total por padrão. Você não precisa habilitar o `<loadFromRemoteSources>` elemento.</span><span class="sxs-lookup"><span data-stu-id="32a3a-154">In the .NET Framework 4.5 and later versions, assemblies on local network shares run in full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>

- <span data-ttu-id="32a3a-155">Se um aplicativo tiver sido copiado da web, ele será sinalizado pelo Windows como sendo um aplicativo web, mesmo que ele reside no computador local.</span><span class="sxs-lookup"><span data-stu-id="32a3a-155">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="32a3a-156">Você pode alterar essa designação alterando suas propriedades de arquivo, ou você pode usar o `<loadFromRemoteSources>` confiança total do elemento para conceder o conjunto.</span><span class="sxs-lookup"><span data-stu-id="32a3a-156">You can change that designation by changing its file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="32a3a-157">Como alternativa, você pode usar o <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> método para carregar um assembly local que o sistema operacional foi sinalizada como tendo sido carregados da web.</span><span class="sxs-lookup"><span data-stu-id="32a3a-157">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>

- <span data-ttu-id="32a3a-158">Você pode obter um <xref:System.IO.FileLoadException> em um aplicativo que está em execução em um aplicativo do Windows Virtual PC.</span><span class="sxs-lookup"><span data-stu-id="32a3a-158">You may get a <xref:System.IO.FileLoadException> in an application that is running in a Windows Virtual PC application.</span></span> <span data-ttu-id="32a3a-159">Isso pode acontecer quando você tenta carregar um arquivo de pastas vinculadas no computador de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="32a3a-159">This can happen when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="32a3a-160">Ele também pode ocorrer quando você tenta carregar um arquivo de uma pasta vinculada ao longo [Remote Desktop Services](https://go.microsoft.com/fwlink/?LinkId=182775) (serviços de Terminal).</span><span class="sxs-lookup"><span data-stu-id="32a3a-160">It can also occur when you try to load a file from a folder linked over [Remote Desktop Services](https://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Services).</span></span> <span data-ttu-id="32a3a-161">Para evitar a exceção, defina `enabled` para `true`.</span><span class="sxs-lookup"><span data-stu-id="32a3a-161">To avoid the exception, set `enabled` to `true`.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="32a3a-162">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="32a3a-162">Configuration file</span></span>

<span data-ttu-id="32a3a-163">Esse elemento é normalmente usado no arquivo de configuração do aplicativo, mas pode ser usado em outros arquivos de configuração, dependendo do contexto.</span><span class="sxs-lookup"><span data-stu-id="32a3a-163">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="32a3a-164">Para obter mais informações, consulte o artigo [mais implícita usa da política de CAS: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) no blog de segurança do .NET.</span><span class="sxs-lookup"><span data-stu-id="32a3a-164">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) in the .NET Security blog.</span></span>  

## <a name="example"></a><span data-ttu-id="32a3a-165">Exemplo</span><span class="sxs-lookup"><span data-stu-id="32a3a-165">Example</span></span>

<span data-ttu-id="32a3a-166">O exemplo a seguir mostra como conceder confiança total para os assemblies carregados de fontes remotas.</span><span class="sxs-lookup"><span data-stu-id="32a3a-166">The following example shows how to grant full trust to assemblies loaded from remote sources.</span></span>

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a><span data-ttu-id="32a3a-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32a3a-167">See also</span></span>

- [<span data-ttu-id="32a3a-168">Usos mais implícitos da política de CAS: loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="32a3a-168">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=266839)
- [<span data-ttu-id="32a3a-169">Como: Executar o código parcialmente confiável em uma área restrita</span><span class="sxs-lookup"><span data-stu-id="32a3a-169">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="32a3a-170">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="32a3a-170">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="32a3a-171">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="32a3a-171">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
