---
title: Elemento <supportPortability>
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 011793006f2aff32486fbe4537b46517e0a2b888
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252299"
---
# <a name="supportportability-element"></a><span data-ttu-id="518ee-102">\<Elemento de > supportPortability</span><span class="sxs-lookup"><span data-stu-id="518ee-102">\<supportPortability> Element</span></span>
<span data-ttu-id="518ee-103">Especifica que um aplicativo pode fazer referência ao mesmo assembly em duas implementações diferentes do .NET Framework, desabilitando o comportamento padrão que trata os assemblies como equivalentes para fins de portabilidade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="518ee-103">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
<span data-ttu-id="518ee-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="518ee-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="518ee-105">&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="518ee-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="518ee-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> assemblyBinding**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="518ee-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="518ee-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> supportPortability**</span><span class="sxs-lookup"><span data-stu-id="518ee-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<supportPortability>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="518ee-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="518ee-108">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="518ee-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="518ee-109">Attributes and Elements</span></span>  

<span data-ttu-id="518ee-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="518ee-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="518ee-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="518ee-111">Attributes</span></span>  
  
|<span data-ttu-id="518ee-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="518ee-112">Attribute</span></span>|<span data-ttu-id="518ee-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="518ee-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="518ee-114">PCT</span><span class="sxs-lookup"><span data-stu-id="518ee-114">PKT</span></span>|<span data-ttu-id="518ee-115">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="518ee-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="518ee-116">Especifica o token de chave pública do assembly afetado, como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="518ee-116">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="518ee-117">habilitado</span><span class="sxs-lookup"><span data-stu-id="518ee-117">enabled</span></span>|<span data-ttu-id="518ee-118">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="518ee-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="518ee-119">Especifica se o suporte para portabilidade entre as implementações do assembly de .NET Framework especificado deve ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="518ee-119">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="518ee-120">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="518ee-120">enabled Attribute</span></span>  
  
|<span data-ttu-id="518ee-121">Valor</span><span class="sxs-lookup"><span data-stu-id="518ee-121">Value</span></span>|<span data-ttu-id="518ee-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="518ee-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="518ee-123">true</span><span class="sxs-lookup"><span data-stu-id="518ee-123">true</span></span>|<span data-ttu-id="518ee-124">Habilite o suporte para portabilidade entre implementações do assembly de .NET Framework especificado.</span><span class="sxs-lookup"><span data-stu-id="518ee-124">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="518ee-125">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="518ee-125">This is the default.</span></span>|  
|<span data-ttu-id="518ee-126">false</span><span class="sxs-lookup"><span data-stu-id="518ee-126">false</span></span>|<span data-ttu-id="518ee-127">Desabilite o suporte para portabilidade entre implementações do assembly de .NET Framework especificado.</span><span class="sxs-lookup"><span data-stu-id="518ee-127">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="518ee-128">Isso permite que o aplicativo tenha referências a várias implementações do assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="518ee-128">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="518ee-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="518ee-129">Child Elements</span></span>  

<span data-ttu-id="518ee-130">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="518ee-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="518ee-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="518ee-131">Parent Elements</span></span>  
  
|<span data-ttu-id="518ee-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="518ee-132">Element</span></span>|<span data-ttu-id="518ee-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="518ee-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="518ee-134">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="518ee-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="518ee-135">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="518ee-135">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="518ee-136">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="518ee-136">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="518ee-137">Comentários</span><span class="sxs-lookup"><span data-stu-id="518ee-137">Remarks</span></span>  

<span data-ttu-id="518ee-138">A partir do .NET Framework 4, o suporte é fornecido automaticamente para aplicativos que podem usar uma das duas implementações do .NET Framework, por exemplo, a implementação do .NET Framework ou o .NET Framework para a implementação do Silverlight.</span><span class="sxs-lookup"><span data-stu-id="518ee-138">Beginning with the .NET Framework 4, support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="518ee-139">As duas implementações de um determinado assembly de .NET Framework são vistas como equivalentes pelo associador de assembly.</span><span class="sxs-lookup"><span data-stu-id="518ee-139">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="518ee-140">Em alguns cenários, esse recurso de portabilidade de aplicativo causa problemas.</span><span class="sxs-lookup"><span data-stu-id="518ee-140">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="518ee-141">Nesses cenários, o `<supportPortability>` elemento pode ser usado para desabilitar o recurso.</span><span class="sxs-lookup"><span data-stu-id="518ee-141">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
<span data-ttu-id="518ee-142">Um cenário desse tipo é um assembly que tem que referenciar a implementação de .NET Framework e o .NET Framework para a implementação do Silverlight de um determinado assembly de referência.</span><span class="sxs-lookup"><span data-stu-id="518ee-142">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="518ee-143">Por exemplo, um designer XAML escrito em Windows Presentation Foundation (WPF) pode precisar referenciar a implementação da área de trabalho do WPF, para a interface do usuário do designer e o subconjunto do WPF que está incluído na implementação do Silverlight.</span><span class="sxs-lookup"><span data-stu-id="518ee-143">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="518ee-144">Por padrão, as referências separadas causam um erro do compilador, pois a associação de assembly considera os dois assemblies equivalentes.</span><span class="sxs-lookup"><span data-stu-id="518ee-144">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="518ee-145">Esse elemento desabilita o comportamento padrão e permite que a compilação tenha sucesso.</span><span class="sxs-lookup"><span data-stu-id="518ee-145">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="518ee-146">Para que o compilador passe as informações para a lógica de associação de assembly do Common Language Runtime, você deve usar a opção `/appconfig` do compilador para especificar o local do arquivo app. config que contém esse elemento.</span><span class="sxs-lookup"><span data-stu-id="518ee-146">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="518ee-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="518ee-147">Example</span></span>  

<span data-ttu-id="518ee-148">O exemplo a seguir permite que um aplicativo tenha referências para a implementação de .NET Framework e o .NET Framework para a implementação do Silverlight de qualquer assembly .NET Framework que exista em ambas as implementações.</span><span class="sxs-lookup"><span data-stu-id="518ee-148">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="518ee-149">A `/appconfig` opção do compilador deve ser usada para especificar o local deste arquivo app. config.</span><span class="sxs-lookup"><span data-stu-id="518ee-149">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="518ee-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="518ee-150">See also</span></span>

- [<span data-ttu-id="518ee-151">/AppConfig (C# opções do compilador)</span><span class="sxs-lookup"><span data-stu-id="518ee-151">/appconfig (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- <span data-ttu-id="518ee-152">[Visão geral da unificação do assembly .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="518ee-152">[.NET Framework Assembly Unification Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span></span>
