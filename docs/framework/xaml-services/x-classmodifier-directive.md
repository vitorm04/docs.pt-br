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
ms.openlocfilehash: c3c08f61b49a6367663cf02099dda86d1a692284
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484755"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="35c46-102">Diretiva x:ClassModifier</span><span class="sxs-lookup"><span data-stu-id="35c46-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="35c46-103">Modifica o comportamento de compilação XAML `x:Class` quando também é fornecido.</span><span class="sxs-lookup"><span data-stu-id="35c46-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="35c46-104">Especificamente, em vez de criar um `class` parcial que tenha `Public` um nível de acesso (o padrão), `x:Class` o fornecido é criado `NotPublic` com um nível de acesso.</span><span class="sxs-lookup"><span data-stu-id="35c46-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="35c46-105">Esse comportamento afeta o nível de acesso para a classe nos assemblies gerados.</span><span class="sxs-lookup"><span data-stu-id="35c46-105">This behavior affects the access level for the class in the generated assemblies.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="35c46-106">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="35c46-106">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="35c46-107">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="35c46-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="35c46-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="35c46-108">*NotPublic*</span></span>|<span data-ttu-id="35c46-109">A cadeia de caracteres exata a ser <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> passada <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> para especificar versus varia, dependendo da linguagem de programação code-behind que você usa.</span><span class="sxs-lookup"><span data-stu-id="35c46-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="35c46-110">Consulte Observações.</span><span class="sxs-lookup"><span data-stu-id="35c46-110">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="35c46-111">Dependências</span><span class="sxs-lookup"><span data-stu-id="35c46-111">Dependencies</span></span>  
 <span data-ttu-id="35c46-112">[x:Class](x-class-directive.md) também deve ser fornecida no mesmo elemento, e esse elemento deve ser o elemento raiz em uma página.</span><span class="sxs-lookup"><span data-stu-id="35c46-112">[x:Class](x-class-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="35c46-113">Para obter mais informações, consulte [ \[a seção\] MS-XAML 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="35c46-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35c46-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="35c46-114">Remarks</span></span>  
 <span data-ttu-id="35c46-115">O valor de `x:ClassModifier` no .NET Framework uso de serviços XAML varia de acordo com a linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="35c46-115">The value of `x:ClassModifier` in .NET Framework XAML Services usage varies by programming language.</span></span> <span data-ttu-id="35c46-116">A cadeia de caracteres a ser usada depende de como cada <xref:System.CodeDom.Compiler.CodeDomProvider> idioma implementa seu e os conversores de tipo que ele retorna para <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> definir <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>os significados para e e se esse idioma diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="35c46-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
- <span data-ttu-id="35c46-117">Para C#, a cadeia de caracteres a ser passada <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> para `internal`designar é.</span><span class="sxs-lookup"><span data-stu-id="35c46-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>  
  
- <span data-ttu-id="35c46-118">Para o Microsoft Visual Basic .net, a cadeia de caracteres a ser <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> passada `Friend`para designar é.</span><span class="sxs-lookup"><span data-stu-id="35c46-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>  
  
- <span data-ttu-id="35c46-119">Para C++/CLI, não existem destinos que dão suporte à compilação de XAML; Portanto, o valor a ser passado não é especificado.</span><span class="sxs-lookup"><span data-stu-id="35c46-119">For C++/CLI, no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>  
  
 <span data-ttu-id="35c46-120">Você também pode especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); no entanto <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> , a especificação é feita <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> com pouca frequência porque já é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="35c46-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>  
  
 <span data-ttu-id="35c46-121">Outros valores com restrições de nível `private` de acesso do código do usuário equivalentes, como no C#, não `x:ClassModifier` são relevantes para o porque não há suporte para referências de classe aninhadas <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> em XAML e, portanto, o modificador tem o mesmo efeito .</span><span class="sxs-lookup"><span data-stu-id="35c46-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>  
  
## <a name="security-notes"></a><span data-ttu-id="35c46-122">Observações de segurança</span><span class="sxs-lookup"><span data-stu-id="35c46-122">Security Notes</span></span>  
 <span data-ttu-id="35c46-123">O nível de acesso como declarado `x:ClassModifier` em ainda está sujeito à interpretação por estruturas específicas e seus recursos.</span><span class="sxs-lookup"><span data-stu-id="35c46-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="35c46-124">O WPF inclui recursos para carregar e criar uma `x:ClassModifier` instância `internal`de tipos onde está, se essa classe for referenciada de um recurso do WPF por meio de uma referência de URI pack.</span><span class="sxs-lookup"><span data-stu-id="35c46-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="35c46-125">Como consequência desse caso e, potencialmente, outras pessoas, como as implementadas por outras estruturas, não `x:ClassModifier` se baseiam exclusivamente para bloquear todas as possíveis tentativas de instanciação.</span><span class="sxs-lookup"><span data-stu-id="35c46-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35c46-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35c46-126">See also</span></span>

- [<span data-ttu-id="35c46-127">Diretiva x:Class</span><span class="sxs-lookup"><span data-stu-id="35c46-127">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="35c46-128">Code-behind e XAML no WPF</span><span class="sxs-lookup"><span data-stu-id="35c46-128">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="35c46-129">Diretiva x:FieldModifier</span><span class="sxs-lookup"><span data-stu-id="35c46-129">x:FieldModifier Directive</span></span>](x-fieldmodifier-directive.md)
- [<span data-ttu-id="35c46-130">Segurança (WPF)</span><span class="sxs-lookup"><span data-stu-id="35c46-130">Security (WPF)</span></span>](../wpf/security-wpf.md)
- [<span data-ttu-id="35c46-131">Tipos migrados do WPF para System.Xaml</span><span class="sxs-lookup"><span data-stu-id="35c46-131">Types Migrated from WPF to System.Xaml</span></span>](types-migrated-from-wpf-to-system-xaml.md)
