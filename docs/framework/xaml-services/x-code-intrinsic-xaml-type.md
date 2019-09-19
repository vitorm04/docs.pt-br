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
ms.openlocfilehash: 2b7713548b6269f079ef32b5bf1fe4fa630edcc8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053789"
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="1cdda-102">Tipo intrínseco x:Code (XAML)</span><span class="sxs-lookup"><span data-stu-id="1cdda-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="1cdda-103">Permite o posicionamento do código em uma produção XAML.</span><span class="sxs-lookup"><span data-stu-id="1cdda-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="1cdda-104">Esse código pode ser compilado por qualquer implementação de processador XAML que compila XAML ou deixado na produção XAML para usos posteriores, como interpretação por um tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="1cdda-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="1cdda-105">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="1cdda-105">XAML Object Element Usage</span></span>  
  
```xaml  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a><span data-ttu-id="1cdda-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="1cdda-106">Remarks</span></span>  
 <span data-ttu-id="1cdda-107">O código dentro do `x:Code` elemento de diretiva XAML ainda é interpretado no namespace XML geral e nos namespaces XAML fornecidos.</span><span class="sxs-lookup"><span data-stu-id="1cdda-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="1cdda-108">Portanto, geralmente é necessário colocar o código usado para `x:Code` dentro de um `CDATA` segmento.</span><span class="sxs-lookup"><span data-stu-id="1cdda-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>  
  
 <span data-ttu-id="1cdda-109">`x:Code`Não é permitido para todos os mecanismos de implantação possíveis de uma produção XAML.</span><span class="sxs-lookup"><span data-stu-id="1cdda-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="1cdda-110">Em estruturas específicas (por exemplo, WPF), o código deve ser compilado.</span><span class="sxs-lookup"><span data-stu-id="1cdda-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="1cdda-111">Em outras estruturas, `x:Code` o uso pode ser geralmente não permitido.</span><span class="sxs-lookup"><span data-stu-id="1cdda-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>  
  
 <span data-ttu-id="1cdda-112">Para estruturas que permitem conteúdo gerenciado `x:Code` , o compilador de idioma correto a ser usado `x:Code` para conteúdo é determinado pelas configurações e destinos do projeto recipiente que é usado para compilar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1cdda-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="1cdda-113">Observações de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="1cdda-113">WPF Usage Notes</span></span>  
 <span data-ttu-id="1cdda-114">O código declarado `x:Code` no para WPF tem várias limitações notáveis:</span><span class="sxs-lookup"><span data-stu-id="1cdda-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>  
  
- <span data-ttu-id="1cdda-115">O `x:Code` elemento Diretivo deve ser um elemento filho imediato do elemento raiz da produção XAML.</span><span class="sxs-lookup"><span data-stu-id="1cdda-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>  
  
- <span data-ttu-id="1cdda-116">a [diretiva x:Class](x-class-directive.md) deve ser fornecida no elemento pai root.</span><span class="sxs-lookup"><span data-stu-id="1cdda-116">[x:Class Directive](x-class-directive.md) must be provided on the parent root element.</span></span>  
  
- <span data-ttu-id="1cdda-117">O código colocado em `x:Code` será tratado pela compilação para estar dentro do escopo da classe parcial que já está sendo criada para essa página XAML.</span><span class="sxs-lookup"><span data-stu-id="1cdda-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="1cdda-118">Portanto, todo o código que você definir deve ser membros ou variáveis dessa classe parcial.</span><span class="sxs-lookup"><span data-stu-id="1cdda-118">Therefore all code you define must be members or variables of that partial class.</span></span>  
  
- <span data-ttu-id="1cdda-119">Você não pode definir classes adicionais, além de aninhar uma classe dentro da classe Partial (o aninhamento é permitido, mas não é comum porque classes aninhadas não podem ser referenciadas em XAML).</span><span class="sxs-lookup"><span data-stu-id="1cdda-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="1cdda-120">Os namespaces CLR que não sejam o namespace usado para a classe parcial existente não podem ser definidos ou adicionados ao.</span><span class="sxs-lookup"><span data-stu-id="1cdda-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>  
  
- <span data-ttu-id="1cdda-121">As referências a entidades de código fora do namespace CLR de classe parcial devem ser totalmente qualificadas.</span><span class="sxs-lookup"><span data-stu-id="1cdda-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="1cdda-122">Se os membros que estão sendo declarados forem substituídos para os membros de classe parcial Overridable, isso deverá ser especificado com a palavra-chave de substituição específica do idioma.</span><span class="sxs-lookup"><span data-stu-id="1cdda-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="1cdda-123">Se os membros declarados no escopo entrarem em `x:Code` conflito com membros da classe parcial criada fora do XAML, de forma que o compilador relate o conflito, o arquivo XAML não poderá ser compilado ou carregado.</span><span class="sxs-lookup"><span data-stu-id="1cdda-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cdda-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1cdda-124">See also</span></span>

- [<span data-ttu-id="1cdda-125">Diretiva x:Class</span><span class="sxs-lookup"><span data-stu-id="1cdda-125">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="1cdda-126">Code-behind e XAML no WPF</span><span class="sxs-lookup"><span data-stu-id="1cdda-126">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="1cdda-127">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="1cdda-127">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
