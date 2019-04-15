---
title: Configurando o redirecionamento de associações de assemblies
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5df468b87c62f454f6a42fa7a80d92e5ec199fd1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151535"
---
# <a name="configuring-assembly-binding-redirection"></a><span data-ttu-id="04d60-102">Configurando o redirecionamento de associações de assemblies</span><span class="sxs-lookup"><span data-stu-id="04d60-102">Configuring Assembly Binding Redirection</span></span>
<span data-ttu-id="04d60-103">Por padrão, os aplicativos usam o conjunto de assemblies do .NET Framework que acompanha a versão do tempo de execução usada para compilar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04d60-103">By default, applications use the set of .NET Framework assemblies that shipped with the runtime version used to compile the application.</span></span> <span data-ttu-id="04d60-104">Você pode usar o atributo **appliesTo** no elemento [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) em um arquivo de configuração de aplicativo para redirecionar referências de associação de assembly para uma versão específica de assemblies do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="04d60-104">You can use the **appliesTo** attribute on the [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element in an application configuration file to redirect assembly binding references to a specific version of the .NET Framework assemblies.</span></span> <span data-ttu-id="04d60-105">Esse atributo opcional usa um número de versão do .NET Framework para indicar a qual versão ele se aplica.</span><span class="sxs-lookup"><span data-stu-id="04d60-105">This optional attribute uses a .NET Framework version number to indicate which version it applies to.</span></span> <span data-ttu-id="04d60-106">Se nenhum atributo **appliesTo** for especificado, o elemento **\<assemblyBinding>** se aplica a todas as versões do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="04d60-106">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="04d60-107">O atributo **appliesTo** foi introduzido no.NET Framework versão 1.1; ele é ignorado pelo .NET Framework versão 1.0.</span><span class="sxs-lookup"><span data-stu-id="04d60-107">The **appliesTo** attribute was introduced in the .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="04d60-108">Isso significa que todos os elementos **\<assemblyBinding>** são aplicados ao usar o .NET Framework versão 1.0, mesmo se um atributo **appliesTo** for especificado.</span><span class="sxs-lookup"><span data-stu-id="04d60-108">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04d60-109">Use o atributo **appliesTo** para limitar o redirecionamento de associação de assembly para uma versão específica do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="04d60-109">Use the **appliesTo** attribute to limit assembly binding redirection to a specific version of the runtime.</span></span>  
  
 <span data-ttu-id="04d60-110">Por exemplo, para redirecionar a associação de assembly para um assembly do .NET Framework versão 1.0, inclua código XML a seguir no seu arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04d60-110">For example, to redirect assembly binding for a .NET Framework version 1.0 assembly, you would include the following XML code in your application configuration file.</span></span>  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 <span data-ttu-id="04d60-111">Os elementos **\<assemblyBinding>** fazem distinção conforme a ordem.</span><span class="sxs-lookup"><span data-stu-id="04d60-111">The **\<assemblyBinding>** elements are order-sensitive.</span></span> <span data-ttu-id="04d60-112">Insira as informações de redirecionamento de associação de assembly primeiramente para os assemblies do .NET Framework versão 1.0, seguido pelas informações de redirecionamento de associação de assembly para os assemblies do .NET Framework versão 1.1.</span><span class="sxs-lookup"><span data-stu-id="04d60-112">You should enter assembly binding redirection information for any .NET Framework version 1.0 assemblies first, followed by assembly binding redirection information for any .NET Framework version 1.1 assemblies.</span></span> <span data-ttu-id="04d60-113">Por fim, insira as informações de redirecionamento de associação de assembly para qualquer redirecionamento de assembly do .NET Framework que não use o atributo **appliesTo** e, portanto, se aplica a todas as versões do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="04d60-113">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="04d60-114">No caso de um conflito de redirecionamento, a primeira instrução de redirecionamento correspondente no arquivo de configuração é usada.</span><span class="sxs-lookup"><span data-stu-id="04d60-114">In case of a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>  
  
 <span data-ttu-id="04d60-115">Por exemplo, para redirecionar uma referência a um assembly do .NET Framework versão 1.0 e outra referência a um assembly do .NET Framework versão 1.1, use o padrão mostrado no pseudocódigo a seguir.</span><span class="sxs-lookup"><span data-stu-id="04d60-115">For example, to redirect one reference to a .NET Framework version 1.0 assembly and another reference to a .NET Framework version 1.1 assembly, you would use the pattern shown in the following pseudocode.</span></span>  
  
```xml  
<assemblyBinding xmlns="..." appliesTo="v1.0.3705">   
  <!-- .NET Framework version 1.0 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="..." appliesTo="v1.1.4322">   
  <!-- .NET Framework version 1.1 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="...">   
  <!-- Redirects meant for all versions of the .NET Framework. -->   
</assemblyBinding>  
```  
  
## <a name="debugging-configuration-file-errors"></a><span data-ttu-id="04d60-116">Depurando erros de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="04d60-116">Debugging Configuration File Errors</span></span>  
 <span data-ttu-id="04d60-117">O tempo de execução analisa os arquivos de configuração uma vez quando um domínio do aplicativo é criado e carrega o código para ele.</span><span class="sxs-lookup"><span data-stu-id="04d60-117">The runtime parses configuration files once when an application domain is created, and loads code into that application domain.</span></span> <span data-ttu-id="04d60-118">O Common Language Runtime trata os erros em um arquivo de configuração ignorando a entrada.</span><span class="sxs-lookup"><span data-stu-id="04d60-118">The common language runtime handles errors in a configuration file by ignoring the entry.</span></span> <span data-ttu-id="04d60-119">O tempo de execução ignorará todo o arquivo de configuração se ele contiver XML mal formado.</span><span class="sxs-lookup"><span data-stu-id="04d60-119">The runtime ignores the entire configuration file if it contains malformed XML.</span></span> <span data-ttu-id="04d60-120">Para XML inválido, apenas as seções inválidas serão ignoradas.</span><span class="sxs-lookup"><span data-stu-id="04d60-120">For invalid XML, only the invalid sections are ignored.</span></span>  
  
 <span data-ttu-id="04d60-121">É possível identificar se um arquivo de configuração está sendo usado determinando se os redirecionamentos de associação de assembly estão ocorrendo.</span><span class="sxs-lookup"><span data-stu-id="04d60-121">You can determine whether a configuration file is being used by determining whether assembly binding redirects are occurring.</span></span> <span data-ttu-id="04d60-122">Use o [Visualizador de Log de Associação de Assembly (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) para ver quais assemblies são carregados.</span><span class="sxs-lookup"><span data-stu-id="04d60-122">Use the [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) to see which assemblies are being loaded.</span></span> <span data-ttu-id="04d60-123">Para ver todas as associações de assembly, você deve definir uma entrada para **ForceLog** no registro.</span><span class="sxs-lookup"><span data-stu-id="04d60-123">To see all assembly binds, you must set an entry for **ForceLog** in the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04d60-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04d60-124">See also</span></span>

- [<span data-ttu-id="04d60-125">Como: Habilitar e desabilitar o redirecionamento automático de associação</span><span class="sxs-lookup"><span data-stu-id="04d60-125">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
