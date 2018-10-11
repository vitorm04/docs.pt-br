---
title: Considerações sobre versão e atualização para os desenvolvedores de C#
description: A introdução de novos recursos de linguagem de programação em sua biblioteca pode afetar o código que faz uso dela.
ms.date: 09/19/2018
ms.openlocfilehash: 56685422e2c73dcca25acbdccb3a77a8de9df775
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47199925"
---
# <a name="version-and-update-considerations-for-c-developers"></a><span data-ttu-id="80fea-103">Considerações sobre versão e atualização para os desenvolvedores de C#</span><span class="sxs-lookup"><span data-stu-id="80fea-103">Version and update considerations for C# developers</span></span>

<span data-ttu-id="80fea-104">A compatibilidade é uma meta muito importante quando novos recursos são adicionados à linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="80fea-104">Compatibility is a very important goal as new features are added to the C# language.</span></span> <span data-ttu-id="80fea-105">Em quase todos os casos, o código existente pode ser recompilado com uma nova versão do compilador sem nenhum problema.</span><span class="sxs-lookup"><span data-stu-id="80fea-105">In almost all cases, existing code can be recompiled with a new compiler version without any issue.</span></span>

<span data-ttu-id="80fea-106">Mais cuidado pode ser necessário quando você adota novos recursos de linguagem de programação em uma biblioteca.</span><span class="sxs-lookup"><span data-stu-id="80fea-106">More care may be required when you adopt new language features in a library.</span></span> <span data-ttu-id="80fea-107">Você poderá estar criando uma nova biblioteca com recursos encontrados na versão mais recente, e precisará garantir que os aplicativos criados com versões anteriores do compilador possam usá-la.</span><span class="sxs-lookup"><span data-stu-id="80fea-107">You may be creating a new library with features found in the latest version and need to ensure apps built using previous versions of the compiler can use it.</span></span> <span data-ttu-id="80fea-108">Ou você pode estar atualizando uma biblioteca existente e muitos dos seus usuários talvez não tenham atualizado as versões ainda.</span><span class="sxs-lookup"><span data-stu-id="80fea-108">Or you may be upgrading an existing library and many of your users may not have upgraded versions yet.</span></span> <span data-ttu-id="80fea-109">Ao tomar decisões sobre a adoção de novos recursos, você precisará considerar duas variações de compatibilidade: compatível com a origem e compatível com binário.</span><span class="sxs-lookup"><span data-stu-id="80fea-109">As you make decisions on adopting new features, you'll need to consider two variations of compatibility: source compatible and binary compatible.</span></span>

## <a name="binary-compatible-changes"></a><span data-ttu-id="80fea-110">Alterações compatíveis com binário</span><span class="sxs-lookup"><span data-stu-id="80fea-110">Binary compatible changes</span></span>

<span data-ttu-id="80fea-111">Alterações à sua biblioteca são **compatíveis com binário** quando sua biblioteca atualizada pode ser usada sem recompilar os aplicativos e bibliotecas que fazem uso dela.</span><span class="sxs-lookup"><span data-stu-id="80fea-111">Changes to your library are **binary compatible** when your updated library can be used without rebuilding applications and libraries that use it.</span></span> <span data-ttu-id="80fea-112">Não é necessário recompilar assemblies dependentes, tampouco é necessária qualquer alteração de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="80fea-112">Dependent assemblies are not required to be rebuilt, nor are any source code changes required.</span></span> <span data-ttu-id="80fea-113">Alterações compatíveis com binário também alterações compatíveis com a origem.</span><span class="sxs-lookup"><span data-stu-id="80fea-113">Binary compatible changes are also source compatible changes.</span></span>

## <a name="source-compatible-changes"></a><span data-ttu-id="80fea-114">Alterações compatíveis com a origem</span><span class="sxs-lookup"><span data-stu-id="80fea-114">Source compatible changes</span></span>

<span data-ttu-id="80fea-115">Alterações à sua biblioteca são **compatíveis com a origem** quando os aplicativos e bibliotecas que usam sua biblioteca não exigem alterações de código-fonte, mas a origem deve ser recompilada em relação à nova versão para funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="80fea-115">Changes to your library are **source compatible** when applications and libraries that use your library do not require source code changes, but the source must be recompiled against the new version to work correctly.</span></span>

## <a name="incompatible-changes"></a><span data-ttu-id="80fea-116">Alterações incompatíveis</span><span class="sxs-lookup"><span data-stu-id="80fea-116">Incompatible changes</span></span>

<span data-ttu-id="80fea-117">Se uma alteração não for nem **compatível com a origem** nem **compatível com binário**, alterações de código-fonte, juntamente com a recompilação, serão necessárias nas bibliotecas e aplicativos dependentes.</span><span class="sxs-lookup"><span data-stu-id="80fea-117">If a change is neither **source compatible** nor **binary compatible**, source code changes along with recompilation are required in dependent libraries and applications.</span></span>

## <a name="evaluate-your-library"></a><span data-ttu-id="80fea-118">Avaliar a biblioteca</span><span class="sxs-lookup"><span data-stu-id="80fea-118">Evaluate your library</span></span>

<span data-ttu-id="80fea-119">Esses conceitos de compatibilidade afetam as declarações públicas e protegidas para sua biblioteca, mas não a respectiva implementação interna.</span><span class="sxs-lookup"><span data-stu-id="80fea-119">These compatibility concepts affect the public and protected declarations for your library, not its internal implementation.</span></span> <span data-ttu-id="80fea-120">A adoção de quaisquer novos recursos internamente é sempre **compatível com binário**.</span><span class="sxs-lookup"><span data-stu-id="80fea-120">Adopting any new features internally are always **binary compatible**.</span></span>  

<span data-ttu-id="80fea-121">Alterações **compatíveis com binário** oferecem uma nova sintaxe que gera o mesmo código compilado para declarações públicas que a sintaxe antiga.</span><span class="sxs-lookup"><span data-stu-id="80fea-121">**Binary compatible** changes provide new syntax that generates the same compiled code for public declarations as the older syntax.</span></span> <span data-ttu-id="80fea-122">Por exemplo, a alteração de um método para um membro de corpo da expressão é uma alteração **compatível com binário**:</span><span class="sxs-lookup"><span data-stu-id="80fea-122">For example, changing a method to an expression-bodied member is a **binary compatible** change:</span></span>

<span data-ttu-id="80fea-123">Código original:</span><span class="sxs-lookup"><span data-stu-id="80fea-123">Original code:</span></span>

```csharp
public double CalculateSquare(double value)
{
    return value * value;
}
```

<span data-ttu-id="80fea-124">Novo código:</span><span class="sxs-lookup"><span data-stu-id="80fea-124">New code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="80fea-125">Alterações **compatíveis com a origem** introduzem sintaxe que altera o código compilado para um membro público, mas de uma forma compatível com sites de chamada já existentes.</span><span class="sxs-lookup"><span data-stu-id="80fea-125">**Source compatible** changes introduce syntax that changes the compiled code for a public member, but in a way that is compatible with existing call sites.</span></span> <span data-ttu-id="80fea-126">Por exemplo, alterar a assinatura de um método de um parâmetro por valor para um `in` por referência é compatível com a origem, mas não é compatível com binário:</span><span class="sxs-lookup"><span data-stu-id="80fea-126">For example, changing a method signature from a by value parameter to an `in` by reference parameter is source compatible, but not binary compatible:</span></span>

<span data-ttu-id="80fea-127">Código original:</span><span class="sxs-lookup"><span data-stu-id="80fea-127">Original code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="80fea-128">Novo código:</span><span class="sxs-lookup"><span data-stu-id="80fea-128">New code:</span></span>

```csharp
public double CalculateSquare(in double value) => value * value;
```

<span data-ttu-id="80fea-129">Os artigos [Novidades](index.md) apontam que a introdução de um recurso que afeta as declarações públicas é compatível com a origem ou compatível com binário.</span><span class="sxs-lookup"><span data-stu-id="80fea-129">The [What's new](index.md) articles note if introducing a feature that affects public declarations is source compatible or binary compatible.</span></span>