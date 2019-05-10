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
ms.openlocfilehash: f6898008fa3e3e7e385a2bc77c5b2eac7eeda2ec
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617149"
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="e12ac-102">Tipo intrínseco x:Code (XAML)</span><span class="sxs-lookup"><span data-stu-id="e12ac-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="e12ac-103">Permite o posicionamento de código dentro de uma produção de XAML.</span><span class="sxs-lookup"><span data-stu-id="e12ac-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="e12ac-104">Esse código também pode ser compilado por qualquer implementação do processador XAML que compila XAML ou à esquerda na produção para uso posterior, como de interpretação XAML por um tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e12ac-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="e12ac-105">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="e12ac-105">XAML Object Element Usage</span></span>  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a><span data-ttu-id="e12ac-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="e12ac-106">Remarks</span></span>  
 <span data-ttu-id="e12ac-107">O código dentro de `x:Code` elemento de diretiva de XAML é ainda interpretada dentro do namespace XML geral e os namespaces XAML fornecidos.</span><span class="sxs-lookup"><span data-stu-id="e12ac-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="e12ac-108">Portanto, é geralmente necessário incluir o código usado para `x:Code` dentro de um `CDATA` segmento.</span><span class="sxs-lookup"><span data-stu-id="e12ac-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>  
  
 <span data-ttu-id="e12ac-109">`x:Code` não é permitida em todos os mecanismos de implantação possíveis de uma produção de XAML.</span><span class="sxs-lookup"><span data-stu-id="e12ac-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="e12ac-110">O código deve ser compilado em estruturas específicas (por exemplo, WPF).</span><span class="sxs-lookup"><span data-stu-id="e12ac-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="e12ac-111">Em outras estruturas, `x:Code` uso pode ser geralmente não permitido.</span><span class="sxs-lookup"><span data-stu-id="e12ac-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>  
  
 <span data-ttu-id="e12ac-112">Para estruturas que permitem gerenciado `x:Code` de conteúdo, o compilador de idioma correto a ser usado para `x:Code` conteúdo é determinado pelas configurações e destinos do projeto que é usado para compilar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e12ac-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="e12ac-113">Notas de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="e12ac-113">WPF Usage Notes</span></span>  
 <span data-ttu-id="e12ac-114">Código declarado em `x:Code` para WPF tem várias limitações importantes:</span><span class="sxs-lookup"><span data-stu-id="e12ac-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>  
  
- <span data-ttu-id="e12ac-115">O `x:Code` elemento de diretiva deve ser um elemento filho imediatos do elemento raiz da produção de XAML.</span><span class="sxs-lookup"><span data-stu-id="e12ac-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>  
  
- <span data-ttu-id="e12ac-116">[Diretiva X:Class](x-class-directive.md) deve ser fornecido no elemento root pai.</span><span class="sxs-lookup"><span data-stu-id="e12ac-116">[x:Class Directive](x-class-directive.md) must be provided on the parent root element.</span></span>  
  
- <span data-ttu-id="e12ac-117">O código é colocado dentro de `x:Code` será tratado pela compilação como dentro do escopo da classe parcial que já está sendo criado para a página XAML.</span><span class="sxs-lookup"><span data-stu-id="e12ac-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="e12ac-118">Portanto, todo código que você definir deve ser membros ou variáveis de classe parcial.</span><span class="sxs-lookup"><span data-stu-id="e12ac-118">Therefore all code you define must be members or variables of that partial class.</span></span>  
  
- <span data-ttu-id="e12ac-119">Você não pode definir classes adicionais, além de aninhamento de uma classe dentro da classe parcial (aninhamento é permitido, mas não é comum porque as classes aninhadas não podem ser referenciadas em XAML).</span><span class="sxs-lookup"><span data-stu-id="e12ac-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="e12ac-120">Namespaces CLR que não seja o namespace que é usado para a classe parcial existente não pode ser definida ou adicionado ao.</span><span class="sxs-lookup"><span data-stu-id="e12ac-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>  
  
- <span data-ttu-id="e12ac-121">Referências a entidades de código fora do namespace CLR de classe parcial devem ser totalmente qualificadas.</span><span class="sxs-lookup"><span data-stu-id="e12ac-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="e12ac-122">Se os membros que estão sendo declarados são substituições para os membros de classe parcial substituível, isso deve ser especificado com a palavra-chave específicas de idioma de substituição.</span><span class="sxs-lookup"><span data-stu-id="e12ac-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="e12ac-123">Se os membros declarados em `x:Code` escopo estão em conflito com os membros da classe parcial, criada a partir do XAML, de forma que o compilador relatará o conflito, o arquivo XAML não é possível compilar ou carregar.</span><span class="sxs-lookup"><span data-stu-id="e12ac-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e12ac-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e12ac-124">See also</span></span>

- [<span data-ttu-id="e12ac-125">Diretiva x:Class</span><span class="sxs-lookup"><span data-stu-id="e12ac-125">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="e12ac-126">Code-behind e XAML no WPF</span><span class="sxs-lookup"><span data-stu-id="e12ac-126">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="e12ac-127">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="e12ac-127">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
