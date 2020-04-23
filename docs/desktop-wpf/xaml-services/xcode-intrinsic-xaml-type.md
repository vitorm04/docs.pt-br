---
title: Tipo intrínseco x:Code (XAML)
ms.date: 03/30/2017
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
ms.openlocfilehash: 4da72ed630c1df001e3fd6c7e55f866b94c4d9b1
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071552"
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="45c69-102">Tipo intrínseco x:Code (XAML)</span><span class="sxs-lookup"><span data-stu-id="45c69-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="45c69-103">Permite a colocação de código dentro de uma produção XAML.</span><span class="sxs-lookup"><span data-stu-id="45c69-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="45c69-104">Esse código pode ser compilado por qualquer implementação de processador XAML que compile XAML, ou deixado na produção XAML para usos posteriores, como interpretação por tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="45c69-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="45c69-105">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="45c69-105">XAML Object Element Usage</span></span>

```xaml
<x:Code>
   // code instructions, usually enclosed by CDATA...
</x:Code>
```

## <a name="remarks"></a><span data-ttu-id="45c69-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="45c69-106">Remarks</span></span>

<span data-ttu-id="45c69-107">O código `x:Code` dentro do elemento de diretiva XAML ainda é interpretado dentro do espaço de nome XML geral e dos namespaces XAML fornecidos.</span><span class="sxs-lookup"><span data-stu-id="45c69-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="45c69-108">Portanto, geralmente é necessário envolver o código `x:Code` usado `CDATA` para dentro de um segmento.</span><span class="sxs-lookup"><span data-stu-id="45c69-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>

<span data-ttu-id="45c69-109">`x:Code`não é permitido para todos os mecanismos de implantação possíveis de uma produção XAML.</span><span class="sxs-lookup"><span data-stu-id="45c69-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="45c69-110">Em frameworks específicos (por exemplo, WPF) o código deve ser compilado.</span><span class="sxs-lookup"><span data-stu-id="45c69-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="45c69-111">Em outros quadros, `x:Code` o uso pode ser geralmente proibido.</span><span class="sxs-lookup"><span data-stu-id="45c69-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>

<span data-ttu-id="45c69-112">Para estruturas que permitem `x:Code` conteúdo gerenciado, o compilador `x:Code` de idiomas correto para usar para conteúdo é determinado por configurações e metas do projeto de contenção que é usado para compilar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="45c69-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="45c69-113">Notas de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="45c69-113">WPF Usage Notes</span></span>

<span data-ttu-id="45c69-114">O código `x:Code` declarado dentro do WPF tem várias limitações notáveis:</span><span class="sxs-lookup"><span data-stu-id="45c69-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>

- <span data-ttu-id="45c69-115">O `x:Code` elemento diretivo deve ser um elemento filho imediato do elemento raiz da produção XAML.</span><span class="sxs-lookup"><span data-stu-id="45c69-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>

- <span data-ttu-id="45c69-116">[x:Diretiva de classe](xclass-directive.md) deve ser fornecida no elemento raiz pai.</span><span class="sxs-lookup"><span data-stu-id="45c69-116">[x:Class Directive](xclass-directive.md) must be provided on the parent root element.</span></span>

- <span data-ttu-id="45c69-117">O código `x:Code` colocado dentro será tratado por compilação para estar dentro do escopo da classe parcial que já está sendo criada para essa página XAML.</span><span class="sxs-lookup"><span data-stu-id="45c69-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="45c69-118">Portanto, todo o código que você define deve ser membros ou variáveis dessa classe parcial.</span><span class="sxs-lookup"><span data-stu-id="45c69-118">Therefore all code you define must be members or variables of that partial class.</span></span>

- <span data-ttu-id="45c69-119">Você não pode definir classes adicionais, exceto aninhando uma classe dentro da classe parcial (o aninhamento é permitido, mas não é típico porque classes aninhadas não podem ser referenciadas em XAML).</span><span class="sxs-lookup"><span data-stu-id="45c69-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="45c69-120">Os namespaces clr que não sejam o namespace usado para a classe parcial existente não podem ser definidos ou adicionados.</span><span class="sxs-lookup"><span data-stu-id="45c69-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>

- <span data-ttu-id="45c69-121">As referências a entidades de código fora do espaço de nome CLR de classe parcial devem ser totalmente qualificadas.</span><span class="sxs-lookup"><span data-stu-id="45c69-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="45c69-122">Se os membros que estão sendo declarados forem substituídos pelos membros parcialmente da classe, isso deve ser especificado com a palavra-chave de substituição específica do idioma.</span><span class="sxs-lookup"><span data-stu-id="45c69-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="45c69-123">Se os membros `x:Code` declarados em conflito de escopo com membros da classe parcial criados a partir do XAML, de tal forma que o compilador relatar o conflito, o arquivo XAML não poderá compilar ou carregar.</span><span class="sxs-lookup"><span data-stu-id="45c69-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>

## <a name="see-also"></a><span data-ttu-id="45c69-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="45c69-124">See also</span></span>

- [<span data-ttu-id="45c69-125">Diretiva x:Class</span><span class="sxs-lookup"><span data-stu-id="45c69-125">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="45c69-126">Code-behind e XAML no WPF</span><span class="sxs-lookup"><span data-stu-id="45c69-126">Code-Behind and XAML in WPF</span></span>](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="45c69-127">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="45c69-127">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
