---
title: Diretiva x:ClassModifier
ms.date: 03/30/2017
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
ms.openlocfilehash: 5a3bbd1d4d75c84dda741d382c8dd7568dbb474b
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45749896"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="449a1-102">Diretiva x:ClassModifier</span><span class="sxs-lookup"><span data-stu-id="449a1-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="449a1-103">Modifica o comportamento de compilação XAML quando `x:Class` também é fornecido.</span><span class="sxs-lookup"><span data-stu-id="449a1-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="449a1-104">Especificamente, em vez de criar um parcial `class` que tem um `Public` (o padrão), do nível de acesso fornecido `x:Class` é criada com um `NotPublic` nível de acesso.</span><span class="sxs-lookup"><span data-stu-id="449a1-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="449a1-105">Esse comportamento afeta o nível de acesso para a classe em que os assemblies gerados.</span><span class="sxs-lookup"><span data-stu-id="449a1-105">This behavior affects the access level for the class in the generated assemblies.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="449a1-106">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="449a1-106">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="449a1-107">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="449a1-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="449a1-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="449a1-108">*NotPublic*</span></span>|<span data-ttu-id="449a1-109">A cadeia de caracteres exata para passar para especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varia, dependendo da linguagem de programação de lógica que você usar.</span><span class="sxs-lookup"><span data-stu-id="449a1-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="449a1-110">Consulte Observações.</span><span class="sxs-lookup"><span data-stu-id="449a1-110">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="449a1-111">Dependências</span><span class="sxs-lookup"><span data-stu-id="449a1-111">Dependencies</span></span>  
 <span data-ttu-id="449a1-112">[X:Class](../../../docs/framework/xaml-services/x-class-directive.md) também deve ser fornecido no mesmo elemento, e esse elemento deve ser o elemento raiz em uma página.</span><span class="sxs-lookup"><span data-stu-id="449a1-112">[x:Class](../../../docs/framework/xaml-services/x-class-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="449a1-113">Para obter mais informações, consulte [ \[MS-XAML\] seção 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="449a1-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="449a1-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="449a1-114">Remarks</span></span>  
 <span data-ttu-id="449a1-115">O valor de `x:ClassModifier` nos serviços de XAML do .NET Framework uso varia de acordo com a linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="449a1-115">The value of `x:ClassModifier` in .NET Framework XAML Services usage varies by programming language.</span></span> <span data-ttu-id="449a1-116">A cadeia de caracteres a ser usado depende de como cada linguagem implementa sua <xref:System.CodeDom.Compiler.CodeDomProvider> e os conversores de tipo, ele retorna para definir os significados para <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> e <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, e se esse idioma é diferencia maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="449a1-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
-   <span data-ttu-id="449a1-117">Para c#, a cadeia de caracteres para passar para designar <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> é `internal`.</span><span class="sxs-lookup"><span data-stu-id="449a1-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>  
  
-   <span data-ttu-id="449a1-118">Para o Microsoft Visual Basic .NET, a cadeia de caracteres para passar para designar <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> é `Friend`.</span><span class="sxs-lookup"><span data-stu-id="449a1-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>  
  
-   <span data-ttu-id="449a1-119">Para [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], nenhum destino existe que dão suporte à compilação de XAML; portanto, o valor passado não está especificado.</span><span class="sxs-lookup"><span data-stu-id="449a1-119">For [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>  
  
 <span data-ttu-id="449a1-120">Você também pode especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` em c#, `Public` no Visual Basic); no entanto, especificando <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> raramente é feito porque <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> já é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="449a1-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>  
  
 <span data-ttu-id="449a1-121">Outros valores com o código de usuário equivalente nível de acesso restrições, como `private` em c#, não são relevantes `x:ClassModifier` porque não há suporte para referências de classe aninhada em XAML e, portanto, o <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modificador tem o mesmo efeito.</span><span class="sxs-lookup"><span data-stu-id="449a1-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>  
  
## <a name="security-notes"></a><span data-ttu-id="449a1-122">Observações sobre segurança</span><span class="sxs-lookup"><span data-stu-id="449a1-122">Security Notes</span></span>  
 <span data-ttu-id="449a1-123">O nível de acesso, como declarado na `x:ClassModifier` ainda está sujeito à interpretação de determinadas estruturas e seus recursos.</span><span class="sxs-lookup"><span data-stu-id="449a1-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="449a1-124">O WPF inclui recursos para carregar e instanciar tipos em que `x:ClassModifier` é `internal`, se essa classe é referenciada em um recurso WPF por meio de um pacote de referência de URI.</span><span class="sxs-lookup"><span data-stu-id="449a1-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="449a1-125">Como consequência neste caso e potencialmente outras como ela é implementada por outras estruturas, não dependa exclusivamente nas `x:ClassModifier` para bloquear a instanciação de todos os possíveis tentativas.</span><span class="sxs-lookup"><span data-stu-id="449a1-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="449a1-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="449a1-126">See Also</span></span>  
 [<span data-ttu-id="449a1-127">Diretiva x:Class</span><span class="sxs-lookup"><span data-stu-id="449a1-127">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="449a1-128">Code-behind e XAML no WPF</span><span class="sxs-lookup"><span data-stu-id="449a1-128">Code-Behind and XAML in WPF</span></span>](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [<span data-ttu-id="449a1-129">Diretiva x:FieldModifier</span><span class="sxs-lookup"><span data-stu-id="449a1-129">x:FieldModifier Directive</span></span>](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)  
 [<span data-ttu-id="449a1-130">Segurança (WPF)</span><span class="sxs-lookup"><span data-stu-id="449a1-130">Security (WPF)</span></span>](../../../docs/framework/wpf/security-wpf.md)  
 [<span data-ttu-id="449a1-131">Tipos migrados do WPF para System.Xaml</span><span class="sxs-lookup"><span data-stu-id="449a1-131">Types Migrated from WPF to System.Xaml</span></span>](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
