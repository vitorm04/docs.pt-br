---
title: Use &quot;FilePutObject&quot; em vez de &quot;FilePut&quot; quando usar argumento do tipo &quot;Object&quot; | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4b6889950e4eed8c0f1eff09a988d4443d47c9b2
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a><span data-ttu-id="acc89-102">Use 'FilePutObject' em vez de 'FilePut' quando usar argumento do tipo 'Object'</span><span class="sxs-lookup"><span data-stu-id="acc89-102">Use &#39;FilePutObject&#39; instead of &#39;FilePut&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="acc89-103">O `FilePut` método inclui um argumento do tipo`Object`.</span><span class="sxs-lookup"><span data-stu-id="acc89-103">The `FilePut` method includes an argument of type`Object`.</span></span> <span data-ttu-id="acc89-104">`FilePutObject`deve ser usado no lugar de `FilePut` para evitar ambiguidades.</span><span class="sxs-lookup"><span data-stu-id="acc89-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="acc89-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="acc89-105">To correct this error</span></span>  
  
-   <span data-ttu-id="acc89-106">Substitua `FilePut` por `FilePutObject`.</span><span class="sxs-lookup"><span data-stu-id="acc89-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
-   <span data-ttu-id="acc89-107">Conversão de `Object` argumento para um tipo mais específico.</span><span class="sxs-lookup"><span data-stu-id="acc89-107">Cast the `Object` argument to a more specific type.</span></span>  
  
-   <span data-ttu-id="acc89-108">Use a funcionalidade disponível no `My.Computer.FileSystem` objeto.</span><span class="sxs-lookup"><span data-stu-id="acc89-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acc89-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="acc89-109">See Also</span></span>  
 <span data-ttu-id="acc89-110">[NÃO está em compilação: Função FilePutObject](http://msdn.microsoft.com/en-us/a0f52a1c-5ecc-4945-b18c-03147af61d6b) </span><span class="sxs-lookup"><span data-stu-id="acc89-110">[NOT IN BUILD: FilePutObject Function](http://msdn.microsoft.com/en-us/a0f52a1c-5ecc-4945-b18c-03147af61d6b) </span></span>  
<span data-ttu-id="acc89-111"> [Objeto My.Computer.FileSystem](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md) </span><span class="sxs-lookup"><span data-stu-id="acc89-111"> [My.Computer.FileSystem Object](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md) </span></span>  
<span data-ttu-id="acc89-112"> [Método WriteAllBytes](http://msdn.microsoft.com/en-us/b1a24dc1-eac8-4e22-8ffa-cc3bacbaf826)</span><span class="sxs-lookup"><span data-stu-id="acc89-112"> [My.Computer.FileSystem.WriteAllBytes Method](http://msdn.microsoft.com/en-us/b1a24dc1-eac8-4e22-8ffa-cc3bacbaf826)</span></span>
