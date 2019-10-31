---
title: <Library> (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
ms.openlocfilehash: f94bfe047fa7a95b6f24264bae0b27112c589dfd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128362"
---
# <a name="library-element-net-native"></a><span data-ttu-id="5ae48-102">Elemento de > de biblioteca de \<(.NET Native)</span><span class="sxs-lookup"><span data-stu-id="5ae48-102">\<Library> Element (.NET Native)</span></span>
<span data-ttu-id="5ae48-103">Define o assembly que contém tipos e membros de tipo cujos metadados estão disponíveis para reflexão em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5ae48-103">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>  
  
 <span data-ttu-id="5ae48-104">Elemento \<Directives></span><span class="sxs-lookup"><span data-stu-id="5ae48-104">\<Directives> Element</span></span>  
<span data-ttu-id="5ae48-105">Elemento \<Library></span><span class="sxs-lookup"><span data-stu-id="5ae48-105">\<Library> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ae48-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ae48-106">Syntax</span></span>  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ae48-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5ae48-107">Attributes and Elements</span></span>  
 <span data-ttu-id="5ae48-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5ae48-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ae48-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="5ae48-109">Attributes</span></span>  
  
|<span data-ttu-id="5ae48-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="5ae48-110">Attribute</span></span>|<span data-ttu-id="5ae48-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ae48-111">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="5ae48-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="5ae48-112">Required attribute.</span></span> <span data-ttu-id="5ae48-113">Especifica o nome de um assembly.</span><span class="sxs-lookup"><span data-stu-id="5ae48-113">Specifies the name of an assembly.</span></span> <span data-ttu-id="5ae48-114">Elementos filhos deste elemento `<Library>` define a política de reflexão do tempo de execução para tipos e membros de tipo encontrados neste assembly.</span><span class="sxs-lookup"><span data-stu-id="5ae48-114">Child elements of this `<Library>` element define the runtime reflection policy for types and type members found in this assembly.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="5ae48-115">Atributo de nome</span><span class="sxs-lookup"><span data-stu-id="5ae48-115">Name attribute</span></span>  
  
|<span data-ttu-id="5ae48-116">Valor</span><span class="sxs-lookup"><span data-stu-id="5ae48-116">Value</span></span>|<span data-ttu-id="5ae48-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ae48-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5ae48-118">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="5ae48-118">*assembly_name*</span></span>|<span data-ttu-id="5ae48-119">O nome simples do assembly, sem a extensão de arquivo.</span><span class="sxs-lookup"><span data-stu-id="5ae48-119">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="5ae48-120">Este atributo corresponde à propriedade <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5ae48-120">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="5ae48-121">Por exemplo, o nome de um assembly denominado Extensions.dll é "Extensions".</span><span class="sxs-lookup"><span data-stu-id="5ae48-121">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span> <span data-ttu-id="5ae48-122">Consulte a seção Comentários para ver uma forma especial de *assembly_name* que dá suporte à inclusão condicional de metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="5ae48-122">See the Remarks section for a special form of *assembly_name* that supports conditional inclusion of metadata from the assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ae48-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5ae48-123">Child Elements</span></span>  
  
|<span data-ttu-id="5ae48-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ae48-124">Element</span></span>|<span data-ttu-id="5ae48-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ae48-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ae48-126">\<Assembly></span><span class="sxs-lookup"><span data-stu-id="5ae48-126">\<Assembly></span></span>](assembly-element-net-native.md)|<span data-ttu-id="5ae48-127">Aplica a política a todos os tipos em um assembly específico.</span><span class="sxs-lookup"><span data-stu-id="5ae48-127">Applies policy to all the types in a particular assembly.</span></span>|  
|[<span data-ttu-id="5ae48-128">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="5ae48-128">\<Namespace></span></span>](namespace-element-net-native.md)|<span data-ttu-id="5ae48-129">Aplica a política a todos os tipos em um namespace específico.</span><span class="sxs-lookup"><span data-stu-id="5ae48-129">Applies policy to all the types in a particular namespace.</span></span>|  
|[<span data-ttu-id="5ae48-130">\<Type></span><span class="sxs-lookup"><span data-stu-id="5ae48-130">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="5ae48-131">Aplica a política a um tipo específico, como uma classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5ae48-131">Applies policy to a particular type, such as a class or structure.</span></span>|  
|[<span data-ttu-id="5ae48-132">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="5ae48-132">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="5ae48-133">Aplica a política a um tipo genérico construído.</span><span class="sxs-lookup"><span data-stu-id="5ae48-133">Applies policy to a constructed generic type.</span></span> <span data-ttu-id="5ae48-134">Por exemplo, um elemento [\<TypeInstantiation>](typeinstantiation-element-net-native.md) pode ser usado para definir a política para um tipo `List<String>`.</span><span class="sxs-lookup"><span data-stu-id="5ae48-134">For example, a [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element could be used to define policy for a `List<String>` type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5ae48-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5ae48-135">Parent Elements</span></span>  
  
|<span data-ttu-id="5ae48-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ae48-136">Element</span></span>|<span data-ttu-id="5ae48-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ae48-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ae48-138">\<Directives></span><span class="sxs-lookup"><span data-stu-id="5ae48-138">\<Directives></span></span>](directives-element-net-native.md)|<span data-ttu-id="5ae48-139">O elemento raiz de um arquivo de diretivas de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5ae48-139">The root element of a runtime directives file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ae48-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ae48-140">Remarks</span></span>  
 <span data-ttu-id="5ae48-141">O elemento [\<Directives>](directives-element-net-native.md) pode conter zero, um ou mais elementos `<Library>`.</span><span class="sxs-lookup"><span data-stu-id="5ae48-141">The [\<Directives>](directives-element-net-native.md) element can contain zero, one, or more `<Library>` elements.</span></span>  
  
 <span data-ttu-id="5ae48-142">O elemento `<Library>` serve como um contêiner para definir os elementos do programa cujos metadados são necessária no tempo de execução. Este elemento não expressa política.</span><span class="sxs-lookup"><span data-stu-id="5ae48-142">The `<Library>` element serves as a container to define the program elements whose metadata is needed at run time; this element doesn't express policy.</span></span> <span data-ttu-id="5ae48-143">No tempo de compilação, as ferramentas do compilador pesquisam somente a biblioteca designada pelo elemento `<Library>` para os elementos do programa identificados por seus elementos filho.</span><span class="sxs-lookup"><span data-stu-id="5ae48-143">At compile time, compiler tools search only the library designated by the `<Library>` element for program elements identified by its child elements.</span></span> <span data-ttu-id="5ae48-144">Em contraste, as ferramentas do compilador pesquisam todas as bibliotecas, incluindo as bibliotecas principais do .NET Framework, por elementos de programa identificados por elementos filhos do elemento [\<Application>](application-element-net-native.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="5ae48-144">In contrast, compiler tools search all libraries, including.NET Framework core libraries, for program elements identified by child elements of the [\<Application>](application-element-net-native.md) element.</span></span>  
  
 <span data-ttu-id="5ae48-145">As diretivas `<Library>` podem ser utilizadas condicionalmente.</span><span class="sxs-lookup"><span data-stu-id="5ae48-145">`<Library>` directives may be conditionally utilized.</span></span> <span data-ttu-id="5ae48-146">Se o nome do elemento de `<Library>` iniciar e terminar com um asterisco (\*), a diretiva de `<Library>` terá efeito somente se o assembly especificado entre os asteriscos for referenciado pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ae48-146">If the name of the `<Library>` element starts and ends with an asterisk (\*), the `<Library>` directive has an effect only if the assembly specified between the asterisks is referenced by the app.</span></span> <span data-ttu-id="5ae48-147">Por exemplo, a diretiva de tempo de execução a seguir se aplica somente se o assembly Utilities. dll for referenciado pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ae48-147">For example, the following runtime directive applies only if the Utilities.dll assembly is referenced by the app.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ae48-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ae48-148">See also</span></span>

- [<span data-ttu-id="5ae48-149">Elemento de > de aplicativo \<</span><span class="sxs-lookup"><span data-stu-id="5ae48-149">\<Application> Element</span></span>](application-element-net-native.md)
- [<span data-ttu-id="5ae48-150">Elemento de > de diretivas de \<</span><span class="sxs-lookup"><span data-stu-id="5ae48-150">\<Directives> Element</span></span>](directives-element-net-native.md)
- [<span data-ttu-id="5ae48-151">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="5ae48-151">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="5ae48-152">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5ae48-152">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
