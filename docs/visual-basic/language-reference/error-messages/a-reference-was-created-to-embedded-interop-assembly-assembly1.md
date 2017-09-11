---
title: "Foi criada uma referência ao assembly de interoperabilidade inserido &quot;&lt;assembly1&gt;&quot;devido a uma referência indireta ao assembly do assembly&quot;&lt;assembly2&gt;&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 79fe6dfe86f818133b4aa23dd6c590b7352d2e6b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="a-reference-was-created-to-embedded-interop-assembly-39ltassembly1gt39-because-of-an-indirect-reference-to-that-assembly-from-assembly-39ltassembly2gt39"></a><span data-ttu-id="848aa-102">Foi criada uma referência ao assembly de interoperabilidade inserido '&lt;assembly1&gt;'devido a uma referência indireta ao assembly do assembly'&lt;assembly2&gt;'</span><span class="sxs-lookup"><span data-stu-id="848aa-102">A reference was created to embedded interop assembly &#39;&lt;assembly1&gt;&#39; because of an indirect reference to that assembly from assembly &#39;&lt;assembly2&gt;&#39;</span></span>
<span data-ttu-id="848aa-103">Foi criada uma referência ao assembly de interoperabilidade inserido '\<assembly1 >' devido a uma referência indireta ao assembly do assembly '\<assembly2 >'.</span><span class="sxs-lookup"><span data-stu-id="848aa-103">A reference was created to embedded interop assembly '\<assembly1>' because of an indirect reference to that assembly from assembly '\<assembly2>'.</span></span> <span data-ttu-id="848aa-104">Considere alterar a propriedade 'Inserir tipos Interop' em um assembly.</span><span class="sxs-lookup"><span data-stu-id="848aa-104">Consider changing the 'Embed Interop Types' property on either assembly.</span></span>  
  
 <span data-ttu-id="848aa-105">Você adicionou uma referência a um assembly (assembly1) que tem o `Embed Interop Types` definida como `True`.</span><span class="sxs-lookup"><span data-stu-id="848aa-105">You have added a reference to an assembly (assembly1) that has the `Embed Interop Types` property set to `True`.</span></span> <span data-ttu-id="848aa-106">Isso instrui o compilador a inserir informações de tipo de interoperabilidade do assembly.</span><span class="sxs-lookup"><span data-stu-id="848aa-106">This instructs the compiler to embed interop type information from that assembly.</span></span> <span data-ttu-id="848aa-107">No entanto, o compilador não pode inserir informações de tipo de interoperabilidade do assembly porque outro assembly que você referenciou (assembly2) também faz referência a esse assembly (assembly1) e tem o `Embed Interop Types` definida como `False`.</span><span class="sxs-lookup"><span data-stu-id="848aa-107">However, the compiler cannot embed interop type information from that assembly because another assembly that you have referenced (assembly2) also references that assembly (assembly1) and has the `Embed Interop Types` property set to `False`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="848aa-108">Definindo o `Embed Interop Types` propriedade em uma referência de assembly para `True` é equivalente à referência do assembly usando o `/link` opção para o compilador de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="848aa-108">Setting the `Embed Interop Types` property on an assembly reference to `True` is equivalent to referencing the assembly by using the `/link` option for the command-line compiler.</span></span>  
  
 <span data-ttu-id="848aa-109">**ID do erro:** BC40059</span><span class="sxs-lookup"><span data-stu-id="848aa-109">**Error ID:** BC40059</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="848aa-110">Para resolver este aviso</span><span class="sxs-lookup"><span data-stu-id="848aa-110">To address this warning</span></span>  
  
-   <span data-ttu-id="848aa-111">Para inserir informações de tipo de interoperabilidade para os dois assemblies, definir o `Embed Interop Types` propriedade em todas as referências a assembly1 para `True`.</span><span class="sxs-lookup"><span data-stu-id="848aa-111">To embed interop type information for both assemblies, set the `Embed Interop Types` property on all references to assembly1 to `True`.</span></span>  
  
-   <span data-ttu-id="848aa-112">Para remover o aviso, você pode definir o `Embed Interop Types` propriedade assembly1 para `False`.</span><span class="sxs-lookup"><span data-stu-id="848aa-112">To remove the warning, you can set the `Embed Interop Types` property of assembly1 to `False`.</span></span> <span data-ttu-id="848aa-113">Nesse caso, as informações de tipo de interoperabilidade são fornecidas por um assembly de interoperabilidade primária (PIA).</span><span class="sxs-lookup"><span data-stu-id="848aa-113">In this case, interop type information is provided by a primary interop assembly (PIA).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="848aa-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="848aa-114">See Also</span></span>  
 <span data-ttu-id="848aa-115">[/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md) </span><span class="sxs-lookup"><span data-stu-id="848aa-115">[/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md) </span></span>  
<span data-ttu-id="848aa-116"> [Programação com Assemblies de interoperabilidade primários](http://msdn.microsoft.com/en-us/306fa1d6-0703-4004-9e93-d0a57f1be81e)</span><span class="sxs-lookup"><span data-stu-id="848aa-116"> [Programming with Primary Interop Assemblies](http://msdn.microsoft.com/en-us/306fa1d6-0703-4004-9e93-d0a57f1be81e)</span></span>
