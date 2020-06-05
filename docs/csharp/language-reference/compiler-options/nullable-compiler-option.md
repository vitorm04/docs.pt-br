---
title: -Nullable (opções do compilador C#)
ms.date: 06/04/2020
f1_keywords:
- /nullable
helpviewer_keywords:
- nullable compiler option [C#]
- /nullable compiler option [C#]
- -nullable compiler option [C#]
ms.openlocfilehash: a68255dba18a022784cd4aaf0027c371893c577b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84449809"
---
# <a name="-nullable-c-compiler-options"></a><span data-ttu-id="94581-102">-Nullable (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="94581-102">-nullable (C# Compiler Options)</span></span>

<span data-ttu-id="94581-103">A opção **-Nullable** permite especificar o contexto anulável desejado.</span><span class="sxs-lookup"><span data-stu-id="94581-103">The **-nullable** option lets you specify the desired nullable context.</span></span>

## <a name="syntax"></a><span data-ttu-id="94581-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94581-104">Syntax</span></span>

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a><span data-ttu-id="94581-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="94581-105">Arguments</span></span>

<span data-ttu-id="94581-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="94581-106">`+` &#124; `-`</span></span>  
<span data-ttu-id="94581-107">Especificar `+` ou apenas **anulável**faz com que o compilador habilite o contexto anulável.</span><span class="sxs-lookup"><span data-stu-id="94581-107">Specifying `+`, or just **-nullable**, causes the compiler to enable nullable context.</span></span> <span data-ttu-id="94581-108">Especificando `-` , que estará em vigor se você não especificar **-Nullable**, desabilitará o contexto anulável.</span><span class="sxs-lookup"><span data-stu-id="94581-108">Specifying `-`, which is in effect if you do not specify **-nullable**, disables nullable context.</span></span>

<span data-ttu-id="94581-109">`enable`&#124; `disable` &#124; `warnings` &#124;`annotations`</span><span class="sxs-lookup"><span data-stu-id="94581-109">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span></span>  
<span data-ttu-id="94581-110">Especifica a opção de contexto anulável.</span><span class="sxs-lookup"><span data-stu-id="94581-110">Specifies the nullable context option.</span></span> <span data-ttu-id="94581-111">Semelhante a `+` ou `-` , para habilitar e desabilitar, mas permite mais granularidade da especificidade de contexto anulável.</span><span class="sxs-lookup"><span data-stu-id="94581-111">Similar to `+` or `-`, to enable and disable, but allows for more granularity of nullable context specificity.</span></span> <span data-ttu-id="94581-112">O `enable` argumento, que está em vigor, como se você especificar **-Nullable**, habilita o contexto anulável.</span><span class="sxs-lookup"><span data-stu-id="94581-112">The `enable` argument, which is in effect the same as if you specify **-nullable**, enables the nullable context.</span></span> <span data-ttu-id="94581-113">Especificar `disable` desabilitará o contexto anulável.</span><span class="sxs-lookup"><span data-stu-id="94581-113">Specifying `disable` will disable nullable context.</span></span> <span data-ttu-id="94581-114">Ao fornecer o `warnings` argumento, **-Nullable: Warnings**, o contexto de aviso anulável é habilitado.</span><span class="sxs-lookup"><span data-stu-id="94581-114">When providing the `warnings` argument, **-nullable:warnings**, the nullable warning context is enabled.</span></span> <span data-ttu-id="94581-115">Ao especificar o `annotations` argumento, **-Nullable: Annotations**, o contexto de anotação anulável é habilitado.</span><span class="sxs-lookup"><span data-stu-id="94581-115">When specifying the `annotations` argument, **-nullable:annotations**, the nullable annotation context is enabled.</span></span>

## <a name="remarks"></a><span data-ttu-id="94581-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="94581-116">Remarks</span></span>

<span data-ttu-id="94581-117">A análise de fluxo é usada para inferir a nulidade das variáveis no código executável.</span><span class="sxs-lookup"><span data-stu-id="94581-117">Flow analysis is used to infer the nullability of variables within executable code.</span></span> <span data-ttu-id="94581-118">A nulidade inferida de uma variável é independente da nulidade declarada da variável.</span><span class="sxs-lookup"><span data-stu-id="94581-118">The inferred nullability of a variable is independent of the variable's declared nullability.</span></span> <span data-ttu-id="94581-119">As chamadas de método são analisadas mesmo quando são omitidas condicionalmente.</span><span class="sxs-lookup"><span data-stu-id="94581-119">Method calls are analyzed even when they are conditionally omitted.</span></span> <span data-ttu-id="94581-120">Por exemplo, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> no modo de versão.</span><span class="sxs-lookup"><span data-stu-id="94581-120">For instance, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> in release mode.</span></span>

<span data-ttu-id="94581-121">A invocação de métodos anotados com os seguintes atributos também afetará a análise do fluxo:</span><span class="sxs-lookup"><span data-stu-id="94581-121">Invocation of methods annotated with the following attributes will also affect flow analysis:</span></span>

- <span data-ttu-id="94581-122">Pré-condições simples: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> e<xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span><span class="sxs-lookup"><span data-stu-id="94581-122">Simple pre-conditions: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span></span>
- <span data-ttu-id="94581-123">Pós-condições simples: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> e<xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span><span class="sxs-lookup"><span data-stu-id="94581-123">Simple post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span></span>
- <span data-ttu-id="94581-124">Pós-condições condicionais: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> e<xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span><span class="sxs-lookup"><span data-stu-id="94581-124">Conditional post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span></span>
- <span data-ttu-id="94581-125"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute>(por exemplo, `DoesNotReturnIf(false)` para <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ) e<xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span><span class="sxs-lookup"><span data-stu-id="94581-125"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (e.g. `DoesNotReturnIf(false)` for <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>) and <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span></span>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- <span data-ttu-id="94581-126">Pós-condições do membro: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> e<xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span><span class="sxs-lookup"><span data-stu-id="94581-126">Member post-conditions: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> and <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span></span>

### <a name="to-set-this-compiler-option-in-a-project"></a><span data-ttu-id="94581-127">Para definir essa opção de compilador em um projeto</span><span class="sxs-lookup"><span data-stu-id="94581-127">To set this compiler option in a project</span></span>

<span data-ttu-id="94581-128">Edite o *. csproj* para adicionar a `<Nullable>` marca em uma `Project/PropertyGroup` hierarquia:</span><span class="sxs-lookup"><span data-stu-id="94581-128">Edit the *.csproj* to add the `<Nullable>` tag within a `Project/PropertyGroup` hierarchy:</span></span>

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a><span data-ttu-id="94581-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="94581-129">See also</span></span>

- [<span data-ttu-id="94581-130">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="94581-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="94581-131">Tipos de referência anuláveis</span><span class="sxs-lookup"><span data-stu-id="94581-131">Nullable reference types</span></span>](../../nullable-references.md)
