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
ms.openlocfilehash: 73732a06029cca3a4c6c6d82762d5263c5b8c955
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544811"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="db141-102">Diretiva x:ClassModifier</span><span class="sxs-lookup"><span data-stu-id="db141-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="db141-103">Modifica o comportamento de compilação XAML quando `x:Class` também é fornecido.</span><span class="sxs-lookup"><span data-stu-id="db141-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="db141-104">Especificamente, em vez de criar um parcial `class` que tenha um `Public` nível de acesso (o padrão), o fornecido `x:Class` é criado com um nível de `NotPublic` acesso.</span><span class="sxs-lookup"><span data-stu-id="db141-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="db141-105">Esse comportamento afeta o nível de acesso para a classe nos assemblies gerados.</span><span class="sxs-lookup"><span data-stu-id="db141-105">This behavior affects the access level for the class in the generated assemblies.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="db141-106">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="db141-106">XAML Attribute Usage</span></span>

```xaml
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">
   ...
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="db141-107">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="db141-107">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="db141-108">*Não público*</span><span class="sxs-lookup"><span data-stu-id="db141-108">*NotPublic*</span></span>|<span data-ttu-id="db141-109">A cadeia de caracteres exata a ser passada para especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varia, dependendo da linguagem de programação code-behind que você usa.</span><span class="sxs-lookup"><span data-stu-id="db141-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="db141-110">Consulte Observações.</span><span class="sxs-lookup"><span data-stu-id="db141-110">See Remarks.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="db141-111">Dependências</span><span class="sxs-lookup"><span data-stu-id="db141-111">Dependencies</span></span>

<span data-ttu-id="db141-112">[x:Class](xclass-directive.md) também deve ser fornecida no mesmo elemento, e esse elemento deve ser o elemento raiz em uma página.</span><span class="sxs-lookup"><span data-stu-id="db141-112">[x:Class](xclass-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="db141-113">Para obter mais informações, consulte [ \[ a \] seção MS-XAML 4.3.1.8](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="db141-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="remarks"></a><span data-ttu-id="db141-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="db141-114">Remarks</span></span>

<span data-ttu-id="db141-115">O valor do `x:ClassModifier` uso dos serviços XAML .NET varia de acordo com a linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="db141-115">The value of `x:ClassModifier` in .NET XAML Services usage varies by programming language.</span></span> <span data-ttu-id="db141-116">A cadeia de caracteres a ser usada depende de como cada idioma implementa seu <xref:System.CodeDom.Compiler.CodeDomProvider> e os conversores de tipo que ele retorna para definir os significados para <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> e e <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> se esse idioma diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="db141-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>

- <span data-ttu-id="db141-117">Para o C#, a cadeia de caracteres a ser passada para designar <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> é `internal` .</span><span class="sxs-lookup"><span data-stu-id="db141-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>

- <span data-ttu-id="db141-118">Para o Microsoft Visual Basic .NET, a cadeia de caracteres a ser passada para designar <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> é `Friend` .</span><span class="sxs-lookup"><span data-stu-id="db141-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>

- <span data-ttu-id="db141-119">Para C++/CLI, não existem destinos que dão suporte à compilação de XAML; Portanto, o valor a ser passado não é especificado.</span><span class="sxs-lookup"><span data-stu-id="db141-119">For C++/CLI, no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>

<span data-ttu-id="db141-120">Você também pode especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> ( `public` em C#, `Public` em Visual Basic); no entanto, a especificação <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> é feita com pouca frequência porque <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> já é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="db141-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>

<span data-ttu-id="db141-121">Outros valores com restrições de nível de acesso do código do usuário equivalentes, como `private` em C#, não são relevantes para o `x:ClassModifier` porque não há suporte para referências de classe aninhadas em XAML e, portanto, o <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modificador tem o mesmo efeito.</span><span class="sxs-lookup"><span data-stu-id="db141-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>

## <a name="security-notes"></a><span data-ttu-id="db141-122">Observações sobre segurança</span><span class="sxs-lookup"><span data-stu-id="db141-122">Security Notes</span></span>

<span data-ttu-id="db141-123">O nível de acesso como declarado em `x:ClassModifier` ainda está sujeito à interpretação por estruturas específicas e seus recursos.</span><span class="sxs-lookup"><span data-stu-id="db141-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="db141-124">O WPF inclui recursos para carregar e criar uma instância de tipos onde `x:ClassModifier` está `internal` , se essa classe for referenciada de um recurso do WPF por meio de uma referência de URI pack.</span><span class="sxs-lookup"><span data-stu-id="db141-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="db141-125">Como consequência desse caso e, potencialmente, outras pessoas, como as implementadas por outras estruturas, não se baseiam exclusivamente `x:ClassModifier` para bloquear todas as possíveis tentativas de instanciação.</span><span class="sxs-lookup"><span data-stu-id="db141-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>

## <a name="see-also"></a><span data-ttu-id="db141-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="db141-126">See also</span></span>

- [<span data-ttu-id="db141-127">Diretiva x:Class</span><span class="sxs-lookup"><span data-stu-id="db141-127">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="db141-128">Code-behind e XAML no WPF</span><span class="sxs-lookup"><span data-stu-id="db141-128">Code-Behind and XAML in WPF</span></span>](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf)
- [<span data-ttu-id="db141-129">Diretiva x:FieldModifier</span><span class="sxs-lookup"><span data-stu-id="db141-129">x:FieldModifier Directive</span></span>](xfieldmodifier-directive.md)
- [<span data-ttu-id="db141-130">Segurança (WPF)</span><span class="sxs-lookup"><span data-stu-id="db141-130">Security (WPF)</span></span>](/dotnet/desktop/wpf/security-wpf)
- [<span data-ttu-id="db141-131">Tipos migrados do WPF para System.Xaml</span><span class="sxs-lookup"><span data-stu-id="db141-131">Types Migrated from WPF to System.Xaml</span></span>](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
