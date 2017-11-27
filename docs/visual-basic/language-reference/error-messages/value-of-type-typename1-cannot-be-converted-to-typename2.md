---
title: "Valor do tipo &#39; &lt;typename1&gt;&#39; não pode ser convertido para &#39;&lt; typename2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords: BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2154a56f9ff004f906cb2b571f8771e74cfca9c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39"></a><span data-ttu-id="e394e-102">Valor do tipo &#39; &lt;typename1&gt;&#39; não pode ser convertido para &#39;&lt; typename2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="e394e-102">Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39;</span></span>
<span data-ttu-id="e394e-103">O valor do tipo '\<typename1 >' não pode ser convertido em '\<typename2 >'.</span><span class="sxs-lookup"><span data-stu-id="e394e-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="e394e-104">Incompatibilidade de tipo pode se dever à combinação de uma referência de arquivo com uma referência ao assembly '\<assemblyname >'.</span><span class="sxs-lookup"><span data-stu-id="e394e-104">Type mismatch could be due to the mixing of a file reference with a project reference to assembly '\<assemblyname>'.</span></span> <span data-ttu-id="e394e-105">Tente substituir a referência de arquivo para '\<filepath >' no projeto '\<projectname1 >' com uma referência de projeto para '\<projectname2 >'.</span><span class="sxs-lookup"><span data-stu-id="e394e-105">Try replacing the file reference to '\<filepath>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="e394e-106">Em uma situação na qual um projeto faz uma referência de projeto e uma referência de arquivo, o compilador não pode garantir que um tipo possa ser convertido para outro.</span><span class="sxs-lookup"><span data-stu-id="e394e-106">In a situation where a project makes both a project reference and a file reference, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="e394e-107">O pseudocódigo a seguir ilustra uma situação que pode gerar esse erro.</span><span class="sxs-lookup"><span data-stu-id="e394e-107">The following pseudo-code illustrates a situation that can generate this error.</span></span>  
  
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
  
 <span data-ttu-id="e394e-108">Projeto `P1` faz uma referência indireta projeto por meio do projeto `P2` ao projeto `P3`e também uma referência a `P3`.</span><span class="sxs-lookup"><span data-stu-id="e394e-108">Project `P1` makes an indirect project reference through project `P2` to project `P3`, and also a direct file reference to `P3`.</span></span> <span data-ttu-id="e394e-109">A declaração de `commonObject` usa a referência de arquivo para `P3`, enquanto a chamada para `P2.getCommonClass` usa a referência de projeto para `P3`.</span><span class="sxs-lookup"><span data-stu-id="e394e-109">The declaration of `commonObject` uses the file reference to `P3`, while the call to `P2.getCommonClass` uses the project reference to `P3`.</span></span>  
  
 <span data-ttu-id="e394e-110">O problema nessa situação é que a referência do arquivo Especifica um caminho de arquivo e um nome para o arquivo de saída do `P3` (geralmente p3. dll), enquanto as referências do projeto identificam o projeto de origem (`P3`) pelo nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="e394e-110">The problem in this situation is that the file reference specifies a file path and name for the output file of `P3` (typically p3.dll), while the project references identify the source project (`P3`) by project name.</span></span> <span data-ttu-id="e394e-111">Por isso, o compilador não pode garantir que o tipo `P3.commonClass` vêm do mesmo código-fonte por meio de duas referências diferentes.</span><span class="sxs-lookup"><span data-stu-id="e394e-111">Because of this, the compiler cannot guarantee that the type `P3.commonClass` comes from the same source code through the two different references.</span></span>  
  
 <span data-ttu-id="e394e-112">Essa situação normalmente ocorre quando as referências do projeto e as referências do arquivo estão misturadas.</span><span class="sxs-lookup"><span data-stu-id="e394e-112">This situation typically occurs when project references and file references are mixed.</span></span> <span data-ttu-id="e394e-113">Na ilustração anterior, o problema não ocorrerá se `P1` feita uma referência direta ao `P3` em vez de uma referência de arquivo.</span><span class="sxs-lookup"><span data-stu-id="e394e-113">In the preceding illustration, the problem would not occur if `P1` made a direct project reference to `P3` instead of a file reference.</span></span>  
  
 <span data-ttu-id="e394e-114">**ID do erro:** BC30955</span><span class="sxs-lookup"><span data-stu-id="e394e-114">**Error ID:** BC30955</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e394e-115">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="e394e-115">To correct this error</span></span>  
  
-   <span data-ttu-id="e394e-116">Altere a referência de arquivo para uma referência de projeto.</span><span class="sxs-lookup"><span data-stu-id="e394e-116">Change the file reference to a project reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e394e-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e394e-117">See Also</span></span>  
 [<span data-ttu-id="e394e-118">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e394e-118">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="e394e-119">Gerenciando referências em um projeto</span><span class="sxs-lookup"><span data-stu-id="e394e-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="e394e-120">NIB: como adicionar ou remover referências usando a caixa de diálogo Adicionar Referência</span><span class="sxs-lookup"><span data-stu-id="e394e-120">NIB How to: Add or Remove References By Using the Add Reference Dialog Box</span></span>](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
