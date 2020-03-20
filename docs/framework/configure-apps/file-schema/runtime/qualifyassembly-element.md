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
ms.openlocfilehash: 74e83900c68ab4b3fe01beb3f97657b0140d78ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153913"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="62976-102">\<qualificarElemento> Assembly</span><span class="sxs-lookup"><span data-stu-id="62976-102">\<qualifyAssembly> Element</span></span>
<span data-ttu-id="62976-103">Especifica o nome completo do assembly que deve ser carregado dinamicamente quando um nome parcial é usado.</span><span class="sxs-lookup"><span data-stu-id="62976-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
<span data-ttu-id="62976-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="62976-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="62976-105">&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="62976-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="62976-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<montagem>vinculante**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="62976-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="62976-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualificar>de montagem**</span><span class="sxs-lookup"><span data-stu-id="62976-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62976-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="62976-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62976-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="62976-109">Attributes and Elements</span></span>  
 <span data-ttu-id="62976-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="62976-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62976-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="62976-111">Attributes</span></span>  
  
|<span data-ttu-id="62976-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="62976-112">Attribute</span></span>|<span data-ttu-id="62976-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="62976-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="62976-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="62976-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="62976-115">Especifica o nome parcial do conjunto como aparece no código.</span><span class="sxs-lookup"><span data-stu-id="62976-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="62976-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="62976-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="62976-117">Especifica o nome completo da montagem como ela aparece no cache de montagem global.</span><span class="sxs-lookup"><span data-stu-id="62976-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62976-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="62976-118">Child Elements</span></span>  
 <span data-ttu-id="62976-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="62976-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62976-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="62976-120">Parent Elements</span></span>  
  
|<span data-ttu-id="62976-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="62976-121">Element</span></span>|<span data-ttu-id="62976-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="62976-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="62976-123">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="62976-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="62976-124">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="62976-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="62976-125">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="62976-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62976-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="62976-126">Remarks</span></span>  
 <span data-ttu-id="62976-127">Chamar <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> o método usando nomes de montagem parciais faz com que o tempo de execução do idioma comum procure o conjunto apenas no diretório base do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="62976-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="62976-128">Use \*\* \<\*\* o elemento qualifyAssembly>no arquivo de configuração do aplicativo para fornecer as informações completas de montagem (nome, versão, token de chave pública e cultura) e faça com que o tempo de execução do idioma comum procure a montagem no cache de montagem global.</span><span class="sxs-lookup"><span data-stu-id="62976-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="62976-129">O atributo **fullName** deve incluir os quatro campos de identidade de montagem: nome, versão, token de chave pública e cultura.</span><span class="sxs-lookup"><span data-stu-id="62976-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="62976-130">O **atributo Nome parcial** deve fazer referência parcial a um conjunto.</span><span class="sxs-lookup"><span data-stu-id="62976-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="62976-131">Você deve especificar pelo menos o nome de texto da assembléia (o caso mais comum), mas você também pode incluir versão, token de chave pública ou cultura (ou qualquer combinação dos quatro, mas não todos os quatro).</span><span class="sxs-lookup"><span data-stu-id="62976-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="62976-132">A **parcialNome** deve corresponder ao nome especificado em sua chamada.</span><span class="sxs-lookup"><span data-stu-id="62976-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="62976-133">Por exemplo, você `"math"` não pode especificar como o `Assembly.Load("math, Version=3.3.3.3")` atributo nome **parcial** em seu arquivo de configuração e chamar em seu código.</span><span class="sxs-lookup"><span data-stu-id="62976-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62976-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="62976-134">Example</span></span>  
 <span data-ttu-id="62976-135">O exemplo a seguir, `Assembly.Load("math")` `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`logicamente, transforma a chamada em .</span><span class="sxs-lookup"><span data-stu-id="62976-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="62976-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="62976-136">See also</span></span>

- [<span data-ttu-id="62976-137">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="62976-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="62976-138">Como o runtime localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="62976-138">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="62976-139">[Referências parciais a assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="62976-139">[Partial Assembly References](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
