---
title: Diretiva x:TypeArguments
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: 28eda94914125f2c5849a471671c8e283475c82c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44225601"
---
# <a name="xtypearguments-directive"></a><span data-ttu-id="0cf01-102">Diretiva x:TypeArguments</span><span class="sxs-lookup"><span data-stu-id="0cf01-102">x:TypeArguments Directive</span></span>
<span data-ttu-id="0cf01-103">Passa a restrição de tipo de argumentos de um genérico para o construtor do tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="0cf01-103">Passes constraining type arguments of a generic to the constructor of the generic type.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="0cf01-104">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="0cf01-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="0cf01-105">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="0cf01-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`object`|<span data-ttu-id="0cf01-106">Uma declaração de elemento de objeto de um tipo XAML, que é apoiada por um tipo genérico do CLR.</span><span class="sxs-lookup"><span data-stu-id="0cf01-106">An object element declaration of a XAML type, which is backed by a CLR generic type.</span></span> <span data-ttu-id="0cf01-107">Se `object` refere-se a um tipo XAML que não é do namespace XAML padrão, `object` requer um prefixo para indicar o namespace XAML em que `object` existe.</span><span class="sxs-lookup"><span data-stu-id="0cf01-107">If `object` refers to a XAML type that is not from the default XAML namespace, `object` requires a prefix to indicate the XAML namespace where `object` exists.</span></span>|  
|`typeString`|<span data-ttu-id="0cf01-108">Uma cadeia de caracteres que declara um ou mais XAML Digite nomes como cadeias de caracteres, que fornece os argumentos de tipo para o tipo genérico do CLR.</span><span class="sxs-lookup"><span data-stu-id="0cf01-108">A string that declares one or more XAML type names as strings, which supplies the type arguments for the CLR generic type.</span></span> <span data-ttu-id="0cf01-109">Consulte os comentários para observações sobre a sintaxe adicional.</span><span class="sxs-lookup"><span data-stu-id="0cf01-109">See Remarks for additional syntax notes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cf01-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="0cf01-110">Remarks</span></span>  
 <span data-ttu-id="0cf01-111">Na maioria dos casos, os tipos XAML que são usados como um item de informações em um `typeString` cadeia de caracteres têm o prefixo.</span><span class="sxs-lookup"><span data-stu-id="0cf01-111">In most cases, the XAML types that are used as an information item in a `typeString` string are prefixed.</span></span> <span data-ttu-id="0cf01-112">Tipos típicos de restrições genéricas do CLR (por exemplo, <xref:System.Int32> e <xref:System.String>) provenientes de bibliotecas de classes base do CLR.</span><span class="sxs-lookup"><span data-stu-id="0cf01-112">Typical types of CLR generic constraints (for example, <xref:System.Int32> and <xref:System.String>) come from CLR base class libraries.</span></span> <span data-ttu-id="0cf01-113">Essas bibliotecas não são mapeadas para típico padrão de específicas da estrutura XAML namespaces e, portanto, exigem um prefixo de mapeamento para o uso do XAML.</span><span class="sxs-lookup"><span data-stu-id="0cf01-113">Those libraries are not mapped to typical framework-specific default XAML namespaces, and therefore, require a prefix mapping for XAML usage.</span></span>  
  
 <span data-ttu-id="0cf01-114">Você pode especificar mais de um nome de tipo XAML usando um delimitador de vírgula.</span><span class="sxs-lookup"><span data-stu-id="0cf01-114">You can specify more than one XAML type name by using a comma delimiter.</span></span>  
  
 <span data-ttu-id="0cf01-115">Se as restrições genéricas em si usam tipos genéricos, os argumentos de tipo de restrição aninhadas podem estar contidos por parênteses ().</span><span class="sxs-lookup"><span data-stu-id="0cf01-115">If the generic constraints themselves use generic types, the nested constraint type arguments can be contained by parentheses ().</span></span>  
  
 <span data-ttu-id="0cf01-116">Observe que essa definição de `x:TypeArguments` é específico para serviços de XAML do .NET Framework e usando o CLR de retorno.</span><span class="sxs-lookup"><span data-stu-id="0cf01-116">Note that this definition of `x:TypeArguments` is specific to .NET Framework XAML Services and using CLR backing.</span></span> <span data-ttu-id="0cf01-117">Uma definição de nível de linguagem pode ser encontrada em [ \[MS-XAML\] seção 5.3.11](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="0cf01-117">A language-level definition can be found in [\[MS-XAML\] Section 5.3.11](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="usage-examples"></a><span data-ttu-id="0cf01-118">Exemplos de uso</span><span class="sxs-lookup"><span data-stu-id="0cf01-118">Usage Examples</span></span>  
 <span data-ttu-id="0cf01-119">Nestes exemplos, suponha que as seguintes definições de namespace XAML são declaradas:</span><span class="sxs-lookup"><span data-stu-id="0cf01-119">For these examples, assume that the following XAML namespace definitions are declared:</span></span>  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a><span data-ttu-id="0cf01-120">Lista\<cadeia de caracteres ></span><span class="sxs-lookup"><span data-stu-id="0cf01-120">List\<String></span></span>  
 <span data-ttu-id="0cf01-121">`<scg:List x:TypeArguments="sys:String" ...>` cria uma nova <xref:System.Collections.Generic.List%601> com um <xref:System.String> argumento de tipo.</span><span class="sxs-lookup"><span data-stu-id="0cf01-121">`<scg:List x:TypeArguments="sys:String" ...>` instantiates a new <xref:System.Collections.Generic.List%601> with a <xref:System.String> type argument.</span></span>  
  
### <a name="dictionarystringstring"></a><span data-ttu-id="0cf01-122">Dicionário\<String, String ></span><span class="sxs-lookup"><span data-stu-id="0cf01-122">Dictionary\<String,String></span></span>  
 <span data-ttu-id="0cf01-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` cria uma nova <xref:System.Collections.Generic.Dictionary%602> com dois <xref:System.String> argumentos de tipo.</span><span class="sxs-lookup"><span data-stu-id="0cf01-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instantiates a new <xref:System.Collections.Generic.Dictionary%602> with two <xref:System.String> type arguments.</span></span>  
  
### <a name="queuekeyvaluepairstringstring"></a><span data-ttu-id="0cf01-124">Fila < KeyValuePair\<String, String >></span><span class="sxs-lookup"><span data-stu-id="0cf01-124">Queue<KeyValuePair\<String,String>></span></span>  
 <span data-ttu-id="0cf01-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` cria uma nova <xref:System.Collections.Generic.Queue%601> que tem uma restrição de <xref:System.Collections.Generic.KeyValuePair%602> com os argumentos de tipo de restrição interna <xref:System.String> e <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="0cf01-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instantiates a new <xref:System.Collections.Generic.Queue%601> that has a constraint of <xref:System.Collections.Generic.KeyValuePair%602> with the inner constraint type arguments <xref:System.String> and <xref:System.String>.</span></span>  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a><span data-ttu-id="0cf01-126">Usos XAML genérico do XAML 2006 e o WPF</span><span class="sxs-lookup"><span data-stu-id="0cf01-126">XAML 2006 and WPF Generic XAML Usages</span></span>  
 <span data-ttu-id="0cf01-127">Para uso do XAML 2006 e XAML que é usado para aplicativos do WPF, existem as seguintes restrições para `x:TypeArguments` e usos de tipo genérico do XAML em geral:</span><span class="sxs-lookup"><span data-stu-id="0cf01-127">For XAML 2006 usage, and XAML that is used for WPF applications, the following restrictions exist for `x:TypeArguments` and generic type usages from XAML in general:</span></span>  
  
-   <span data-ttu-id="0cf01-128">Apenas o elemento raiz de um arquivo XAML pode dar suporte a um uso genérico de XAML que faz referência a um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="0cf01-128">Only the root element of a XAML file can support a generic XAML usage that references a generic type.</span></span>  
  
-   <span data-ttu-id="0cf01-129">O elemento raiz deve mapear para um tipo genérico com pelo menos um argumento de tipo.</span><span class="sxs-lookup"><span data-stu-id="0cf01-129">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="0cf01-130">Um exemplo é <xref:System.Windows.Navigation.PageFunction%601>.</span><span class="sxs-lookup"><span data-stu-id="0cf01-130">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="0cf01-131">As funções de página são o cenário principal para suporte ao uso de genéricos de XAML no WPF.</span><span class="sxs-lookup"><span data-stu-id="0cf01-131">The page functions are the primary scenario for XAML generic usage support in WPF.</span></span>  
  
-   <span data-ttu-id="0cf01-132">O elemento de objeto XAML de elemento raiz para o genérico também deve declarar uma classe parcial usando `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="0cf01-132">The root element XAML object element for the generic must also declare a partial class using `x:Class`.</span></span> <span data-ttu-id="0cf01-133">Isso é verdadeiro mesmo se a ação de build definindo um WPF.</span><span class="sxs-lookup"><span data-stu-id="0cf01-133">This is true even if defining a WPF build action.</span></span>  
  
-   <span data-ttu-id="0cf01-134">`x:TypeArguments` não é possível fazer referência a restrições genéricas aninhadas.</span><span class="sxs-lookup"><span data-stu-id="0cf01-134">`x:TypeArguments` cannot reference nested generic constraints.</span></span>  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a><span data-ttu-id="0cf01-135">XAML 2009 ou XAML 2006 sem 3.0 do WPF ou WPF 3.5 dependência</span><span class="sxs-lookup"><span data-stu-id="0cf01-135">XAML 2009 or XAML 2006 with No WPF 3.0 or WPF 3.5 Dependency</span></span>  
 <span data-ttu-id="0cf01-136">Em serviços de XAML .NET Framework para XAML 2006 ou XAML 2009, as restrições relacionadas a WPF no uso de genéricos XAML são reduzidas.</span><span class="sxs-lookup"><span data-stu-id="0cf01-136">In .NET Framework XAML Services for either XAML 2006 or XAML 2009, the WPF-related restrictions on generic XAML usage are relaxed.</span></span> <span data-ttu-id="0cf01-137">Você pode instanciar um elemento de objeto genérico em qualquer posição na marcação XAML que o modelo de objeto e de sistema de tipo backup pode dar suporte.</span><span class="sxs-lookup"><span data-stu-id="0cf01-137">You can instantiate a generic object element at any position in XAML markup that the backing type system and object model can support.</span></span>  
  
 <span data-ttu-id="0cf01-138">Se você usar o XAML 2009 em vez de mapeamento do CLR tipos para obter tipos XAML para primitivos de linguagem comuns de base, você pode usar [tipos inseridos para primitivos de linguagem XAML comuns](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) como itens de informações em um `typeString`.</span><span class="sxs-lookup"><span data-stu-id="0cf01-138">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [Built-in Types for Common XAML Language Primitives](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) as information items in a `typeString`.</span></span> <span data-ttu-id="0cf01-139">Por exemplo, você poderia declarar o seguinte (mapeamentos de prefixo não mostrados, mas x é o namespace XAML de linguagem XAML para o XAML 2009):</span><span class="sxs-lookup"><span data-stu-id="0cf01-139">For example, you could declare the following (prefix mappings not shown, but x is the XAML language XAML namespace for XAML 2009):</span></span>  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 <span data-ttu-id="0cf01-140">No WPF e ao direcionar [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], você pode usar recursos do XAML 2009 junto com `x:TypeArguments` , mas somente para XAML flexível (XAML não é compilado por marcação).</span><span class="sxs-lookup"><span data-stu-id="0cf01-140">In WPF and when targeting [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use XAML 2009 features together with `x:TypeArguments` but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="0cf01-141">Compilado por marcação XAML para WPF e o formato BAML de XAML têm suporte no momento, as palavras-chave do XAML 2009 e os recursos.</span><span class="sxs-lookup"><span data-stu-id="0cf01-141">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span> <span data-ttu-id="0cf01-142">Se você precisa para marcação de compilar o XAML, você deve operar sob as restrições na seção "XAML 2006 and genérico XAML usos do WPF".</span><span class="sxs-lookup"><span data-stu-id="0cf01-142">If you need to markup compile the XAML, you must operate under the restrictions noted in the "XAML 2006 and WPF Generic XAML Usages" section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cf01-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0cf01-143">See Also</span></span>  
 [<span data-ttu-id="0cf01-144">Diretiva x:Class</span><span class="sxs-lookup"><span data-stu-id="0cf01-144">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="0cf01-145">Extensão de marcação x:Type</span><span class="sxs-lookup"><span data-stu-id="0cf01-145">x:Type Markup Extension</span></span>](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [<span data-ttu-id="0cf01-146">Tipos inseridos para primitivos de linguagem XML comuns</span><span class="sxs-lookup"><span data-stu-id="0cf01-146">Built-in Types for Common XAML Language Primitives</span></span>](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)  
 [<span data-ttu-id="0cf01-147">Genéricos em XAML</span><span class="sxs-lookup"><span data-stu-id="0cf01-147">Generics in XAML</span></span>](../../../docs/framework/xaml-services/generics-in-xaml.md)
