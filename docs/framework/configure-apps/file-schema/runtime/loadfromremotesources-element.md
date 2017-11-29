---
title: '&lt;loadFromRemoteSources&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
caps.latest.revision: "31"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 959073381ef936fa7c0b248419c8529deaee969f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltloadfromremotesourcesgt-element"></a><span data-ttu-id="fae14-102">&lt;loadFromRemoteSources&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="fae14-102">&lt;loadFromRemoteSources&gt; Element</span></span>
<span data-ttu-id="fae14-103">Especifica se assemblies de fontes remotas devem receber confiança total.</span><span class="sxs-lookup"><span data-stu-id="fae14-103">Specifies whether assemblies from remote sources should be granted full trust.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fae14-104">Se tiver sido direcionado a este tópico devido a uma mensagem de erro na lista de erros do projeto do Visual Studio ou um erro de compilação, consulte [como: usar um Assembly da Web no Visual Studio](http://msdn.microsoft.com/en-us/d8635b63-89a0-41aa-90f4-f351b2111070).</span><span class="sxs-lookup"><span data-stu-id="fae14-104">If you were directed to this topic because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](http://msdn.microsoft.com/en-us/d8635b63-89a0-41aa-90f4-f351b2111070).</span></span>  
  
 <span data-ttu-id="fae14-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="fae14-105">\<configuration></span></span>  
<span data-ttu-id="fae14-106">\<tempo de execução ></span><span class="sxs-lookup"><span data-stu-id="fae14-106">\<runtime></span></span>  
<span data-ttu-id="fae14-107">\<loadFromRemoteSources ></span><span class="sxs-lookup"><span data-stu-id="fae14-107">\<loadFromRemoteSources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fae14-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fae14-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fae14-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fae14-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fae14-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fae14-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fae14-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="fae14-111">Attributes</span></span>  
  
|<span data-ttu-id="fae14-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="fae14-112">Attribute</span></span>|<span data-ttu-id="fae14-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="fae14-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="fae14-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="fae14-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="fae14-115">Especifica se um assembly carregado a partir de fontes remotas deve receber confiança total.</span><span class="sxs-lookup"><span data-stu-id="fae14-115">Specifies whether an assembly that is loaded from remote sources should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="fae14-116">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="fae14-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="fae14-117">Valor</span><span class="sxs-lookup"><span data-stu-id="fae14-117">Value</span></span>|<span data-ttu-id="fae14-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="fae14-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="fae14-119">Não conceda confiança total para aplicativos de fontes remotas.</span><span class="sxs-lookup"><span data-stu-id="fae14-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="fae14-120">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="fae14-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="fae14-121">Conceder confiança total para aplicativos de fontes remotas.</span><span class="sxs-lookup"><span data-stu-id="fae14-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fae14-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fae14-122">Child Elements</span></span>  
 <span data-ttu-id="fae14-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="fae14-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fae14-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fae14-124">Parent Elements</span></span>  
  
|<span data-ttu-id="fae14-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="fae14-125">Element</span></span>|<span data-ttu-id="fae14-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="fae14-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fae14-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fae14-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="fae14-128">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="fae14-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fae14-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="fae14-129">Remarks</span></span>  
 <span data-ttu-id="fae14-130">No .NET Framework versão 3.5 e versões anteriores, se você carregar um assembly de um local remoto, o assembly será executado parcialmente confiável com um conjunto de concessão que depende da zona em que ele foi carregado.</span><span class="sxs-lookup"><span data-stu-id="fae14-130">In the .NET Framework version 3.5 and earlier versions, if you loaded an assembly from a remote location, the assembly would run partially trusted with a grant set that depended on the zone in which it was loaded.</span></span> <span data-ttu-id="fae14-131">Por exemplo, se você tiver carregado um assembly de um site, ele foi carregado na zona da Internet e concedido o conjunto de permissões de Internet.</span><span class="sxs-lookup"><span data-stu-id="fae14-131">For example, if you loaded an assembly from a website, it was loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="fae14-132">Em outras palavras, executado em uma área restrita de Internet.</span><span class="sxs-lookup"><span data-stu-id="fae14-132">In other words, it executed in an Internet sandbox.</span></span> <span data-ttu-id="fae14-133">Se você tentar executar o assembly [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] e versões posteriores, uma exceção é lançada; você deve criar explicitamente uma área restrita para o assembly (consulte [como: executar código parcialmente confiável em uma área restrita](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)), ou executá-lo em confiança total.</span><span class="sxs-lookup"><span data-stu-id="fae14-133">If you try to run that assembly in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later versions, an exception is thrown; you must either explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)), or run it in full trust.</span></span>  
  
 <span data-ttu-id="fae14-134">O `<loadFromRemoteSources>` permite que o elemento você especificar que os assemblies que executaria parcialmente confiável em versões anteriores do .NET Framework a ser executado totalmente confiáveis no [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="fae14-134">The `<loadFromRemoteSources>` element lets you specify that the assemblies that would have run partially trusted in earlier versions of the .NET Framework are to be run fully trusted in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later versions.</span></span> <span data-ttu-id="fae14-135">Por padrão, os assemblies remotos não são executados no [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] e posterior.</span><span class="sxs-lookup"><span data-stu-id="fae14-135">By default, remote assemblies do not run in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later.</span></span> <span data-ttu-id="fae14-136">Para executar um assembly remoto, você deve executá-lo como totalmente confiável ou criar uma área restrita <xref:System.AppDomain> na qual para executá-lo.</span><span class="sxs-lookup"><span data-stu-id="fae14-136">To run a remote assembly, you must either run it as fully trusted or create a sandboxed <xref:System.AppDomain> in which to run it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fae14-137">No [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], assemblies em compartilhamentos de rede local são executados em confiança total por padrão; você não precisa habilitar o `<loadFromRemoteSources>` elemento.</span><span class="sxs-lookup"><span data-stu-id="fae14-137">In the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], assemblies on local network shares are run as full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fae14-138">Se um aplicativo foi copiado da web, ele é marcado pelo Windows como sendo um aplicativo web, mesmo que ela reside no computador local.</span><span class="sxs-lookup"><span data-stu-id="fae14-138">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="fae14-139">Você pode alterar essa designação alterando as propriedades de arquivo, ou você pode usar o `<loadFromRemoteSources>` elemento conceder o conjunto completo de confiança.</span><span class="sxs-lookup"><span data-stu-id="fae14-139">You can change that designation by changing the file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="fae14-140">Como alternativa, você pode usar o <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> método para carregar um assembly local que o sistema operacional foi sinalizada como tendo sido carregado da web.</span><span class="sxs-lookup"><span data-stu-id="fae14-140">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>  
  
 <span data-ttu-id="fae14-141">O `enabled` atributo para este elemento é eficaz apenas quando a segurança de acesso ao código (CAS) está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="fae14-141">The `enabled` attribute for this element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="fae14-142">Por padrão, a política de CAS está desabilitada no [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="fae14-142">By default, CAS policy is disabled in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later versions.</span></span> <span data-ttu-id="fae14-143">Se você definir `enabled` para `true`, aplicativos remotos recebem confiança total.</span><span class="sxs-lookup"><span data-stu-id="fae14-143">If you set `enabled` to `true`, remote applications are granted full trust.</span></span>  
  
 <span data-ttu-id="fae14-144">Se `<loadFromRemoteSources>``enabled` não está definido como `true`, uma exceção é lançada sob as seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="fae14-144">If `<loadFromRemoteSources>``enabled` is not set to `true`, an exception is thrown under the following conditions:</span></span>  
  
-   <span data-ttu-id="fae14-145">O comportamento de modo seguro do domínio atual é diferente de seu comportamento no [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fae14-145">The sandboxing behavior of the current domain is different from its behavior in the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span> <span data-ttu-id="fae14-146">Isso requer a política de CAS será desabilitada e o domínio atual não deve ser em modo seguro.</span><span class="sxs-lookup"><span data-stu-id="fae14-146">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>  
  
-   <span data-ttu-id="fae14-147">O assembly que está sendo carregado não é do `MyComputer` zona.</span><span class="sxs-lookup"><span data-stu-id="fae14-147">The assembly being loaded is not from the `MyComputer` zone.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fae14-148">Você pode obter um <xref:System.IO.FileLoadException> em um aplicativo do Windows Virtual PC ao tentar carregar um arquivo de pastas vinculadas no computador host.</span><span class="sxs-lookup"><span data-stu-id="fae14-148">You may get a <xref:System.IO.FileLoadException> in a Windows Virtual PC application when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="fae14-149">Esse erro também pode ocorrer ao tentar carregar um arquivo de uma pasta vinculada por [dos serviços de área de trabalho remota](http://go.microsoft.com/fwlink/?LinkId=182775) (serviços de Terminal).</span><span class="sxs-lookup"><span data-stu-id="fae14-149">This error may also occur when you try to load a file from a folder linked over [Remote Desktop Services](http://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Services).</span></span> <span data-ttu-id="fae14-150">Para evitar a exceção, defina `enabled` para `true`.</span><span class="sxs-lookup"><span data-stu-id="fae14-150">To avoid the exception, set `enabled` to `true`.</span></span>  
  
 <span data-ttu-id="fae14-151">Definindo o `<loadFromRemoteSources>` elemento `true` impede esta exceção de que está sendo gerada.</span><span class="sxs-lookup"><span data-stu-id="fae14-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="fae14-152">Ele permite que você especifique que você não depender de common language runtime para a área restrita de assemblies carregados para a segurança e que eles possam ter permissão para executar como total confiança.</span><span class="sxs-lookup"><span data-stu-id="fae14-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute as full trust.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fae14-153">Se o assembly não deve ser executado em confiança total, não defina este elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="fae14-153">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="fae14-154">Em vez disso, crie uma área restrita <xref:System.AppDomain> no qual carregar o assembly.</span><span class="sxs-lookup"><span data-stu-id="fae14-154">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="fae14-155">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="fae14-155">Configuration File</span></span>  
 <span data-ttu-id="fae14-156">Esse elemento é normalmente usado no arquivo de configuração do aplicativo, mas pode ser usado em outros arquivos de configuração, dependendo do contexto.</span><span class="sxs-lookup"><span data-stu-id="fae14-156">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="fae14-157">Para obter mais informações, consulte o artigo [mais implícita usa da política de CAS: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) no blog de segurança do .NET.</span><span class="sxs-lookup"><span data-stu-id="fae14-157">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) in the .NET Security blog.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fae14-158">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fae14-158">Example</span></span>  
 <span data-ttu-id="fae14-159">O exemplo a seguir mostra como conceder confiança total para aplicativos de fontes remotas.</span><span class="sxs-lookup"><span data-stu-id="fae14-159">The following example shows how to grant full trust to applications from remote sources.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fae14-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fae14-160">See Also</span></span>  
 [<span data-ttu-id="fae14-161">Usa mais implícita da política de CAS: loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="fae14-161">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=266839)  
 [<span data-ttu-id="fae14-162">Como executar código parcialmente confiável em uma área restrita</span><span class="sxs-lookup"><span data-stu-id="fae14-162">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
 [<span data-ttu-id="fae14-163">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="fae14-163">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="fae14-164">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="fae14-164">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
