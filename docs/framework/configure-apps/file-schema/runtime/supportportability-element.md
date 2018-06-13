---
title: '&lt;supportPortability&gt; elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a8a454919a195a0f0c03ed6890e51b2723f64fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754100"
---
# <a name="ltsupportportabilitygt-element"></a><span data-ttu-id="9e5f0-102">&lt;supportPortability&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="9e5f0-102">&lt;supportPortability&gt; Element</span></span>
<span data-ttu-id="9e5f0-103">Especifica que um aplicativo pode fazer referência ao mesmo assembly em duas implementações diferentes do .NET Framework, desabilitando o comportamento padrão que trata os assemblies como equivalentes para fins de portabilidade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-103">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
 <span data-ttu-id="9e5f0-104">\<Configuração > elemento</span><span class="sxs-lookup"><span data-stu-id="9e5f0-104">\<configuration> Element</span></span>  
<span data-ttu-id="9e5f0-105">\<tempo de execução > elemento</span><span class="sxs-lookup"><span data-stu-id="9e5f0-105">\<runtime> Element</span></span>  
<span data-ttu-id="9e5f0-106">\<assemblyBinding > elemento</span><span class="sxs-lookup"><span data-stu-id="9e5f0-106">\<assemblyBinding> Element</span></span>  
<span data-ttu-id="9e5f0-107">\<supportPortability > elemento</span><span class="sxs-lookup"><span data-stu-id="9e5f0-107">\<supportPortability> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e5f0-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e5f0-108">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e5f0-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9e5f0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9e5f0-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e5f0-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="9e5f0-111">Attributes</span></span>  
  
|<span data-ttu-id="9e5f0-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="9e5f0-112">Attribute</span></span>|<span data-ttu-id="9e5f0-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e5f0-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9e5f0-114">PCT</span><span class="sxs-lookup"><span data-stu-id="9e5f0-114">PKT</span></span>|<span data-ttu-id="9e5f0-115">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="9e5f0-116">Especifica o token de chave pública do assembly afetado, como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-116">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="9e5f0-117">habilitado</span><span class="sxs-lookup"><span data-stu-id="9e5f0-117">enabled</span></span>|<span data-ttu-id="9e5f0-118">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="9e5f0-119">Especifica se o suporte para a portabilidade entre implementações de assembly do .NET Framework especificado deve ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-119">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9e5f0-120">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="9e5f0-120">enabled Attribute</span></span>  
  
|<span data-ttu-id="9e5f0-121">Valor</span><span class="sxs-lookup"><span data-stu-id="9e5f0-121">Value</span></span>|<span data-ttu-id="9e5f0-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e5f0-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9e5f0-123">true</span><span class="sxs-lookup"><span data-stu-id="9e5f0-123">true</span></span>|<span data-ttu-id="9e5f0-124">Habilite o suporte para a portabilidade entre implementações de assembly do .NET Framework especificado.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-124">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="9e5f0-125">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-125">This is the default.</span></span>|  
|<span data-ttu-id="9e5f0-126">false</span><span class="sxs-lookup"><span data-stu-id="9e5f0-126">false</span></span>|<span data-ttu-id="9e5f0-127">Desabilite o suporte para a portabilidade entre implementações de assembly do .NET Framework especificado.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-127">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="9e5f0-128">Isso permite que o aplicativo para que as referências a várias implementações do assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-128">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e5f0-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9e5f0-129">Child Elements</span></span>  
 <span data-ttu-id="9e5f0-130">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9e5f0-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9e5f0-131">Parent Elements</span></span>  
  
|<span data-ttu-id="9e5f0-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="9e5f0-132">Element</span></span>|<span data-ttu-id="9e5f0-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e5f0-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9e5f0-134">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9e5f0-135">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-135">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="9e5f0-136">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-136">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e5f0-137">Comentários</span><span class="sxs-lookup"><span data-stu-id="9e5f0-137">Remarks</span></span>  
 <span data-ttu-id="9e5f0-138">Começando com o [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], automaticamente é oferecido suporte para aplicativos que podem usar qualquer uma das duas implementações do .NET Framework, por exemplo uma implementação do .NET Framework ou o .NET Framework para a implementação do Silverlight.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-138">Beginning with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="9e5f0-139">As duas implementações de um determinado assembly do .NET Framework são vistas como equivalentes por do fichário de assembly.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-139">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="9e5f0-140">Em alguns cenários, esse recurso de portabilidade de aplicativo causa problemas.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-140">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="9e5f0-141">Nesses cenários, o `<supportPortability>` elemento pode ser usado para desabilitar o recurso.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-141">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
 <span data-ttu-id="9e5f0-142">Um cenário como esse é um assembly que tem a fazer referência a implementação do .NET Framework e o .NET Framework para Silverlight implementação de um assembly de referência específica.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-142">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="9e5f0-143">Por exemplo, um designer XAML gravado no Windows Presentation Foundation (WPF) talvez seja necessário fazer referência a área de trabalho do WPF implementação, para interface do usuário do designer e o subconjunto de WPF que está incluído na implementação do Silverlight.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-143">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="9e5f0-144">Por padrão, as referências separadas causam um erro do compilador, pois a associação de assembly considera os dois assemblies equivalentes.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-144">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="9e5f0-145">Este elemento desativa o comportamento padrão e permite que a compilação seja bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-145">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9e5f0-146">Para o compilador passar as informações a lógica de associação de assembly do common language runtime, você deve usar o `/appconfig` opção de compilador para especificar o local do arquivo App. config que contém este elemento.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-146">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e5f0-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e5f0-147">Example</span></span>  
 <span data-ttu-id="9e5f0-148">O exemplo a seguir permite que um aplicativo têm referências a implementação do .NET Framework e o .NET Framework para Silverlight implementação de qualquer assembly do .NET Framework que existe em ambas as implementações.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-148">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="9e5f0-149">O `/appconfig` opção de compilador deve ser usada para especificar o local do arquivo App. config.</span><span class="sxs-lookup"><span data-stu-id="9e5f0-149">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e5f0-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e5f0-150">See Also</span></span>  
 [<span data-ttu-id="9e5f0-151">/AppConfig (opções do compilador c#)</span><span class="sxs-lookup"><span data-stu-id="9e5f0-151">/appconfig (C# Compiler Options)</span></span>](http://msdn.microsoft.com/library/ee523958.aspx)  
 [<span data-ttu-id="9e5f0-152">Visão geral do .NET framework Assembly Unificação</span><span class="sxs-lookup"><span data-stu-id="9e5f0-152">.NET Framework Assembly Unification Overview</span></span>](http://msdn.microsoft.com/library/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)
