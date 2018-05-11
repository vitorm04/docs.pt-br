---
title: '&lt;CompatSortNLSVersion&gt; elemento'
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
ms.openlocfilehash: e78106c4df2e1c414d00f18871566dd5906c54f2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcompatsortnlsversiongt-element"></a><span data-ttu-id="db724-102">&lt;CompatSortNLSVersion&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="db724-102">&lt;CompatSortNLSVersion&gt; Element</span></span>
<span data-ttu-id="db724-103">Especifica que o tempo de execução deve usar as ordens de classificação herdadas ao executar comparações de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="db724-103">Specifies that the runtime should use legacy sort orders when performing string comparisons.</span></span>  
  
 <span data-ttu-id="db724-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="db724-104">\<configuration></span></span>  
<span data-ttu-id="db724-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="db724-105">\<runtime></span></span>  
<span data-ttu-id="db724-106">\<CompatSortNLSVersion > elemento</span><span class="sxs-lookup"><span data-stu-id="db724-106">\<CompatSortNLSVersion> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db724-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db724-107">Syntax</span></span>  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db724-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="db724-108">Attributes and Elements</span></span>  
 <span data-ttu-id="db724-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="db724-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db724-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="db724-110">Attributes</span></span>  
  
|<span data-ttu-id="db724-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="db724-111">Attribute</span></span>|<span data-ttu-id="db724-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="db724-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="db724-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="db724-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="db724-114">Especifica a ID de localidade cuja ordem de classificação deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="db724-114">Specifies the locale ID whose sort order is to be used.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="db724-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="db724-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="db724-116">Valor</span><span class="sxs-lookup"><span data-stu-id="db724-116">Value</span></span>|<span data-ttu-id="db724-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="db724-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="db724-118">4096</span><span class="sxs-lookup"><span data-stu-id="db724-118">4096</span></span>|<span data-ttu-id="db724-119">A ID de localidade que representa uma ordem de classificação alternativa.</span><span class="sxs-lookup"><span data-stu-id="db724-119">The locale ID that represents an alternate sort order.</span></span> <span data-ttu-id="db724-120">Neste caso, 4096 representa a ordem de classificação do [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] e versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="db724-120">In this case, 4096 represents the sort order of the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] and earlier versions.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db724-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="db724-121">Child Elements</span></span>  
 <span data-ttu-id="db724-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="db724-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db724-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="db724-123">Parent Elements</span></span>  
  
|<span data-ttu-id="db724-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="db724-124">Element</span></span>|<span data-ttu-id="db724-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="db724-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="db724-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="db724-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="db724-127">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="db724-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db724-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="db724-128">Remarks</span></span>  
 <span data-ttu-id="db724-129">Pois operações de maiusculas e minúsculas, classificação e comparação de cadeia de caracteres executada pelo <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> classe no [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] está de acordo com o Unicode 5.1 padrão, os resultados dos métodos de comparação de cadeia de caracteres como <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> e <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> podem diferir versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="db724-129">Because string comparison, sorting, and casing operations performed by the <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> class in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] conform to the Unicode 5.1 standard, the results of string comparison methods such as <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> and <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> may differ from previous versions of the .NET Framework.</span></span> <span data-ttu-id="db724-130">Se seu aplicativo depender de comportamento herdado, você poderá restaurar as regras de classificação e comparação de cadeia de caracteres usadas no [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] e em versões anteriores ao incluir o elemento `<CompatSortNLSVersion>` no arquivo de configuração do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="db724-130">If your application depends on legacy behavior, you can restore the string comparison and sorting rules used in the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] and earlier versions by including the `<CompatSortNLSVersion>` element in your application's configuration file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="db724-131">Restaurar a comparação e as regras de classificação de cadeia de caracteres herdadas também requer que a biblioteca de vínculo dinâmico do arquivo sort00001000.dll esteja disponível no sistema local.</span><span class="sxs-lookup"><span data-stu-id="db724-131">Restoring legacy string comparison and sorting rules also requires the sort00001000.dll dynamic link library to be available on the local system.</span></span>  
  
 <span data-ttu-id="db724-132">Você também pode usar regras de classificação e comparação herdadas em um domínio de aplicativo específico ao passar a cadeia de caracteres "NetFx40_Legacy20SortingBehavior" ao método <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> quando o domínio do aplicativo é criado.</span><span class="sxs-lookup"><span data-stu-id="db724-132">You can also use legacy string sorting and comparison rules in a specific application domain by passing the string "NetFx40_Legacy20SortingBehavior" to the <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> method when you create the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db724-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="db724-133">Example</span></span>  
 <span data-ttu-id="db724-134">O exemplo a seguir cria uma instância de dois objetos <xref:System.String> e chama o método <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> para compará-los ao usar as convenções da cultura atual.</span><span class="sxs-lookup"><span data-stu-id="db724-134">The following example instantiates two <xref:System.String> objects and calls the <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method to compare them by using the conventions of the current culture.</span></span>  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 <span data-ttu-id="db724-135">Ao executar o exemplo no [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], ele exibe a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="db724-135">When you run the example on the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], it displays the following output.</span></span>  
  
```  
sta follows a in the sort order.  
```  
  
 <span data-ttu-id="db724-136">Isso é completamente diferente de saída exibida quando você executa o exemplo no [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db724-136">This is completely different from the output that is displayed when you run the example on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```  
sta equals a in the sort order.  
```  
  
 <span data-ttu-id="db724-137">No entanto, se você adicionar o arquivo de configuração a seguir ao diretório do exemplo e executar o exemplo no [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], a saída será idêntica à produzida pelo exemplo quando ele é executado no [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db724-137">However, if you add the following configuration file to the example's directory and then run the example on the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the output is identical to that produced by the example when it is run on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="db724-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db724-138">See Also</span></span>  
 [<span data-ttu-id="db724-139">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="db724-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="db724-140">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="db724-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
