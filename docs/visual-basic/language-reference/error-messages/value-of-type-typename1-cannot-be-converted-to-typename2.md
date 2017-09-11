---
title: "O valor do tipo &quot;&lt;typename1&gt;&quot;não pode ser convertido em&quot;&lt;typename2&gt;&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30955
- bc30955
dev_langs:
- VB
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
caps.latest.revision: 12
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
ms.openlocfilehash: 2fbe1550515d2b15a3e349392fc8d78812787ae4
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39"></a><span data-ttu-id="e4acc-102">O valor do tipo '&lt;typename1&gt;'não pode ser convertido em'&lt;typename2&gt;'</span><span class="sxs-lookup"><span data-stu-id="e4acc-102">Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39;</span></span>
<span data-ttu-id="e4acc-103">O valor do tipo '\<typename1 >' não pode ser convertido em '\<typename2 >'.</span><span class="sxs-lookup"><span data-stu-id="e4acc-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="e4acc-104">Incompatibilidade de tipo pode ser devido à combinação de uma referência de arquivo com uma referência ao assembly '\<assemblyname >'.</span><span class="sxs-lookup"><span data-stu-id="e4acc-104">Type mismatch could be due to the mixing of a file reference with a project reference to assembly '\<assemblyname>'.</span></span> <span data-ttu-id="e4acc-105">Tente substituir a referência de arquivo para '\<filepath >' no projeto '\<projectname1 >' com uma referência de projeto para '\<projectname2 >'.</span><span class="sxs-lookup"><span data-stu-id="e4acc-105">Try replacing the file reference to '\<filepath>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="e4acc-106">Em uma situação na qual um projeto faz uma referência de projeto e uma referência de arquivo, o compilador não pode garantir que um tipo pode ser convertido para outro.</span><span class="sxs-lookup"><span data-stu-id="e4acc-106">In a situation where a project makes both a project reference and a file reference, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="e4acc-107">O pseudocódigo a seguir ilustra uma situação que pode gerar esse erro.</span><span class="sxs-lookup"><span data-stu-id="e4acc-107">The following pseudo-code illustrates a situation that can generate this error.</span></span>  
  
 `' ================ Visual Basic project P1 ================`  
  
 `'        P1 makes a PROJECT REFERENCE to project P2`  
  
 `'        and a FILE REFERENCE to project P3.`  
  
 `Public commonObject As P3.commonClass`  
  
 `commonObject = P2.getCommonClass()`  
  
 `' ================ Visual Basic project P2 ================`  
  
 `'        P2 makes a PROJECT REFERENCE to project P3`  
  
 `Public Function getCommonClass() As P3.commonClass`  
  
 `Return New P3.commonClass`  
  
 `End Function`  
  
 `' ================ Visual Basic project P3 ================`  
  
 `Public Class commonClass`  
  
 `End Class`  
  
 <span data-ttu-id="e4acc-108">Projeto `P1` faz uma referência de projeto indireta através do projeto `P2` ao projeto `P3`e também uma referência a `P3`.</span><span class="sxs-lookup"><span data-stu-id="e4acc-108">Project `P1` makes an indirect project reference through project `P2` to project `P3`, and also a direct file reference to `P3`.</span></span> <span data-ttu-id="e4acc-109">A declaração de `commonObject` usa a referência de arquivo para `P3`, enquanto a chamada para `P2.getCommonClass` usa a referência de projeto para `P3`.</span><span class="sxs-lookup"><span data-stu-id="e4acc-109">The declaration of `commonObject` uses the file reference to `P3`, while the call to `P2.getCommonClass` uses the project reference to `P3`.</span></span>  
  
 <span data-ttu-id="e4acc-110">O problema nessa situação é que a referência do arquivo Especifica um caminho de arquivo e um nome para o arquivo de saída de `P3` (geralmente p3. dll), enquanto as referências do projeto identificam o projeto de origem (`P3`) pelo nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="e4acc-110">The problem in this situation is that the file reference specifies a file path and name for the output file of `P3` (typically p3.dll), while the project references identify the source project (`P3`) by project name.</span></span> <span data-ttu-id="e4acc-111">Por isso, o compilador não pode garantir que o tipo `P3.commonClass` vem do mesmo código-fonte por meio de duas referências diferentes.</span><span class="sxs-lookup"><span data-stu-id="e4acc-111">Because of this, the compiler cannot guarantee that the type `P3.commonClass` comes from the same source code through the two different references.</span></span>  
  
 <span data-ttu-id="e4acc-112">Essa situação normalmente ocorre quando as referências de projeto e referências de arquivo são misturadas.</span><span class="sxs-lookup"><span data-stu-id="e4acc-112">This situation typically occurs when project references and file references are mixed.</span></span> <span data-ttu-id="e4acc-113">Na ilustração anterior, o problema não ocorreria se `P1` feita uma referência direta ao `P3` em vez de uma referência de arquivo.</span><span class="sxs-lookup"><span data-stu-id="e4acc-113">In the preceding illustration, the problem would not occur if `P1` made a direct project reference to `P3` instead of a file reference.</span></span>  
  
 <span data-ttu-id="e4acc-114">**ID do erro:** BC30955</span><span class="sxs-lookup"><span data-stu-id="e4acc-114">**Error ID:** BC30955</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e4acc-115">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="e4acc-115">To correct this error</span></span>  
  
-   <span data-ttu-id="e4acc-116">Altere a referência de arquivo para uma referência de projeto.</span><span class="sxs-lookup"><span data-stu-id="e4acc-116">Change the file reference to a project reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4acc-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4acc-117">See Also</span></span>  
 <span data-ttu-id="e4acc-118">[Conversões de tipo no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="e4acc-118">[Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="e4acc-119"> [Gerenciando referências em um projeto](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span><span class="sxs-lookup"><span data-stu-id="e4acc-119"> [Managing references in a project](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span></span>  
<span data-ttu-id="e4acc-120"> [NIB: como adicionar ou remover referências usando a caixa de diálogo Adicionar Referência](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)</span><span class="sxs-lookup"><span data-stu-id="e4acc-120"> [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)</span></span>
