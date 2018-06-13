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
ms.openlocfilehash: 94f09bdd3b6ee0b180e30bab0993f0b4e41730ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566854"
---
# <a name="xtypearguments-directive"></a><span data-ttu-id="55cde-102">Diretiva x:TypeArguments</span><span class="sxs-lookup"><span data-stu-id="55cde-102">x:TypeArguments Directive</span></span>
<span data-ttu-id="55cde-103">Passa para a restrição de tipo de argumentos de um genérico para o construtor do tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="55cde-103">Passes constraining type arguments of a generic to the constructor of the generic type.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="55cde-104">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="55cde-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="55cde-105">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="55cde-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`object`|<span data-ttu-id="55cde-106">Uma declaração de elemento de objeto de um tipo XAML, que é apoiado por um tipo genérico do CLR.</span><span class="sxs-lookup"><span data-stu-id="55cde-106">An object element declaration of a XAML type, which is backed by a CLR generic type.</span></span> <span data-ttu-id="55cde-107">Se `object` se refere a um tipo XAML que não seja o padrão do namespace de XAML, `object` requer um prefixo para indicar o namespace XAML onde `object` existe.</span><span class="sxs-lookup"><span data-stu-id="55cde-107">If `object` refers to a XAML type that is not from the default XAML namespace, `object` requires a prefix to indicate the XAML namespace where `object` exists.</span></span>|  
|`typeString`|<span data-ttu-id="55cde-108">Uma cadeia de caracteres que declara um ou mais XAML Digite nomes como cadeias de caracteres, que fornece os argumentos de tipo para o tipo genérico do CLR.</span><span class="sxs-lookup"><span data-stu-id="55cde-108">A string that declares one or more XAML type names as strings, which supplies the type arguments for the CLR generic type.</span></span> <span data-ttu-id="55cde-109">Consulte comentários para obter notas de sintaxe adicional.</span><span class="sxs-lookup"><span data-stu-id="55cde-109">See Remarks for additional syntax notes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55cde-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="55cde-110">Remarks</span></span>  
 <span data-ttu-id="55cde-111">Na maioria dos casos, os tipos XAML que são usados como um item de informação em um `typeString` cadeia de caracteres são prefixados.</span><span class="sxs-lookup"><span data-stu-id="55cde-111">In most cases, the XAML types that are used as an information item in a `typeString` string are prefixed.</span></span> <span data-ttu-id="55cde-112">Tipos típicos de restrições genéricas do CLR (por exemplo, <xref:System.Int32> e <xref:System.String>) provenientes de bibliotecas de classe base do CLR.</span><span class="sxs-lookup"><span data-stu-id="55cde-112">Typical types of CLR generic constraints (for example, <xref:System.Int32> and <xref:System.String>) come from CLR base class libraries.</span></span> <span data-ttu-id="55cde-113">Essas bibliotecas não são mapeados para típico padrão de específica da estrutura XAML namespaces e, portanto, exigem um mapeamento de prefixo para uso em XAML.</span><span class="sxs-lookup"><span data-stu-id="55cde-113">Those libraries are not mapped to typical framework-specific default XAML namespaces, and therefore, require a prefix mapping for XAML usage.</span></span>  
  
 <span data-ttu-id="55cde-114">Você pode especificar mais de um nome de tipo XAML usando um delimitador de vírgula.</span><span class="sxs-lookup"><span data-stu-id="55cde-114">You can specify more than one XAML type name by using a comma delimiter.</span></span>  
  
 <span data-ttu-id="55cde-115">Se as restrições genéricas se usam tipos genéricos, os argumentos de tipo aninhado de restrição podem ser contidos por parênteses ().</span><span class="sxs-lookup"><span data-stu-id="55cde-115">If the generic constraints themselves use generic types, the nested constraint type arguments can be contained by parentheses ().</span></span>  
  
 <span data-ttu-id="55cde-116">Observe que essa definição de `x:TypeArguments` é específico para serviços XAML do .NET Framework e usando o backup do CLR.</span><span class="sxs-lookup"><span data-stu-id="55cde-116">Note that this definition of `x:TypeArguments` is specific to .NET Framework XAML Services and using CLR backing.</span></span> <span data-ttu-id="55cde-117">Uma definição de nível de linguagem que pode ser encontrada na [ \[XAML MS\] seção 5.3.11](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="55cde-117">A language-level definition can be found in [\[MS-XAML\] Section 5.3.11](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="usage-examples"></a><span data-ttu-id="55cde-118">Exemplos de uso</span><span class="sxs-lookup"><span data-stu-id="55cde-118">Usage Examples</span></span>  
 <span data-ttu-id="55cde-119">Para esses exemplos, suponha que as seguintes definições do namespace XAML são declaradas:</span><span class="sxs-lookup"><span data-stu-id="55cde-119">For these examples, assume that the following XAML namespace definitions are declared:</span></span>  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a><span data-ttu-id="55cde-120">Lista\<cadeia de caracteres ></span><span class="sxs-lookup"><span data-stu-id="55cde-120">List\<String></span></span>  
 <span data-ttu-id="55cde-121">`<scg:List x:TypeArguments="sys:String" ...>` cria um novo <xref:System.Collections.Generic.List%601> com um <xref:System.String> argumento de tipo.</span><span class="sxs-lookup"><span data-stu-id="55cde-121">`<scg:List x:TypeArguments="sys:String" ...>` instantiates a new <xref:System.Collections.Generic.List%601> with a <xref:System.String> type argument.</span></span>  
  
### <a name="dictionarystringstring"></a><span data-ttu-id="55cde-122">Dicionário\<String, String ></span><span class="sxs-lookup"><span data-stu-id="55cde-122">Dictionary\<String,String></span></span>  
 <span data-ttu-id="55cde-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` cria um novo <xref:System.Collections.Generic.Dictionary%602> com dois <xref:System.String> argumentos de tipo.</span><span class="sxs-lookup"><span data-stu-id="55cde-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instantiates a new <xref:System.Collections.Generic.Dictionary%602> with two <xref:System.String> type arguments.</span></span>  
  
### <a name="queuekeyvaluepairstringstring"></a><span data-ttu-id="55cde-124">Fila < KeyValuePair\<cadeia de caracteres, cadeia de caracteres >></span><span class="sxs-lookup"><span data-stu-id="55cde-124">Queue<KeyValuePair\<String,String>></span></span>  
 <span data-ttu-id="55cde-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` cria um novo <xref:System.Collections.Generic.Queue%601> que tem uma restrição de <xref:System.Collections.Generic.KeyValuePair%602> com os argumentos de tipo de restrição interna <xref:System.String> e <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="55cde-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instantiates a new <xref:System.Collections.Generic.Queue%601> that has a constraint of <xref:System.Collections.Generic.KeyValuePair%602> with the inner constraint type arguments <xref:System.String> and <xref:System.String>.</span></span>  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a><span data-ttu-id="55cde-126">Usos XAML genérico 2006 XAML e WPF</span><span class="sxs-lookup"><span data-stu-id="55cde-126">XAML 2006 and WPF Generic XAML Usages</span></span>  
 <span data-ttu-id="55cde-127">Para uso de 2006 XAML e XAML que é usado para aplicativos do WPF, existem as seguintes restrições para `x:TypeArguments` e usos de tipo genérico do XAML em geral:</span><span class="sxs-lookup"><span data-stu-id="55cde-127">For XAML 2006 usage, and XAML that is used for WPF applications, the following restrictions exist for `x:TypeArguments` and generic type usages from XAML in general:</span></span>  
  
-   <span data-ttu-id="55cde-128">Apenas o elemento raiz de um arquivo XAML pode dar suporte a um uso XAML genérico que faz referência a um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="55cde-128">Only the root element of a XAML file can support a generic XAML usage that references a generic type.</span></span>  
  
-   <span data-ttu-id="55cde-129">O elemento raiz deve mapear para um tipo genérico com pelo menos um argumento de tipo.</span><span class="sxs-lookup"><span data-stu-id="55cde-129">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="55cde-130">Um exemplo é <xref:System.Windows.Navigation.PageFunction%601>.</span><span class="sxs-lookup"><span data-stu-id="55cde-130">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="55cde-131">As funções de página são o cenário principal para o suporte de uso genérico de XAML no WPF.</span><span class="sxs-lookup"><span data-stu-id="55cde-131">The page functions are the primary scenario for XAML generic usage support in WPF.</span></span>  
  
-   <span data-ttu-id="55cde-132">O elemento raiz elemento XAML objeto genérica também deverá declarar uma classe parcial usando `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="55cde-132">The root element XAML object element for the generic must also declare a partial class using `x:Class`.</span></span> <span data-ttu-id="55cde-133">Isso é verdadeiro mesmo se a ação de compilação definindo um WPF.</span><span class="sxs-lookup"><span data-stu-id="55cde-133">This is true even if defining a WPF build action.</span></span>  
  
-   <span data-ttu-id="55cde-134">`x:TypeArguments` não é possível fazer referência a restrições genéricas aninhadas.</span><span class="sxs-lookup"><span data-stu-id="55cde-134">`x:TypeArguments` cannot reference nested generic constraints.</span></span>  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a><span data-ttu-id="55cde-135">XAML 2009 ou 2006 de XAML sem WPF 3.0 ou 3.5 do WPF dependência</span><span class="sxs-lookup"><span data-stu-id="55cde-135">XAML 2009 or XAML 2006 with No WPF 3.0 or WPF 3.5 Dependency</span></span>  
 <span data-ttu-id="55cde-136">Em serviços de XAML .NET Framework para 2006 XAML ou XAML 2009, as restrições relacionadas a WPF no uso XAML genérico são reduzidas.</span><span class="sxs-lookup"><span data-stu-id="55cde-136">In .NET Framework XAML Services for either XAML 2006 or XAML 2009, the WPF-related restrictions on generic XAML usage are relaxed.</span></span> <span data-ttu-id="55cde-137">Você pode instanciar um elemento de objeto genérico em qualquer posição na marcação XAML que o modelo de objeto e o sistema de tipo backup pode dar suporte.</span><span class="sxs-lookup"><span data-stu-id="55cde-137">You can instantiate a generic object element at any position in XAML markup that the backing type system and object model can support.</span></span>  
  
 <span data-ttu-id="55cde-138">Se você usar o XAML 2009 em vez de mapeamento do CLR base tipos para obter tipos XAML para primitivos de linguagem comum, você pode usar [tipos internos para primitivos de linguagem XAML comum](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) como itens de informações em um `typeString`.</span><span class="sxs-lookup"><span data-stu-id="55cde-138">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [Built-in Types for Common XAML Language Primitives](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) as information items in a `typeString`.</span></span> <span data-ttu-id="55cde-139">Por exemplo, você pode declarar o seguinte (mapeamentos de prefixo não mostrados, mas x é o namespace XAML linguagem XAML XAML 2009):</span><span class="sxs-lookup"><span data-stu-id="55cde-139">For example, you could declare the following (prefix mappings not shown, but x is the XAML language XAML namespace for XAML 2009):</span></span>  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 <span data-ttu-id="55cde-140">No WPF e direcionamento [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], você pode usar recursos XAML 2009 junto com `x:TypeArguments` , mas apenas para XAML livre (XAML não marcação-compilado).</span><span class="sxs-lookup"><span data-stu-id="55cde-140">In WPF and when targeting [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use XAML 2009 features together with `x:TypeArguments` but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="55cde-141">Compilação de marcação XAML WPF e do formulário BAML do XAML atualmente não dão os recursos e as palavras-chave de XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="55cde-141">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span> <span data-ttu-id="55cde-142">Se você precisa para marcação de compilar o XAML, você deve operam sob as restrições na seção "XAML 2006 e WPF genérica usos de XAML".</span><span class="sxs-lookup"><span data-stu-id="55cde-142">If you need to markup compile the XAML, you must operate under the restrictions noted in the "XAML 2006 and WPF Generic XAML Usages" section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55cde-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55cde-143">See Also</span></span>  
 [<span data-ttu-id="55cde-144">Diretiva x:Class</span><span class="sxs-lookup"><span data-stu-id="55cde-144">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="55cde-145">Extensão de marcação x:Type</span><span class="sxs-lookup"><span data-stu-id="55cde-145">x:Type Markup Extension</span></span>](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [<span data-ttu-id="55cde-146">Tipos inseridos para primitivos de linguagem XML comuns</span><span class="sxs-lookup"><span data-stu-id="55cde-146">Built-in Types for Common XAML Language Primitives</span></span>](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)  
 [<span data-ttu-id="55cde-147">Genéricos em XAML</span><span class="sxs-lookup"><span data-stu-id="55cde-147">Generics in XAML</span></span>](../../../docs/framework/xaml-services/generics-in-xaml.md)
