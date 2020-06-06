---
title: Elemento <supportPortability>
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
ms.openlocfilehash: 63c309a8a93c1d31ed8f73a495cf5154c3590d56
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115650"
---
# <a name="supportportability-element"></a><span data-ttu-id="84a28-102">Elemento \<supportPortability></span><span class="sxs-lookup"><span data-stu-id="84a28-102">\<supportPortability> Element</span></span>
<span data-ttu-id="84a28-103">Especifica que um aplicativo pode fazer referência ao mesmo assembly em duas implementações diferentes do .NET Framework, desabilitando o comportamento padrão que trata os assemblies como equivalentes para fins de portabilidade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="84a28-103">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<supportPortability>**  
  
## <a name="syntax"></a><span data-ttu-id="84a28-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84a28-104">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84a28-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="84a28-105">Attributes and Elements</span></span>  

<span data-ttu-id="84a28-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="84a28-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84a28-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="84a28-107">Attributes</span></span>  
  
|<span data-ttu-id="84a28-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="84a28-108">Attribute</span></span>|<span data-ttu-id="84a28-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="84a28-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="84a28-110">PCT</span><span class="sxs-lookup"><span data-stu-id="84a28-110">PKT</span></span>|<span data-ttu-id="84a28-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="84a28-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="84a28-112">Especifica o token de chave pública do assembly afetado, como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="84a28-112">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="84a28-113">Habilitado</span><span class="sxs-lookup"><span data-stu-id="84a28-113">enabled</span></span>|<span data-ttu-id="84a28-114">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="84a28-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="84a28-115">Especifica se o suporte para portabilidade entre as implementações do assembly de .NET Framework especificado deve ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="84a28-115">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="84a28-116">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="84a28-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="84a28-117">Valor</span><span class="sxs-lookup"><span data-stu-id="84a28-117">Value</span></span>|<span data-ttu-id="84a28-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="84a28-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="84a28-119">true</span><span class="sxs-lookup"><span data-stu-id="84a28-119">true</span></span>|<span data-ttu-id="84a28-120">Habilite o suporte para portabilidade entre implementações do assembly de .NET Framework especificado.</span><span class="sxs-lookup"><span data-stu-id="84a28-120">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="84a28-121">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="84a28-121">This is the default.</span></span>|  
|<span data-ttu-id="84a28-122">false</span><span class="sxs-lookup"><span data-stu-id="84a28-122">false</span></span>|<span data-ttu-id="84a28-123">Desabilite o suporte para portabilidade entre implementações do assembly de .NET Framework especificado.</span><span class="sxs-lookup"><span data-stu-id="84a28-123">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="84a28-124">Isso permite que o aplicativo tenha referências a várias implementações do assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="84a28-124">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84a28-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="84a28-125">Child Elements</span></span>  

<span data-ttu-id="84a28-126">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="84a28-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="84a28-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="84a28-127">Parent Elements</span></span>  
  
|<span data-ttu-id="84a28-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="84a28-128">Element</span></span>|<span data-ttu-id="84a28-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="84a28-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="84a28-130">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="84a28-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="84a28-131">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="84a28-131">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="84a28-132">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="84a28-132">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84a28-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="84a28-133">Remarks</span></span>  

<span data-ttu-id="84a28-134">A partir do .NET Framework 4, o suporte é fornecido automaticamente para aplicativos que podem usar uma das duas implementações do .NET Framework, por exemplo, a implementação do .NET Framework ou o .NET Framework para a implementação do Silverlight.</span><span class="sxs-lookup"><span data-stu-id="84a28-134">Beginning with the .NET Framework 4, support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="84a28-135">As duas implementações de um determinado assembly de .NET Framework são vistas como equivalentes pelo associador de assembly.</span><span class="sxs-lookup"><span data-stu-id="84a28-135">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="84a28-136">Em alguns cenários, esse recurso de portabilidade de aplicativo causa problemas.</span><span class="sxs-lookup"><span data-stu-id="84a28-136">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="84a28-137">Nesses cenários, o `<supportPortability>` elemento pode ser usado para desabilitar o recurso.</span><span class="sxs-lookup"><span data-stu-id="84a28-137">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
<span data-ttu-id="84a28-138">Um cenário desse tipo é um assembly que tem que referenciar a implementação de .NET Framework e o .NET Framework para a implementação do Silverlight de um determinado assembly de referência.</span><span class="sxs-lookup"><span data-stu-id="84a28-138">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="84a28-139">Por exemplo, um designer XAML escrito em Windows Presentation Foundation (WPF) pode precisar referenciar a implementação da área de trabalho do WPF, para a interface do usuário do designer e o subconjunto do WPF que está incluído na implementação do Silverlight.</span><span class="sxs-lookup"><span data-stu-id="84a28-139">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="84a28-140">Por padrão, as referências separadas causam um erro do compilador, pois a associação de assembly considera os dois assemblies equivalentes.</span><span class="sxs-lookup"><span data-stu-id="84a28-140">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="84a28-141">Esse elemento desabilita o comportamento padrão e permite que a compilação tenha sucesso.</span><span class="sxs-lookup"><span data-stu-id="84a28-141">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="84a28-142">Para que o compilador passe as informações para a lógica de associação de assembly do Common Language Runtime, você deve usar a `/appconfig` opção do compilador para especificar o local do arquivo app. config que contém esse elemento.</span><span class="sxs-lookup"><span data-stu-id="84a28-142">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84a28-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="84a28-143">Example</span></span>  

<span data-ttu-id="84a28-144">O exemplo a seguir permite que um aplicativo tenha referências para a implementação de .NET Framework e o .NET Framework para a implementação do Silverlight de qualquer assembly .NET Framework que exista em ambas as implementações.</span><span class="sxs-lookup"><span data-stu-id="84a28-144">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="84a28-145">A `/appconfig` opção do compilador deve ser usada para especificar o local deste arquivo app. config.</span><span class="sxs-lookup"><span data-stu-id="84a28-145">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="84a28-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="84a28-146">See also</span></span>

- [<span data-ttu-id="84a28-147">-AppConfig (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="84a28-147">-appconfig (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- <span data-ttu-id="84a28-148">[Visão Geral da Unificação de Assemblies no .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="84a28-148">[.NET Framework Assembly Unification Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span></span>
