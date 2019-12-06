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
ms.openlocfilehash: a24277a4d5fbc4870157b6c8ba00ba71ba61e656
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837227"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="c9dfe-102">Diretiva x:ClassModifier</span><span class="sxs-lookup"><span data-stu-id="c9dfe-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="c9dfe-103">Modifica o comportamento de compilação XAML quando `x:Class` também é fornecido.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="c9dfe-104">Especificamente, em vez de criar um `class` parcial que tenha um nível de acesso de `Public` (o padrão), o `x:Class` fornecido é criado com um nível de acesso `NotPublic`.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="c9dfe-105">Esse comportamento afeta o nível de acesso para a classe nos assemblies gerados.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-105">This behavior affects the access level for the class in the generated assemblies.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="c9dfe-106">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="c9dfe-106">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="c9dfe-107">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="c9dfe-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c9dfe-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="c9dfe-108">*NotPublic*</span></span>|<span data-ttu-id="c9dfe-109">A cadeia de caracteres exata a ser passada para especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varia, dependendo da linguagem de programação code-behind usada.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="c9dfe-110">Consulte Observações.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-110">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="c9dfe-111">Dependências</span><span class="sxs-lookup"><span data-stu-id="c9dfe-111">Dependencies</span></span>  
 <span data-ttu-id="c9dfe-112">[x:Class](x-class-directive.md) também deve ser fornecida no mesmo elemento, e esse elemento deve ser o elemento raiz em uma página.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-112">[x:Class](x-class-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="c9dfe-113">Para obter mais informações, consulte [\[MS-XAML\] seção 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="c9dfe-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9dfe-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9dfe-114">Remarks</span></span>  
 <span data-ttu-id="c9dfe-115">O valor de `x:ClassModifier` no uso de serviços XAML .NET Framework varia de acordo com a linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-115">The value of `x:ClassModifier` in .NET Framework XAML Services usage varies by programming language.</span></span> <span data-ttu-id="c9dfe-116">A cadeia de caracteres a ser usada depende de como cada idioma implementa sua <xref:System.CodeDom.Compiler.CodeDomProvider> e os conversores de tipo que ele retorna para definir os significados para <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> e <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>e se esse idioma diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
- <span data-ttu-id="c9dfe-117">Para C#, a cadeia de caracteres a ser passada para designar <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> é `internal`.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>  
  
- <span data-ttu-id="c9dfe-118">Para o Microsoft Visual Basic .NET, a cadeia de caracteres a ser passada para designar <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> é `Friend`.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>  
  
- <span data-ttu-id="c9dfe-119">Para C++/CLI, não existem destinos que dão suporte à compilação de XAML; Portanto, o valor a ser passado não é especificado.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-119">For C++/CLI, no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>  
  
 <span data-ttu-id="c9dfe-120">Você também pode especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` no C#`Public` Visual Basic); no entanto, a especificação de <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> é feita com pouca frequência porque <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> já é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>  
  
 <span data-ttu-id="c9dfe-121">Outros valores com restrições de nível de acesso do código do usuário equivalentes, C#como `private` no, não são relevantes para `x:ClassModifier` porque não há suporte para referências de classes aninhadas em XAML e, portanto, o modificador de <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> tem o mesmo efeito.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>  
  
## <a name="security-notes"></a><span data-ttu-id="c9dfe-122">Observações sobre segurança</span><span class="sxs-lookup"><span data-stu-id="c9dfe-122">Security Notes</span></span>  
 <span data-ttu-id="c9dfe-123">O nível de acesso como declarado em `x:ClassModifier` ainda está sujeito à interpretação por estruturas específicas e seus recursos.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="c9dfe-124">O WPF inclui recursos para carregar e criar uma instância de tipos em que `x:ClassModifier` é `internal`, se essa classe for referenciada de um recurso do WPF por meio de uma referência de URI de pacote.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="c9dfe-125">Como consequência desse caso e, potencialmente, outras pessoas como ela é implementada por outras estruturas, não dependa exclusivamente de `x:ClassModifier` para bloquear todas as possíveis tentativas de instanciação.</span><span class="sxs-lookup"><span data-stu-id="c9dfe-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9dfe-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9dfe-126">See also</span></span>

- [<span data-ttu-id="c9dfe-127">Diretiva x:Class</span><span class="sxs-lookup"><span data-stu-id="c9dfe-127">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="c9dfe-128">Code-behind e XAML no WPF</span><span class="sxs-lookup"><span data-stu-id="c9dfe-128">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="c9dfe-129">Diretiva x:FieldModifier</span><span class="sxs-lookup"><span data-stu-id="c9dfe-129">x:FieldModifier Directive</span></span>](x-fieldmodifier-directive.md)
- [<span data-ttu-id="c9dfe-130">Segurança (WPF)</span><span class="sxs-lookup"><span data-stu-id="c9dfe-130">Security (WPF)</span></span>](../wpf/security-wpf.md)
- [<span data-ttu-id="c9dfe-131">Tipos migrados do WPF para System.Xaml</span><span class="sxs-lookup"><span data-stu-id="c9dfe-131">Types Migrated from WPF to System.Xaml</span></span>](types-migrated-from-wpf-to-system-xaml.md)
