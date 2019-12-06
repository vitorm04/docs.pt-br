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
ms.openlocfilehash: 2e64c716ee85934bf02c016ee408b8e5f612a819
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837188"
---
# <a name="xtypearguments-directive"></a><span data-ttu-id="162aa-102">Diretiva x:TypeArguments</span><span class="sxs-lookup"><span data-stu-id="162aa-102">x:TypeArguments Directive</span></span>
<span data-ttu-id="162aa-103">Passa a restringir os argumentos de tipo de um genérico para o construtor do tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="162aa-103">Passes constraining type arguments of a generic to the constructor of the generic type.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="162aa-104">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="162aa-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="162aa-105">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="162aa-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`object`|<span data-ttu-id="162aa-106">Uma declaração de elemento de objeto de um tipo XAML, que é apoiada por um tipo genérico CLR.</span><span class="sxs-lookup"><span data-stu-id="162aa-106">An object element declaration of a XAML type, which is backed by a CLR generic type.</span></span> <span data-ttu-id="162aa-107">Se `object` se refere a um tipo XAML que não é do namespace XAML padrão, `object` requer um prefixo para indicar o namespace XAML onde `object` existe.</span><span class="sxs-lookup"><span data-stu-id="162aa-107">If `object` refers to a XAML type that is not from the default XAML namespace, `object` requires a prefix to indicate the XAML namespace where `object` exists.</span></span>|  
|`typeString`|<span data-ttu-id="162aa-108">Uma cadeia de caracteres que declara um ou mais nomes de tipo XAML como cadeias de caracteres, que fornece os argumentos de tipo para o tipo genérico CLR.</span><span class="sxs-lookup"><span data-stu-id="162aa-108">A string that declares one or more XAML type names as strings, which supplies the type arguments for the CLR generic type.</span></span> <span data-ttu-id="162aa-109">Consulte comentários para ver as notas de sintaxe adicionais.</span><span class="sxs-lookup"><span data-stu-id="162aa-109">See Remarks for additional syntax notes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="162aa-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="162aa-110">Remarks</span></span>  
 <span data-ttu-id="162aa-111">Na maioria dos casos, os tipos XAML que são usados como um item de informações em uma cadeia de caracteres `typeString` são prefixados.</span><span class="sxs-lookup"><span data-stu-id="162aa-111">In most cases, the XAML types that are used as an information item in a `typeString` string are prefixed.</span></span> <span data-ttu-id="162aa-112">Tipos típicos de restrições genéricas do CLR (por exemplo, <xref:System.Int32> e <xref:System.String>) vêm de bibliotecas de classes base do CLR.</span><span class="sxs-lookup"><span data-stu-id="162aa-112">Typical types of CLR generic constraints (for example, <xref:System.Int32> and <xref:System.String>) come from CLR base class libraries.</span></span> <span data-ttu-id="162aa-113">Essas bibliotecas não são mapeadas para namespaces padrão XAML específicos da estrutura e, portanto, exigem um mapeamento de prefixo para o uso do XAML.</span><span class="sxs-lookup"><span data-stu-id="162aa-113">Those libraries are not mapped to typical framework-specific default XAML namespaces, and therefore, require a prefix mapping for XAML usage.</span></span>  
  
 <span data-ttu-id="162aa-114">Você pode especificar mais de um nome de tipo XAML usando um delimitador de vírgula.</span><span class="sxs-lookup"><span data-stu-id="162aa-114">You can specify more than one XAML type name by using a comma delimiter.</span></span>  
  
 <span data-ttu-id="162aa-115">Se as próprias restrições genéricas usarem tipos genéricos, os argumentos de tipo de restrição aninhada poderão ser contidos por parênteses ().</span><span class="sxs-lookup"><span data-stu-id="162aa-115">If the generic constraints themselves use generic types, the nested constraint type arguments can be contained by parentheses ().</span></span>  
  
 <span data-ttu-id="162aa-116">Observe que essa definição de `x:TypeArguments` é específica para .NET Framework serviços XAML e o uso de backup do CLR.</span><span class="sxs-lookup"><span data-stu-id="162aa-116">Note that this definition of `x:TypeArguments` is specific to .NET Framework XAML Services and using CLR backing.</span></span> <span data-ttu-id="162aa-117">Uma definição de nível de idioma pode ser encontrada em [\[MS-XAML\] seção 5.3.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="162aa-117">A language-level definition can be found in [\[MS-XAML\] Section 5.3.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
## <a name="usage-examples"></a><span data-ttu-id="162aa-118">Exemplos de uso</span><span class="sxs-lookup"><span data-stu-id="162aa-118">Usage Examples</span></span>  
 <span data-ttu-id="162aa-119">Para esses exemplos, suponha que as seguintes definições de namespace XAML sejam declaradas:</span><span class="sxs-lookup"><span data-stu-id="162aa-119">For these examples, assume that the following XAML namespace definitions are declared:</span></span>  
  
```xaml  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a><span data-ttu-id="162aa-120">Listar\<cadeia de caracteres ></span><span class="sxs-lookup"><span data-stu-id="162aa-120">List\<String></span></span>  
 <span data-ttu-id="162aa-121">`<scg:List x:TypeArguments="sys:String" ...>` instancia um novo <xref:System.Collections.Generic.List%601> com um argumento de tipo <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="162aa-121">`<scg:List x:TypeArguments="sys:String" ...>` instantiates a new <xref:System.Collections.Generic.List%601> with a <xref:System.String> type argument.</span></span>  
  
### <a name="dictionarystringstring"></a><span data-ttu-id="162aa-122">\<de cadeia de caracteres de dicionário, Cadeia de caracteres ></span><span class="sxs-lookup"><span data-stu-id="162aa-122">Dictionary\<String,String></span></span>  
 <span data-ttu-id="162aa-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instancia um novo <xref:System.Collections.Generic.Dictionary%602> com dois argumentos de tipo <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="162aa-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instantiates a new <xref:System.Collections.Generic.Dictionary%602> with two <xref:System.String> type arguments.</span></span>  
  
### <a name="queuekeyvaluepairstringstring"></a><span data-ttu-id="162aa-124">Queue < KeyValuePair\<String, Cadeia de caracteres > ></span><span class="sxs-lookup"><span data-stu-id="162aa-124">Queue<KeyValuePair\<String,String>></span></span>  
 <span data-ttu-id="162aa-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instancia uma nova <xref:System.Collections.Generic.Queue%601> que tem uma restrição de <xref:System.Collections.Generic.KeyValuePair%602> com os argumentos de tipo de restrição interna <xref:System.String> e <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="162aa-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instantiates a new <xref:System.Collections.Generic.Queue%601> that has a constraint of <xref:System.Collections.Generic.KeyValuePair%602> with the inner constraint type arguments <xref:System.String> and <xref:System.String>.</span></span>  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a><span data-ttu-id="162aa-126">Usos de XAML genérico XAML 2006 e WPF</span><span class="sxs-lookup"><span data-stu-id="162aa-126">XAML 2006 and WPF Generic XAML Usages</span></span>  
 <span data-ttu-id="162aa-127">Para o uso de XAML 2006 e XAML que é usado para aplicativos do WPF, existem as seguintes restrições para `x:TypeArguments` e usos de tipo genérico do XAML em geral:</span><span class="sxs-lookup"><span data-stu-id="162aa-127">For XAML 2006 usage, and XAML that is used for WPF applications, the following restrictions exist for `x:TypeArguments` and generic type usages from XAML in general:</span></span>  
  
- <span data-ttu-id="162aa-128">Somente o elemento raiz de um arquivo XAML pode dar suporte a um uso de XAML genérico que faz referência a um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="162aa-128">Only the root element of a XAML file can support a generic XAML usage that references a generic type.</span></span>  
  
- <span data-ttu-id="162aa-129">O elemento raiz deve mapear para um tipo genérico com pelo menos um argumento de tipo.</span><span class="sxs-lookup"><span data-stu-id="162aa-129">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="162aa-130">Um exemplo é <xref:System.Windows.Navigation.PageFunction%601>.</span><span class="sxs-lookup"><span data-stu-id="162aa-130">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="162aa-131">As funções de página são o principal cenário para suporte de uso genérico XAML no WPF.</span><span class="sxs-lookup"><span data-stu-id="162aa-131">The page functions are the primary scenario for XAML generic usage support in WPF.</span></span>  
  
- <span data-ttu-id="162aa-132">O elemento de objeto XAML do elemento raiz para o genérico também deve declarar uma classe parcial usando `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="162aa-132">The root element XAML object element for the generic must also declare a partial class using `x:Class`.</span></span> <span data-ttu-id="162aa-133">Isso é verdadeiro mesmo se definir uma ação de compilação do WPF.</span><span class="sxs-lookup"><span data-stu-id="162aa-133">This is true even if defining a WPF build action.</span></span>  
  
- <span data-ttu-id="162aa-134">`x:TypeArguments` não pode referenciar restrições genéricas aninhadas.</span><span class="sxs-lookup"><span data-stu-id="162aa-134">`x:TypeArguments` cannot reference nested generic constraints.</span></span>  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a><span data-ttu-id="162aa-135">XAML 2009 ou XAML 2006 sem nenhuma dependência do WPF 3,0 ou do WPF 3,5</span><span class="sxs-lookup"><span data-stu-id="162aa-135">XAML 2009 or XAML 2006 with No WPF 3.0 or WPF 3.5 Dependency</span></span>  
 <span data-ttu-id="162aa-136">Em .NET Framework serviços XAML para XAML 2006 ou XAML 2009, as restrições relacionadas ao WPF no uso de XAML genérico são relaxadas.</span><span class="sxs-lookup"><span data-stu-id="162aa-136">In .NET Framework XAML Services for either XAML 2006 or XAML 2009, the WPF-related restrictions on generic XAML usage are relaxed.</span></span> <span data-ttu-id="162aa-137">Você pode criar uma instância de um elemento de objeto genérico em qualquer posição na marcação XAML que o sistema de tipo de backup e o modelo de objeto podem dar suporte.</span><span class="sxs-lookup"><span data-stu-id="162aa-137">You can instantiate a generic object element at any position in XAML markup that the backing type system and object model can support.</span></span>  
  
 <span data-ttu-id="162aa-138">Se você usar o XAML 2009 em vez de mapear os tipos de base do CLR para obter tipos XAML para primitivos de linguagem comum, poderá usar [tipos internos para primitivos comuns de linguagem XAML](built-in-types-for-common-xaml-language-primitives.md) como itens de informações em um `typeString`.</span><span class="sxs-lookup"><span data-stu-id="162aa-138">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [Built-in Types for Common XAML Language Primitives](built-in-types-for-common-xaml-language-primitives.md) as information items in a `typeString`.</span></span> <span data-ttu-id="162aa-139">Por exemplo, você pode declarar o seguinte (mapeamentos de prefixo não mostrados, mas x é o namespace XAML da linguagem XAML para XAML 2009):</span><span class="sxs-lookup"><span data-stu-id="162aa-139">For example, you could declare the following (prefix mappings not shown, but x is the XAML language XAML namespace for XAML 2009):</span></span>  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 <span data-ttu-id="162aa-140">No WPF e, ao direcionar .NET Framework 4, você pode usar os recursos do XAML 2009 juntamente com `x:TypeArguments`, mas apenas para XAML livre (XAML que não é compilado por marcação).</span><span class="sxs-lookup"><span data-stu-id="162aa-140">In WPF and when targeting .NET Framework 4, you can use XAML 2009 features together with `x:TypeArguments` but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="162aa-141">O XAML com compilação de marcação para WPF e a forma de BAML do XAML atualmente não dão suporte às palavras-chave e aos recursos do XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="162aa-141">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span> <span data-ttu-id="162aa-142">Se você precisar compilar a marcação do XAML, você deve operar sob as restrições indicadas na seção "XAML 2006 e usos genéricos XAML do WPF".</span><span class="sxs-lookup"><span data-stu-id="162aa-142">If you need to markup compile the XAML, you must operate under the restrictions noted in the "XAML 2006 and WPF Generic XAML Usages" section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="162aa-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="162aa-143">See also</span></span>

- [<span data-ttu-id="162aa-144">Diretiva x:Class</span><span class="sxs-lookup"><span data-stu-id="162aa-144">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="162aa-145">Extensão de marcação x:Type</span><span class="sxs-lookup"><span data-stu-id="162aa-145">x:Type Markup Extension</span></span>](x-type-markup-extension.md)
- [<span data-ttu-id="162aa-146">Tipos inseridos para primitivos de linguagem XML comuns</span><span class="sxs-lookup"><span data-stu-id="162aa-146">Built-in Types for Common XAML Language Primitives</span></span>](built-in-types-for-common-xaml-language-primitives.md)
- [<span data-ttu-id="162aa-147">Genéricos em XAML</span><span class="sxs-lookup"><span data-stu-id="162aa-147">Generics in XAML</span></span>](generics-in-xaml.md)
