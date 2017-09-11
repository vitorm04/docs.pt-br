---
title: Use &quot;FileGetObject&quot; em vez de &quot;FileGet&quot; quando usar argumento do tipo &quot;Object&quot; | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
ms.assetid: 090b8088-895a-482a-9362-606596bac304
caps.latest.revision: 9
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
ms.openlocfilehash: f8e2068f1da7036b9d787e90abef9b88f7fa21d6
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a><span data-ttu-id="70700-102">Use 'FileGetObject' em vez de 'FileGet' quando usar argumento do tipo 'Object'</span><span class="sxs-lookup"><span data-stu-id="70700-102">Use &#39;FileGetObject&#39; instead of &#39;FileGet&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="70700-103">O `FileGet` método inclui um argumento do tipo `Object`.</span><span class="sxs-lookup"><span data-stu-id="70700-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="70700-104">`FileGetObject`deve ser usado no lugar de `FileGet` para evitar ambiguidades.</span><span class="sxs-lookup"><span data-stu-id="70700-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="70700-105">Observe que a funcionalidade oferecida por `My.Computer.Filesystem` oferece maior facilidade de uso e desempenho que seja `FileGet` ou `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="70700-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="70700-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="70700-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="70700-107">Substitua `FileGet` por `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="70700-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2.  <span data-ttu-id="70700-108">Conversão de `Object` argumento para um tipo mais específico.</span><span class="sxs-lookup"><span data-stu-id="70700-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70700-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70700-109">See Also</span></span>  
 <span data-ttu-id="70700-110">[NÃO está em compilação: Função FileGetObject](http://msdn.microsoft.com/en-us/3eda786b-d1ee-4b44-9dd7-0ea6bff072c0) </span><span class="sxs-lookup"><span data-stu-id="70700-110">[NOT IN BUILD: FileGetObject Function](http://msdn.microsoft.com/en-us/3eda786b-d1ee-4b44-9dd7-0ea6bff072c0) </span></span>  
<span data-ttu-id="70700-111"> [Objeto My.Computer.FileSystem](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)</span><span class="sxs-lookup"><span data-stu-id="70700-111"> [My.Computer.FileSystem Object](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)</span></span>
