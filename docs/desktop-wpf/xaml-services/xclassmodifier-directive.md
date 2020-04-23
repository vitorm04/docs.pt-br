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
ms.openlocfilehash: 436204774c2d59b43a77865c666aed702f7681db
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072028"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="6298c-102">Diretiva x:ClassModifier</span><span class="sxs-lookup"><span data-stu-id="6298c-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="6298c-103">Modifica o comportamento de `x:Class` compilação XAML quando também é fornecida.</span><span class="sxs-lookup"><span data-stu-id="6298c-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="6298c-104">Especificamente, em vez `class` de criar `Public` uma parcial que tenha `x:Class` um nível de `NotPublic` acesso (o padrão), o fornecido é criado com um nível de acesso.</span><span class="sxs-lookup"><span data-stu-id="6298c-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="6298c-105">Esse comportamento afeta o nível de acesso da classe nas assembléias geradas.</span><span class="sxs-lookup"><span data-stu-id="6298c-105">This behavior affects the access level for the class in the generated assemblies.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="6298c-106">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="6298c-106">XAML Attribute Usage</span></span>

```xaml
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">
   ...
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="6298c-107">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="6298c-107">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="6298c-108">*Notpublic*</span><span class="sxs-lookup"><span data-stu-id="6298c-108">*NotPublic*</span></span>|<span data-ttu-id="6298c-109">A seqüência exata <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> a ser aprovada para especificar versus varia, dependendo da linguagem de programação por trás do código que você usa.</span><span class="sxs-lookup"><span data-stu-id="6298c-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="6298c-110">Consulte Observações.</span><span class="sxs-lookup"><span data-stu-id="6298c-110">See Remarks.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="6298c-111">Dependências</span><span class="sxs-lookup"><span data-stu-id="6298c-111">Dependencies</span></span>

<span data-ttu-id="6298c-112">[x:A classe](xclass-directive.md) também deve ser fornecida no mesmo elemento, e esse elemento deve ser o elemento raiz em uma página.</span><span class="sxs-lookup"><span data-stu-id="6298c-112">[x:Class](xclass-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="6298c-113">Para obter mais informações, consulte [ \[\] MS-XAML Seção 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="6298c-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="remarks"></a><span data-ttu-id="6298c-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="6298c-114">Remarks</span></span>

<span data-ttu-id="6298c-115">O valor `x:ClassModifier` do uso do .NET XAML Services varia de acordo com a linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="6298c-115">The value of `x:ClassModifier` in .NET XAML Services usage varies by programming language.</span></span> <span data-ttu-id="6298c-116">A seqüência de string a ser <xref:System.CodeDom.Compiler.CodeDomProvider> usada depende de como cada idioma <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> implementa o seu e os conversores do tipo que ele retorna para definir os significados para e <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, e se essa linguagem é sensível a casos.</span><span class="sxs-lookup"><span data-stu-id="6298c-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>

- <span data-ttu-id="6298c-117">Para C#, a string <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> para `internal`passar para designar é .</span><span class="sxs-lookup"><span data-stu-id="6298c-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>

- <span data-ttu-id="6298c-118">Para o Microsoft Visual Basic .NET, <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> `Friend`a seqüência de transferências para designar é .</span><span class="sxs-lookup"><span data-stu-id="6298c-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>

- <span data-ttu-id="6298c-119">Para C++/CLI, não existem alvos que suportem a compilação do XAML; portanto, o valor para passar não é especificado.</span><span class="sxs-lookup"><span data-stu-id="6298c-119">For C++/CLI, no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>

<span data-ttu-id="6298c-120">Você também <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> pode`public` especificar `Public` (em C#, no Visual Basic); no entanto, especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> é <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> pouco feito porque já é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="6298c-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>

<span data-ttu-id="6298c-121">Outros valores com restrições equivalentes ao `private` nível de acesso ao `x:ClassModifier` código do usuário, como em C#, não são <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> relevantes porque as referências de classe aninhadas não são suportadas em XAML e, portanto, o modificador tem o mesmo efeito.</span><span class="sxs-lookup"><span data-stu-id="6298c-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>

## <a name="security-notes"></a><span data-ttu-id="6298c-122">Observações sobre segurança</span><span class="sxs-lookup"><span data-stu-id="6298c-122">Security Notes</span></span>

<span data-ttu-id="6298c-123">O nível de acesso `x:ClassModifier` declarado ainda está sujeito à interpretação por estruturas particulares e suas capacidades.</span><span class="sxs-lookup"><span data-stu-id="6298c-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="6298c-124">O WPF inclui recursos para carregar `x:ClassModifier` e `internal`instanciar tipos onde está, se essa classe for referenciada a partir de um recurso WPF através de uma referência URI de pacote.</span><span class="sxs-lookup"><span data-stu-id="6298c-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="6298c-125">Como consequência deste caso e potencialmente outros como ele implementado por `x:ClassModifier` outros quadros, não dependem exclusivamente de bloquear todas as tentativas de instanciação possíveis.</span><span class="sxs-lookup"><span data-stu-id="6298c-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>

## <a name="see-also"></a><span data-ttu-id="6298c-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="6298c-126">See also</span></span>

- [<span data-ttu-id="6298c-127">Diretiva x:Class</span><span class="sxs-lookup"><span data-stu-id="6298c-127">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="6298c-128">Code-behind e XAML no WPF</span><span class="sxs-lookup"><span data-stu-id="6298c-128">Code-Behind and XAML in WPF</span></span>](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="6298c-129">Diretiva x:FieldModifier</span><span class="sxs-lookup"><span data-stu-id="6298c-129">x:FieldModifier Directive</span></span>](xfieldmodifier-directive.md)
- [<span data-ttu-id="6298c-130">Segurança (WPF)</span><span class="sxs-lookup"><span data-stu-id="6298c-130">Security (WPF)</span></span>](../../framework/wpf/security-wpf.md)
- [<span data-ttu-id="6298c-131">Tipos migrados do WPF para System.Xaml</span><span class="sxs-lookup"><span data-stu-id="6298c-131">Types Migrated from WPF to System.Xaml</span></span>](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
