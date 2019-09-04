---
title: Elemento <CompatSortNLSVersion>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 575d44ad9ecf445ba5d4b7fbe47032127ccb33ae
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252727"
---
# <a name="compatsortnlsversion-element"></a><span data-ttu-id="bfb6f-102">\<Elemento de > CompatSortNLSVersion</span><span class="sxs-lookup"><span data-stu-id="bfb6f-102">\<CompatSortNLSVersion> Element</span></span>
<span data-ttu-id="bfb6f-103">Especifica que o tempo de execução deve usar as ordens de classificação herdadas ao executar comparações de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-103">Specifies that the runtime should use legacy sort orders when performing string comparisons.</span></span>  
  
<span data-ttu-id="bfb6f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bfb6f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bfb6f-105">&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="bfb6f-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="bfb6f-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<CompatSortNLSVersion>**</span><span class="sxs-lookup"><span data-stu-id="bfb6f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<CompatSortNLSVersion>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfb6f-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bfb6f-107">Syntax</span></span>  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bfb6f-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bfb6f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bfb6f-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bfb6f-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="bfb6f-110">Attributes</span></span>  
  
|<span data-ttu-id="bfb6f-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="bfb6f-111">Attribute</span></span>|<span data-ttu-id="bfb6f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="bfb6f-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="bfb6f-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="bfb6f-114">Especifica a ID de localidade cuja ordem de classificação deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-114">Specifies the locale ID whose sort order is to be used.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="bfb6f-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="bfb6f-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="bfb6f-116">Valor</span><span class="sxs-lookup"><span data-stu-id="bfb6f-116">Value</span></span>|<span data-ttu-id="bfb6f-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="bfb6f-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bfb6f-118">4096</span><span class="sxs-lookup"><span data-stu-id="bfb6f-118">4096</span></span>|<span data-ttu-id="bfb6f-119">A ID de localidade que representa uma ordem de classificação alternativa.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-119">The locale ID that represents an alternate sort order.</span></span> <span data-ttu-id="bfb6f-120">Nesse caso, 4096 representa a ordem de classificação do .NET Framework 3,5 e versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-120">In this case, 4096 represents the sort order of the .NET Framework 3.5 and earlier versions.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bfb6f-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bfb6f-121">Child Elements</span></span>  
 <span data-ttu-id="bfb6f-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bfb6f-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bfb6f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bfb6f-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="bfb6f-124">Element</span></span>|<span data-ttu-id="bfb6f-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="bfb6f-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bfb6f-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="bfb6f-127">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfb6f-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="bfb6f-128">Remarks</span></span>  
 <span data-ttu-id="bfb6f-129">Como as operações de comparação de cadeia de caracteres, classificação e <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> maiúsculas e minúsculas executadas pela classe no .NET Framework 4 estão em conformidade com o padrão Unicode 5,1, <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> os <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> resultados dos métodos de comparação de cadeia de caracteres, como e podem ser diferentes de versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-129">Because string comparison, sorting, and casing operations performed by the <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> class in the .NET Framework 4 conform to the Unicode 5.1 standard, the results of string comparison methods such as <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> and <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> may differ from previous versions of the .NET Framework.</span></span> <span data-ttu-id="bfb6f-130">Se seu aplicativo depender de comportamento herdado, você poderá restaurar a comparação de cadeias de caracteres e as regras de classificação usadas no .NET Framework 3,5 `<CompatSortNLSVersion>` e versões anteriores, incluindo o elemento no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-130">If your application depends on legacy behavior, you can restore the string comparison and sorting rules used in the .NET Framework 3.5 and earlier versions by including the `<CompatSortNLSVersion>` element in your application's configuration file.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bfb6f-131">Restaurar a comparação e as regras de classificação de cadeia de caracteres herdadas também requer que a biblioteca de vínculo dinâmico do arquivo sort00001000.dll esteja disponível no sistema local.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-131">Restoring legacy string comparison and sorting rules also requires the sort00001000.dll dynamic link library to be available on the local system.</span></span>  
  
 <span data-ttu-id="bfb6f-132">Você também pode usar regras de classificação e comparação herdadas em um domínio de aplicativo específico ao passar a cadeia de caracteres "NetFx40_Legacy20SortingBehavior" ao método <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> quando o domínio do aplicativo é criado.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-132">You can also use legacy string sorting and comparison rules in a specific application domain by passing the string "NetFx40_Legacy20SortingBehavior" to the <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> method when you create the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfb6f-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bfb6f-133">Example</span></span>  
 <span data-ttu-id="bfb6f-134">O exemplo a seguir cria uma instância de dois objetos <xref:System.String> e chama o método <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> para compará-los ao usar as convenções da cultura atual.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-134">The following example instantiates two <xref:System.String> objects and calls the <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method to compare them by using the conventions of the current culture.</span></span>  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 <span data-ttu-id="bfb6f-135">Quando você executa o exemplo no .NET Framework 4, ele exibe a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-135">When you run the example on the .NET Framework 4, it displays the following output.</span></span>  
  
```  
sta follows a in the sort order.  
```  
  
 <span data-ttu-id="bfb6f-136">Isso é completamente diferente da saída que é exibida quando você executa o exemplo no .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-136">This is completely different from the output that is displayed when you run the example on the .NET Framework 3.5.</span></span>  
  
```  
sta equals a in the sort order.  
```  
  
 <span data-ttu-id="bfb6f-137">No entanto, se você adicionar o seguinte arquivo de configuração ao diretório do exemplo e, em seguida, executar o exemplo no .NET Framework 4, a saída será idêntica à produzida pelo exemplo quando for executada no .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-137">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4, the output is identical to that produced by the example when it is run on the .NET Framework 3.5.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bfb6f-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bfb6f-138">See also</span></span>

- [<span data-ttu-id="bfb6f-139">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="bfb6f-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bfb6f-140">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="bfb6f-140">Configuration File Schema</span></span>](../index.md)
