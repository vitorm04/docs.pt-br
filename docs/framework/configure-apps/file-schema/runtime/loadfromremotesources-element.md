---
title: Elemento <loadFromRemoteSources>
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
ms.openlocfilehash: a0dcffe378cdd09de0fbd8f0a6ef0635c033fd9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154056"
---
# <a name="loadfromremotesources-element"></a><span data-ttu-id="0ca3c-102">\<carregarDeelemento>Defontes remotas</span><span class="sxs-lookup"><span data-stu-id="0ca3c-102">\<loadFromRemoteSources> element</span></span>
<span data-ttu-id="0ca3c-103">Especifica se os conjuntos carregados de fontes remotas devem ser concedidos total confiança no Quadro .NET 4 e posterior.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-103">Specifies whether assemblies loaded from remote sources should be granted full trust in .NET Framework 4 and later.</span></span>
  
> [!NOTE]
> <span data-ttu-id="0ca3c-104">Se você foi direcionado a este artigo por causa de uma mensagem de erro na lista de erros do projeto Visual Studio ou de um erro de compilação, consulte [Como: Usar um conjunto da Web no Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0ca3c-104">If you were directed to this article because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span></span>  
  
<span data-ttu-id="0ca3c-105">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0ca3c-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0ca3c-106">&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="0ca3c-106">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="0ca3c-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<carregamentoDeDeFormaremotas>**</span><span class="sxs-lookup"><span data-stu-id="0ca3c-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<loadFromRemoteSources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ca3c-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0ca3c-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ca3c-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0ca3c-109">Attributes and elements</span></span>
 <span data-ttu-id="0ca3c-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ca3c-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="0ca3c-111">Attributes</span></span>  
  
|<span data-ttu-id="0ca3c-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="0ca3c-112">Attribute</span></span>|<span data-ttu-id="0ca3c-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ca3c-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="0ca3c-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="0ca3c-115">Especifica se um conjunto carregado de uma fonte remota deve ser concedido total confiança.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-115">Specifies whether an assembly that is loaded from a remote source should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0ca3c-116">atributo ativado</span><span class="sxs-lookup"><span data-stu-id="0ca3c-116">enabled attribute</span></span>  
  
|<span data-ttu-id="0ca3c-117">Valor</span><span class="sxs-lookup"><span data-stu-id="0ca3c-117">Value</span></span>|<span data-ttu-id="0ca3c-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ca3c-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="0ca3c-119">Não conceda total confiança a aplicações de fontes remotas.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="0ca3c-120">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="0ca3c-121">Conceda total confiança a aplicações de fontes remotas.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ca3c-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0ca3c-122">Child elements</span></span>  
 <span data-ttu-id="0ca3c-123">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0ca3c-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0ca3c-124">Parent elements</span></span>  
  
|<span data-ttu-id="0ca3c-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="0ca3c-125">Element</span></span>|<span data-ttu-id="0ca3c-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ca3c-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0ca3c-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0ca3c-128">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ca3c-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="0ca3c-129">Remarks</span></span>

<span data-ttu-id="0ca3c-130">Nas versões .NET Framework 3.5 e anteriores, se você carregar um conjunto de um local remoto, o código no conjunto será executado em confiança parcial com um conjunto de concessões que depende da região da qual ele é carregado.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-130">In the .NET Framework 3.5 and earlier versions, if you load an assembly from a remote location, code in the assembly runs in partial trust with a grant set that depends on the zone from which it is loaded.</span></span> <span data-ttu-id="0ca3c-131">Por exemplo, se você carregar um conjunto de um site, ele é carregado na região da Internet e concedido o conjunto de permissões da Internet.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-131">For example, if you load an assembly from a website, it is loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="0ca3c-132">Em outras palavras, ele é executado em uma caixa de areia da Internet.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-132">In other words, it executes in an Internet sandbox.</span></span>

<span data-ttu-id="0ca3c-133">Começando com o .NET Framework 4, a política CAS (Code Access Security, segurança de acesso ao código) é desativada e as montagens são carregadas em total confiança.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-133">Starting with the .NET Framework 4, code access security (CAS) policy is disabled and assemblies are loaded in full trust.</span></span> <span data-ttu-id="0ca3c-134">Normalmente, isso concederia total confiança às <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> assembléias carregadas com o método que anteriormente havia sido sandboxed.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-134">Ordinarily, this would grant full trust to assemblies loaded with the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method that previously had been sandboxed.</span></span> <span data-ttu-id="0ca3c-135">Para evitar isso, a capacidade de executar código em conjuntos carregados de uma fonte remota é desativada por padrão.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-135">To prevent this, the ability to run code in assemblies loaded from a remote source is disabled by default.</span></span> <span data-ttu-id="0ca3c-136">Por padrão, se você tentar carregar <xref:System.IO.FileLoadException> um conjunto remoto, uma mensagem com exceção como a seguinte será lançada:</span><span class="sxs-lookup"><span data-stu-id="0ca3c-136">By default, if you attempt to load a remote assembly, a <xref:System.IO.FileLoadException> with an exception message like the following is thrown:</span></span>

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported.
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' --->
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default,
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch.
```

<span data-ttu-id="0ca3c-137">Para carregar o conjunto e executar seu código, você deve:</span><span class="sxs-lookup"><span data-stu-id="0ca3c-137">To load the assembly and execute its code, you must either:</span></span>

- <span data-ttu-id="0ca3c-138">Crie explicitamente uma caixa de areia para o conjunto (veja [Como: Executar código parcialmente confiável em uma caixa de areia](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span><span class="sxs-lookup"><span data-stu-id="0ca3c-138">Explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span></span>

- <span data-ttu-id="0ca3c-139">Execute o código da assembléia em total confiança.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-139">Run the assembly's code in full trust.</span></span> <span data-ttu-id="0ca3c-140">Você faz isso configurando o `<loadFromRemoteSources>` elemento.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-140">You do this by configuring the `<loadFromRemoteSources>` element.</span></span> <span data-ttu-id="0ca3c-141">Ele permite especificar que as assembléias que são executadas em confiança parcial em versões anteriores do .NET Framework agora são executadas em total confiança nas versões .NET Framework 4 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-141">It lets you specify that the assemblies that run in partial trust in earlier versions of the .NET Framework now run in full trust in the .NET Framework 4 and later versions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0ca3c-142">Se o conjunto não for executado em plena confiança, não defina este elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-142">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="0ca3c-143">Em vez disso, crie <xref:System.AppDomain> uma caixa de areia na qual para carregar o conjunto.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-143">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>

<span data-ttu-id="0ca3c-144">O `enabled` atributo `<loadFromRemoteSources>` para o elemento só é eficaz quando o CAS (Code Access Security, segurança de acesso ao código) é desativado.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-144">The `enabled` attribute for the `<loadFromRemoteSources>` element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="0ca3c-145">Por padrão, a diretiva CAS é desativada nas versões .NET Framework 4 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-145">By default, CAS policy is disabled in the .NET Framework 4 and later versions.</span></span> <span data-ttu-id="0ca3c-146">Se você `enabled` `true`definir para , assembléias remotas são concedidas total confiança.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-146">If you set `enabled` to `true`, remote assemblies are granted full trust.</span></span>

<span data-ttu-id="0ca3c-147">Se `enabled` não for `true`definido <xref:System.IO.FileLoadException> para, a é jogado qualquer uma das seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="0ca3c-147">If `enabled` is not set to `true`, a <xref:System.IO.FileLoadException> is thrown under the either of the following conditions:</span></span>

- <span data-ttu-id="0ca3c-148">O comportamento de sandboxing do domínio atual é diferente de seu comportamento no Quadro .NET 3.5.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-148">The sandboxing behavior of the current domain is different from its behavior in the .NET Framework 3.5.</span></span> <span data-ttu-id="0ca3c-149">Isso exige que a política CAS seja desativada e que o domínio atual não seja sandbox.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-149">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>

- <span data-ttu-id="0ca3c-150">A montagem que está sendo `MyComputer` carregada não é da zona.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-150">The assembly being loaded is not from the `MyComputer` zone.</span></span>

<span data-ttu-id="0ca3c-151">Definir `<loadFromRemoteSources>` o `true` elemento para evitar que essa exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="0ca3c-152">Ele permite que você especifique que você não está confiando no tempo de execução do idioma comum para sandbox os conjuntos carregados para segurança, e que eles podem ser autorizados a executar em total confiança.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute in full trust.</span></span>

## <a name="notes"></a><span data-ttu-id="0ca3c-153">Observações</span><span class="sxs-lookup"><span data-stu-id="0ca3c-153">Notes</span></span>

- <span data-ttu-id="0ca3c-154">Nas versões .NET Framework 4.5 e posteriores, as assembléias sobre ações de rede locais são executadas em total confiança por padrão; você não precisa ativar `<loadFromRemoteSources>` o elemento.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-154">In the .NET Framework 4.5 and later versions, assemblies on local network shares run in full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>

- <span data-ttu-id="0ca3c-155">Se um aplicativo foi copiado da web, ele é sinalizado pelo Windows como sendo um aplicativo web, mesmo que resida no computador local.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-155">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="0ca3c-156">Você pode alterar essa designação alterando suas `<loadFromRemoteSources>` propriedades de arquivo, ou você pode usar o elemento para conceder a total confiança da assembléia.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-156">You can change that designation by changing its file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="0ca3c-157">Como alternativa, você pode <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> usar o método para carregar um conjunto local que o sistema operacional sinalizou como tendo sido carregado da web.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-157">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>

- <span data-ttu-id="0ca3c-158">Você pode <xref:System.IO.FileLoadException> obter um em um aplicativo que está sendo executado em um aplicativo de PC virtual do Windows.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-158">You may get a <xref:System.IO.FileLoadException> in an application that is running in a Windows Virtual PC application.</span></span> <span data-ttu-id="0ca3c-159">Isso pode acontecer quando você tenta carregar um arquivo de pastas vinculadas no computador de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-159">This can happen when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="0ca3c-160">Também pode ocorrer quando você tenta carregar um arquivo de uma pasta vinculada sobre [serviços de área de trabalho remota](/windows/win32/termserv/terminal-services-portal) (Serviços de Terminal).</span><span class="sxs-lookup"><span data-stu-id="0ca3c-160">It can also occur when you try to load a file from a folder linked over [Remote Desktop Services](/windows/win32/termserv/terminal-services-portal) (Terminal Services).</span></span> <span data-ttu-id="0ca3c-161">Para evitar a `enabled` exceção, definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-161">To avoid the exception, set `enabled` to `true`.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="0ca3c-162">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="0ca3c-162">Configuration file</span></span>

<span data-ttu-id="0ca3c-163">Esse elemento é normalmente usado no arquivo de configuração do aplicativo, mas pode ser usado em outros arquivos de configuração, dependendo do contexto.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-163">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="0ca3c-164">Para obter mais informações, consulte o artigo [Usos mais implícitos da política CAS: loadFromRemoteSources](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources) no blog .NET Security.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-164">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources) in the .NET Security blog.</span></span>  

## <a name="example"></a><span data-ttu-id="0ca3c-165">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ca3c-165">Example</span></span>

<span data-ttu-id="0ca3c-166">O exemplo a seguir mostra como conceder confiança total a assembléias carregadas de fontes remotas.</span><span class="sxs-lookup"><span data-stu-id="0ca3c-166">The following example shows how to grant full trust to assemblies loaded from remote sources.</span></span>

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a><span data-ttu-id="0ca3c-167">Confira também</span><span class="sxs-lookup"><span data-stu-id="0ca3c-167">See also</span></span>

- [<span data-ttu-id="0ca3c-168">Usos mais implícitos da política CAS: loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="0ca3c-168">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources)
- [<span data-ttu-id="0ca3c-169">Como executar código parcialmente confiável em uma área restrita</span><span class="sxs-lookup"><span data-stu-id="0ca3c-169">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="0ca3c-170">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="0ca3c-170">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0ca3c-171">Esquema de arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="0ca3c-171">Configuration File Schema</span></span>](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
