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
ms.openlocfilehash: 30afeb2ab9380db75cbeb723ea15a23e4313c9e8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154264"
---
# <a name="compatsortnlsversion-element"></a><span data-ttu-id="3975d-102">Elemento \<CompatSortNLSVersion></span><span class="sxs-lookup"><span data-stu-id="3975d-102">\<CompatSortNLSVersion> Element</span></span>
<span data-ttu-id="3975d-103">Especifica que o runtime deve usar as ordens de classificação herdadas ao executar comparações de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3975d-103">Specifies that the runtime should use legacy sort orders when performing string comparisons.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<CompatSortNLSVersion>**  
  
## <a name="syntax"></a><span data-ttu-id="3975d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3975d-104">Syntax</span></span>  
  
```xml  
<CompatSortNLSVersion
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3975d-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3975d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3975d-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3975d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3975d-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="3975d-107">Attributes</span></span>  
  
|<span data-ttu-id="3975d-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="3975d-108">Attribute</span></span>|<span data-ttu-id="3975d-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="3975d-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="3975d-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="3975d-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="3975d-111">Especifica a ID de localidade cuja ordem de classificação deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="3975d-111">Specifies the locale ID whose sort order is to be used.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3975d-112">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="3975d-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="3975d-113">Valor</span><span class="sxs-lookup"><span data-stu-id="3975d-113">Value</span></span>|<span data-ttu-id="3975d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="3975d-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3975d-115">4096</span><span class="sxs-lookup"><span data-stu-id="3975d-115">4096</span></span>|<span data-ttu-id="3975d-116">A ID de localidade que representa uma ordem de classificação alternativa.</span><span class="sxs-lookup"><span data-stu-id="3975d-116">The locale ID that represents an alternate sort order.</span></span> <span data-ttu-id="3975d-117">Nesse caso, 4096 representa a ordem de classificação do .NET Framework 3,5 e versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="3975d-117">In this case, 4096 represents the sort order of the .NET Framework 3.5 and earlier versions.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3975d-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3975d-118">Child Elements</span></span>  
 <span data-ttu-id="3975d-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3975d-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3975d-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3975d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3975d-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="3975d-121">Element</span></span>|<span data-ttu-id="3975d-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="3975d-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3975d-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3975d-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3975d-124">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="3975d-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3975d-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="3975d-125">Remarks</span></span>  
 <span data-ttu-id="3975d-126">Como as operações de comparação de cadeia de caracteres, classificação e maiúsculas e minúsculas executadas pela <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> classe no .NET Framework 4 estão em conformidade com o padrão Unicode 5,1, os resultados dos métodos de comparação de cadeia de caracteres, como <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> e <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> podem ser diferentes das versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3975d-126">Because string comparison, sorting, and casing operations performed by the <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> class in the .NET Framework 4 conform to the Unicode 5.1 standard, the results of string comparison methods such as <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> and <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> may differ from previous versions of the .NET Framework.</span></span> <span data-ttu-id="3975d-127">Se seu aplicativo depender de comportamento herdado, você poderá restaurar a comparação de cadeias de caracteres e as regras de classificação usadas no .NET Framework 3,5 e versões anteriores, incluindo o `<CompatSortNLSVersion>` elemento no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3975d-127">If your application depends on legacy behavior, you can restore the string comparison and sorting rules used in the .NET Framework 3.5 and earlier versions by including the `<CompatSortNLSVersion>` element in your application's configuration file.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3975d-128">Restaurar a comparação e as regras de classificação de cadeia de caracteres herdadas também requer que a biblioteca de vínculo dinâmico do arquivo sort00001000.dll esteja disponível no sistema local.</span><span class="sxs-lookup"><span data-stu-id="3975d-128">Restoring legacy string comparison and sorting rules also requires the sort00001000.dll dynamic link library to be available on the local system.</span></span>  
  
 <span data-ttu-id="3975d-129">Você também pode usar regras de classificação e comparação herdadas em um domínio de aplicativo específico ao passar a cadeia de caracteres "NetFx40_Legacy20SortingBehavior" ao método <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> quando o domínio do aplicativo é criado.</span><span class="sxs-lookup"><span data-stu-id="3975d-129">You can also use legacy string sorting and comparison rules in a specific application domain by passing the string "NetFx40_Legacy20SortingBehavior" to the <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> method when you create the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3975d-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3975d-130">Example</span></span>  
 <span data-ttu-id="3975d-131">O exemplo a seguir cria uma instância de dois objetos <xref:System.String> e chama o método <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> para compará-los ao usar as convenções da cultura atual.</span><span class="sxs-lookup"><span data-stu-id="3975d-131">The following example instantiates two <xref:System.String> objects and calls the <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method to compare them by using the conventions of the current culture.</span></span>  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 <span data-ttu-id="3975d-132">Quando você executa o exemplo no .NET Framework 4, ele exibe a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="3975d-132">When you run the example on the .NET Framework 4, it displays the following output:</span></span>
  
```console
sta follows a in the sort order.  
```  
  
 <span data-ttu-id="3975d-133">Isso é completamente diferente da saída que é exibida quando você executa o exemplo no .NET Framework 3,5:</span><span class="sxs-lookup"><span data-stu-id="3975d-133">This is completely different from the output that is displayed when you run the example on the .NET Framework 3.5:</span></span>
  
```console
sta equals a in the sort order.  
```  
  
 <span data-ttu-id="3975d-134">No entanto, se você adicionar o seguinte arquivo de configuração ao diretório do exemplo e, em seguida, executar o exemplo no .NET Framework 4, a saída será idêntica à produzida pelo exemplo quando for executada no .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="3975d-134">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4, the output is identical to that produced by the example when it is run on the .NET Framework 3.5.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3975d-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="3975d-135">See also</span></span>

- [<span data-ttu-id="3975d-136">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="3975d-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3975d-137">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="3975d-137">Configuration File Schema</span></span>](../index.md)
