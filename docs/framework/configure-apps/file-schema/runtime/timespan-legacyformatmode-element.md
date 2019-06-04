---
title: Elemento <TimeSpan_LegacyFormatMode>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31e2a075f9202439cd62c81a06528b20c4971656
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489341"
---
# <a name="timespanlegacyformatmode-element"></a><span data-ttu-id="8246a-102">\<TimeSpan_LegacyFormatMode > elemento</span><span class="sxs-lookup"><span data-stu-id="8246a-102">\<TimeSpan_LegacyFormatMode> Element</span></span>
<span data-ttu-id="8246a-103">Determina se o tempo de execução preserva o comportamento herdado na formatação de operações com <xref:System.TimeSpan?displayProperty=nameWithType> valores.</span><span class="sxs-lookup"><span data-stu-id="8246a-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>  
  
 <span data-ttu-id="8246a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8246a-104">\<configuration></span></span>  
<span data-ttu-id="8246a-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="8246a-105">\<runtime></span></span>  
<span data-ttu-id="8246a-106"><TimeSpan_LegacyFormatMode></span><span class="sxs-lookup"><span data-stu-id="8246a-106"><TimeSpan_LegacyFormatMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8246a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8246a-107">Syntax</span></span>  
  
```xml  
<TimeSpan_LegacyFormatMode    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8246a-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8246a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8246a-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8246a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8246a-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="8246a-110">Attributes</span></span>  
  
|<span data-ttu-id="8246a-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="8246a-111">Attribute</span></span>|<span data-ttu-id="8246a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="8246a-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="8246a-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="8246a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="8246a-114">Especifica se o tempo de execução usa o comportamento herdado de formatação com <xref:System.TimeSpan?displayProperty=nameWithType> valores.</span><span class="sxs-lookup"><span data-stu-id="8246a-114">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="8246a-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="8246a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="8246a-116">Valor</span><span class="sxs-lookup"><span data-stu-id="8246a-116">Value</span></span>|<span data-ttu-id="8246a-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="8246a-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="8246a-118">O tempo de execução não restaura o comportamento herdado de formatação.</span><span class="sxs-lookup"><span data-stu-id="8246a-118">The runtime does not restore legacy formatting behavior.</span></span>|  
|`true`|<span data-ttu-id="8246a-119">O tempo de execução restaura o comportamento herdado de formatação.</span><span class="sxs-lookup"><span data-stu-id="8246a-119">The runtime restores legacy formatting behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8246a-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8246a-120">Child Elements</span></span>  
 <span data-ttu-id="8246a-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8246a-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8246a-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8246a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="8246a-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="8246a-123">Element</span></span>|<span data-ttu-id="8246a-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="8246a-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8246a-125">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8246a-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="8246a-126">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8246a-126">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8246a-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="8246a-127">Remarks</span></span>  
 <span data-ttu-id="8246a-128">Começando com o .NET Framework 4, o <xref:System.TimeSpan?displayProperty=nameWithType> estrutura implementa o <xref:System.IFormattable> interface e dá suporte a operações com cadeias de caracteres de formato padrão e personalizados de formatação.</span><span class="sxs-lookup"><span data-stu-id="8246a-128">Starting with the .NET Framework 4, the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="8246a-129">Se um método de análise encontra um especificador de formato sem suporte ou uma cadeia de caracteres de formato, ele gerará um <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="8246a-129">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>  
  
 <span data-ttu-id="8246a-130">Nas versões anteriores do .NET Framework, o <xref:System.TimeSpan> estrutura não implementou <xref:System.IFormattable> e não ofereciam suporte a cadeias de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="8246a-130">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="8246a-131">No entanto, muitos desenvolvedores, por engano, supõe-se que <xref:System.TimeSpan> oferecia suporte a um conjunto de cadeias de caracteres de formato e usá-los na [operações de formatação de composição](../../../../../docs/standard/base-types/composite-formatting.md) com métodos como <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8246a-131">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../../docs/standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8246a-132">Normalmente, se um tipo implementa <xref:System.IFormattable> e dá suporte a cadeias de caracteres, chamadas para métodos de formatação com formato sem suporte geralmente geram cadeias de caracteres de formato um <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="8246a-132">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="8246a-133">No entanto, porque <xref:System.TimeSpan> não implementa <xref:System.IFormattable>, o tempo de execução ignorada a cadeia de caracteres de formato e chamado em vez disso, o <xref:System.TimeSpan.ToString?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="8246a-133">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8246a-134">Isso significa que, embora as cadeias de caracteres de formato não tinham efeito sobre a operação de formatação, sua presença não resultou em um <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="8246a-134">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>  
  
 <span data-ttu-id="8246a-135">Para casos em que código herdado passa uma método e uma cadeia de caracteres de formato inválido de formatação de composição e que o código não pode ser recompilado, você pode usar o `<TimeSpan_LegacyFormatMode>` elemento para restaurar herdado <xref:System.TimeSpan> comportamento.</span><span class="sxs-lookup"><span data-stu-id="8246a-135">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="8246a-136">Quando você define o `enabled` atributo desse elemento para `true`, o método resulta em uma chamada para formatação de composição <xref:System.TimeSpan.ToString?displayProperty=nameWithType> vez <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>e um <xref:System.FormatException> não é lançada.</span><span class="sxs-lookup"><span data-stu-id="8246a-136">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8246a-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8246a-137">Example</span></span>  
 <span data-ttu-id="8246a-138">O exemplo a seguir instancia um <xref:System.TimeSpan> objeto e tentar formatá-la com o <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> método usando uma cadeia de caracteres de formato padrão sem suporte.</span><span class="sxs-lookup"><span data-stu-id="8246a-138">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>  
  
 [!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
 [!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]  
  
 <span data-ttu-id="8246a-139">Quando você executa o exemplo no [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] ou em uma versão anterior, ele exibe a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="8246a-139">When you run the example on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] or on an earlier version, it displays the following output:</span></span>  
  
```  
12:30:45  
```  
  
 <span data-ttu-id="8246a-140">Isso difere significativamente da saída se você executar o exemplo no .NET Framework 4 ou versão posterior:</span><span class="sxs-lookup"><span data-stu-id="8246a-140">This differs markedly from the output if you run the example on the .NET Framework 4 or later version:</span></span>  
  
```  
Invalid Format  
```  
  
 <span data-ttu-id="8246a-141">No entanto, se você adicionar o seguinte arquivo de configuração para o diretório de exemplo e, em seguida, executar o exemplo no .NET Framework 4 ou versão posterior, a saída será idêntica à produzida pelo exemplo quando ele é executado em [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8246a-141">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4 or later version, the output is identical to that produced by the example when it is run on [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <TimeSpan_LegacyFormatMode enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8246a-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8246a-142">See also</span></span>

- [<span data-ttu-id="8246a-143">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="8246a-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="8246a-144">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="8246a-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
