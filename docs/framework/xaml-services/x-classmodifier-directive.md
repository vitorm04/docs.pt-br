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
ms.openlocfilehash: 67b53a63dbd6e1377d5684d64ed32b0374c84b5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564372"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="6cc41-102">Diretiva x:ClassModifier</span><span class="sxs-lookup"><span data-stu-id="6cc41-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="6cc41-103">Modifica o comportamento de compilação XAML quando `x:Class` também é fornecido.</span><span class="sxs-lookup"><span data-stu-id="6cc41-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="6cc41-104">Especificamente, em vez de criar um parcial `class` que tem um `Public` (o padrão), do nível de acesso fornecido `x:Class` é criada com um `NotPublic` nível de acesso.</span><span class="sxs-lookup"><span data-stu-id="6cc41-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="6cc41-105">Esse comportamento afeta o nível de acesso para a classe no assembly gerado.</span><span class="sxs-lookup"><span data-stu-id="6cc41-105">This behavior affects the access level for the class in the generated assemblies.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="6cc41-106">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="6cc41-106">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="6cc41-107">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="6cc41-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6cc41-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="6cc41-108">*NotPublic*</span></span>|<span data-ttu-id="6cc41-109">A cadeia de caracteres exata para passar para especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varia, dependendo da linguagem de programação por trás do código que você usa.</span><span class="sxs-lookup"><span data-stu-id="6cc41-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="6cc41-110">Consulte Observações.</span><span class="sxs-lookup"><span data-stu-id="6cc41-110">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="6cc41-111">Dependências</span><span class="sxs-lookup"><span data-stu-id="6cc41-111">Dependencies</span></span>  
 <span data-ttu-id="6cc41-112">[X:Class](../../../docs/framework/xaml-services/x-class-directive.md) também deve ser fornecido no mesmo elemento, e esse elemento deve ser o elemento raiz em uma página.</span><span class="sxs-lookup"><span data-stu-id="6cc41-112">[x:Class](../../../docs/framework/xaml-services/x-class-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="6cc41-113">Para obter mais informações, consulte [ \[XAML MS\] seção 4.3.1.8](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="6cc41-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cc41-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="6cc41-114">Remarks</span></span>  
 <span data-ttu-id="6cc41-115">O valor de `x:ClassModifier` em serviços XAML do .NET Framework uso varia de acordo com a linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="6cc41-115">The value of `x:ClassModifier` in .NET Framework XAML Services usage varies by programming language.</span></span> <span data-ttu-id="6cc41-116">A cadeia de caracteres a ser usado depende de como cada linguagem implementa seu <xref:System.CodeDom.Compiler.CodeDomProvider> e conversores de tipo que ele retorna para definir os significados de <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> e <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, e se o idioma diferencia maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="6cc41-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
-   <span data-ttu-id="6cc41-117">Para c#, a cadeia de caracteres para passar para designar <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> é `internal`.</span><span class="sxs-lookup"><span data-stu-id="6cc41-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>  
  
-   <span data-ttu-id="6cc41-118">Para o Microsoft Visual Basic .NET, a cadeia de caracteres para passar para designar <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> é `Friend`.</span><span class="sxs-lookup"><span data-stu-id="6cc41-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>  
  
-   <span data-ttu-id="6cc41-119">Para [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], nenhum destino existe que dão suporte a compilação XAML; portanto, o valor passado for especificado.</span><span class="sxs-lookup"><span data-stu-id="6cc41-119">For [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>  
  
 <span data-ttu-id="6cc41-120">Você também pode especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` em c#, `Public` no Visual Basic); no entanto, especificando <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> raramente é feito porque <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> já é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="6cc41-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>  
  
 <span data-ttu-id="6cc41-121">Outros valores com o código de usuário equivalente nível de acesso restrições, como `private` em c#, não são relevantes para `x:ClassModifier` porque não há suporte para referências de classe aninhada em XAML e, portanto, o <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modificador tem o mesmo efeito.</span><span class="sxs-lookup"><span data-stu-id="6cc41-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>  
  
## <a name="security-notes"></a><span data-ttu-id="6cc41-122">Observações de segurança</span><span class="sxs-lookup"><span data-stu-id="6cc41-122">Security Notes</span></span>  
 <span data-ttu-id="6cc41-123">O nível de acesso conforme declarado em `x:ClassModifier` ainda está sujeito a interpretação de determinadas estruturas e seus recursos.</span><span class="sxs-lookup"><span data-stu-id="6cc41-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="6cc41-124">WPF inclui recursos para carregar e instanciar tipos onde `x:ClassModifier` é `internal`, se essa classe é referenciada em um recurso do WPF por meio de um referência URI de pacote.</span><span class="sxs-lookup"><span data-stu-id="6cc41-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="6cc41-125">Como consequência neste caso e possivelmente outros como ele é implementado por outras estruturas, não confie exclusivamente em `x:ClassModifier` para bloquear todas as possíveis instanciação tentativas.</span><span class="sxs-lookup"><span data-stu-id="6cc41-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cc41-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6cc41-126">See Also</span></span>  
 [<span data-ttu-id="6cc41-127">Diretiva x:Class</span><span class="sxs-lookup"><span data-stu-id="6cc41-127">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="6cc41-128">Code-behind e XAML no WPF</span><span class="sxs-lookup"><span data-stu-id="6cc41-128">Code-Behind and XAML in WPF</span></span>](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [<span data-ttu-id="6cc41-129">Diretiva x:FieldModifier</span><span class="sxs-lookup"><span data-stu-id="6cc41-129">x:FieldModifier Directive</span></span>](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)  
 [<span data-ttu-id="6cc41-130">Segurança (WPF)</span><span class="sxs-lookup"><span data-stu-id="6cc41-130">Security (WPF)</span></span>](../../../docs/framework/wpf/security-wpf.md)  
 [<span data-ttu-id="6cc41-131">Tipos migrados do WPF para System.Xaml</span><span class="sxs-lookup"><span data-stu-id="6cc41-131">Types Migrated from WPF to System.Xaml</span></span>](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
