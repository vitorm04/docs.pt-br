---
title: Elemento <qualifyAssembly>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
ms.openlocfilehash: 26b265996a059d8e52901557603bcf5e7636e596
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195214"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="38960-102">Elemento \<qualifyAssembly></span><span class="sxs-lookup"><span data-stu-id="38960-102">\<qualifyAssembly> Element</span></span>

<span data-ttu-id="38960-103">Especifica o nome completo do assembly que deve ser carregado dinamicamente quando um nome parcial é usado.</span><span class="sxs-lookup"><span data-stu-id="38960-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="38960-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38960-104">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38960-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="38960-105">Attributes and Elements</span></span>  

 <span data-ttu-id="38960-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="38960-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38960-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="38960-107">Attributes</span></span>  
  
|<span data-ttu-id="38960-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="38960-108">Attribute</span></span>|<span data-ttu-id="38960-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="38960-109">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="38960-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="38960-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="38960-111">Especifica o nome parcial do assembly como ele aparece no código.</span><span class="sxs-lookup"><span data-stu-id="38960-111">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="38960-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="38960-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="38960-113">Especifica o nome completo do assembly como ele aparece no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="38960-113">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38960-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="38960-114">Child Elements</span></span>  

 <span data-ttu-id="38960-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="38960-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38960-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="38960-116">Parent Elements</span></span>  
  
|<span data-ttu-id="38960-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="38960-117">Element</span></span>|<span data-ttu-id="38960-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="38960-118">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="38960-119">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="38960-119">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="38960-120">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="38960-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="38960-121">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="38960-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38960-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="38960-122">Remarks</span></span>  

 <span data-ttu-id="38960-123">Chamar o <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> método usando nomes de assembly parciais faz com que o Common Language Runtime procure o assembly somente no diretório base do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="38960-123">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="38960-124">Use o **\<qualifyAssembly>** elemento no arquivo de configuração do aplicativo para fornecer as informações completas do assembly (nome, versão, token de chave pública e cultura) e faça com que o Common Language Runtime procure o assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="38960-124">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="38960-125">O atributo **FullName** deve incluir os quatro campos da identidade do assembly: nome, versão, token de chave pública e cultura.</span><span class="sxs-lookup"><span data-stu-id="38960-125">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="38960-126">O atributo **partialName** deve fazer referência parcial a um assembly.</span><span class="sxs-lookup"><span data-stu-id="38960-126">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="38960-127">Você deve especificar pelo menos o nome de texto do assembly (o caso mais comum), mas também pode incluir a versão, o token de chave pública ou a cultura (ou qualquer combinação dos quatro, mas não todos os quatro).</span><span class="sxs-lookup"><span data-stu-id="38960-127">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="38960-128">O **partialName** deve corresponder ao nome especificado em sua chamada.</span><span class="sxs-lookup"><span data-stu-id="38960-128">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="38960-129">Por exemplo, você não pode especificar `"math"` como o atributo **partialName** no arquivo de configuração e chamar `Assembly.Load("math, Version=3.3.3.3")` seu código.</span><span class="sxs-lookup"><span data-stu-id="38960-129">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38960-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="38960-130">Example</span></span>  

 <span data-ttu-id="38960-131">O exemplo a seguir transforma logicamente a chamada `Assembly.Load("math")` em `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")` .</span><span class="sxs-lookup"><span data-stu-id="38960-131">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="38960-132">Veja também</span><span class="sxs-lookup"><span data-stu-id="38960-132">See also</span></span>

- [<span data-ttu-id="38960-133">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="38960-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="38960-134">Como o runtime localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="38960-134">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="38960-135">[Referências parciais a assemblies](/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="38960-135">[Partial Assembly References](/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
