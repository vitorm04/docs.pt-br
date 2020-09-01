---
description: -Nullable (opções do compilador C#)
title: -Nullable (opções do compilador C#)
author: IEvangelist
ms.author: dapine
ms.date: 06/04/2020
f1_keywords:
- /nullable
helpviewer_keywords:
- nullable compiler option [C#]
- /nullable compiler option [C#]
- -nullable compiler option [C#]
ms.openlocfilehash: f9c6c204d2563865f741c6ddb4644eb56f956c12
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125040"
---
# <a name="-nullable-c-compiler-options"></a><span data-ttu-id="be33a-103">-Nullable (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="be33a-103">-nullable (C# Compiler Options)</span></span>

<span data-ttu-id="be33a-104">A opção **-Nullable** permite especificar o contexto anulável desejado.</span><span class="sxs-lookup"><span data-stu-id="be33a-104">The **-nullable** option lets you specify the desired nullable context.</span></span>

## <a name="syntax"></a><span data-ttu-id="be33a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="be33a-105">Syntax</span></span>

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a><span data-ttu-id="be33a-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="be33a-106">Arguments</span></span>

<span data-ttu-id="be33a-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="be33a-107">`+` &#124; `-`</span></span>  
<span data-ttu-id="be33a-108">Especificar `+` ou apenas **anulável**faz com que o compilador habilite o contexto anulável.</span><span class="sxs-lookup"><span data-stu-id="be33a-108">Specifying `+`, or just **-nullable**, causes the compiler to enable nullable context.</span></span> <span data-ttu-id="be33a-109">Especificando `-` , que estará em vigor se você não especificar **-Nullable**, desabilitará o contexto anulável.</span><span class="sxs-lookup"><span data-stu-id="be33a-109">Specifying `-`, which is in effect if you do not specify **-nullable**, disables nullable context.</span></span>

<span data-ttu-id="be33a-110">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span><span class="sxs-lookup"><span data-stu-id="be33a-110">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span></span>  
<span data-ttu-id="be33a-111">Especifica a opção de contexto anulável.</span><span class="sxs-lookup"><span data-stu-id="be33a-111">Specifies the nullable context option.</span></span> <span data-ttu-id="be33a-112">Semelhante a `+` ou `-` , para habilitar e desabilitar, mas permite mais granularidade da especificidade de contexto anulável.</span><span class="sxs-lookup"><span data-stu-id="be33a-112">Similar to `+` or `-`, to enable and disable, but allows for more granularity of nullable context specificity.</span></span> <span data-ttu-id="be33a-113">O `enable` argumento, que está em vigor, como se você especificar **-Nullable**, habilita o contexto anulável.</span><span class="sxs-lookup"><span data-stu-id="be33a-113">The `enable` argument, which is in effect the same as if you specify **-nullable**, enables the nullable context.</span></span> <span data-ttu-id="be33a-114">Especificar `disable` desabilitará o contexto anulável.</span><span class="sxs-lookup"><span data-stu-id="be33a-114">Specifying `disable` will disable nullable context.</span></span> <span data-ttu-id="be33a-115">Ao fornecer o `warnings` argumento, **-Nullable: Warnings**, o contexto de aviso anulável é habilitado.</span><span class="sxs-lookup"><span data-stu-id="be33a-115">When providing the `warnings` argument, **-nullable:warnings**, the nullable warning context is enabled.</span></span> <span data-ttu-id="be33a-116">Ao especificar o `annotations` argumento, **-Nullable: Annotations**, o contexto de anotação anulável é habilitado.</span><span class="sxs-lookup"><span data-stu-id="be33a-116">When specifying the `annotations` argument, **-nullable:annotations**, the nullable annotation context is enabled.</span></span>

## <a name="remarks"></a><span data-ttu-id="be33a-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="be33a-117">Remarks</span></span>

<span data-ttu-id="be33a-118">A análise de fluxo é usada para inferir a nulidade das variáveis no código executável.</span><span class="sxs-lookup"><span data-stu-id="be33a-118">Flow analysis is used to infer the nullability of variables within executable code.</span></span> <span data-ttu-id="be33a-119">A nulidade inferida de uma variável é independente da nulidade declarada da variável.</span><span class="sxs-lookup"><span data-stu-id="be33a-119">The inferred nullability of a variable is independent of the variable's declared nullability.</span></span> <span data-ttu-id="be33a-120">As chamadas de método são analisadas mesmo quando são omitidas condicionalmente.</span><span class="sxs-lookup"><span data-stu-id="be33a-120">Method calls are analyzed even when they are conditionally omitted.</span></span> <span data-ttu-id="be33a-121">Por exemplo, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> no modo de versão.</span><span class="sxs-lookup"><span data-stu-id="be33a-121">For instance, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> in release mode.</span></span>

<span data-ttu-id="be33a-122">A invocação de métodos anotados com os seguintes atributos também afetará a análise do fluxo:</span><span class="sxs-lookup"><span data-stu-id="be33a-122">Invocation of methods annotated with the following attributes will also affect flow analysis:</span></span>

- <span data-ttu-id="be33a-123">Pré-condições simples: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> e <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span><span class="sxs-lookup"><span data-stu-id="be33a-123">Simple pre-conditions: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span></span>
- <span data-ttu-id="be33a-124">Pós-condições simples: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> e <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span><span class="sxs-lookup"><span data-stu-id="be33a-124">Simple post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span></span>
- <span data-ttu-id="be33a-125">Pós-condições condicionais: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> e <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span><span class="sxs-lookup"><span data-stu-id="be33a-125">Conditional post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span></span>
- <span data-ttu-id="be33a-126"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (por exemplo, `DoesNotReturnIf(false)` para <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ) e <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span><span class="sxs-lookup"><span data-stu-id="be33a-126"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (for example, `DoesNotReturnIf(false)` for <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>) and <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span></span>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- <span data-ttu-id="be33a-127">Pós-condições do membro: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> e <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span><span class="sxs-lookup"><span data-stu-id="be33a-127">Member post-conditions: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> and <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span></span>

### <a name="to-set-this-compiler-option-in-a-project"></a><span data-ttu-id="be33a-128">Para definir essa opção de compilador em um projeto</span><span class="sxs-lookup"><span data-stu-id="be33a-128">To set this compiler option in a project</span></span>

<span data-ttu-id="be33a-129">Edite o arquivo *. csproj* para adicionar a `<Nullable>` marca em uma `Project/PropertyGroup` hierarquia:</span><span class="sxs-lookup"><span data-stu-id="be33a-129">Edit the *.csproj* file to add the `<Nullable>` tag within a `Project/PropertyGroup` hierarchy:</span></span>

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a><span data-ttu-id="be33a-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="be33a-130">See also</span></span>

- [<span data-ttu-id="be33a-131">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="be33a-131">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="be33a-132">Tipos de referência anuláveis</span><span class="sxs-lookup"><span data-stu-id="be33a-132">Nullable reference types</span></span>](../../nullable-references.md)
