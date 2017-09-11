---
title: "Nenhum método &quot;Main&quot; acessível com uma assinatura apropriada foi encontrado em &quot;&lt;nome&gt;&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30737
- vbc30737
dev_langs:
- VB
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
caps.latest.revision: 11
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
ms.openlocfilehash: ce4c891f438dbabc3325468d59fe2b8002b22f4a
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a><span data-ttu-id="3ad89-102">Nenhum método 'Main' acessível com uma assinatura apropriada foi encontrado em '&lt;nome&gt;'</span><span class="sxs-lookup"><span data-stu-id="3ad89-102">No accessible &#39;Main&#39; method with an appropriate signature was found in &#39;&lt;name&gt;&#39;</span></span>
<span data-ttu-id="3ad89-103">Aplicativos de linha de comando devem ter um `Sub Main` definido.</span><span class="sxs-lookup"><span data-stu-id="3ad89-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="3ad89-104">`Main`deve ser declarado como `Public Shared` se ele for definido em uma classe, ou como `Public` se definido em um módulo.</span><span class="sxs-lookup"><span data-stu-id="3ad89-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="3ad89-105">Para obter mais informações sobre `Main`, consulte [NIB: Visual Basic versão de Hello, World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c).</span><span class="sxs-lookup"><span data-stu-id="3ad89-105">For more information on `Main`, see [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c).</span></span>  
  
 <span data-ttu-id="3ad89-106">**ID do erro:** BC30737</span><span class="sxs-lookup"><span data-stu-id="3ad89-106">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3ad89-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="3ad89-107">To correct this error</span></span>  
  
-   <span data-ttu-id="3ad89-108">Definir uma `Public Sub Main` procedimento para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="3ad89-108">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="3ad89-109">Declare-o como `Shared` somente se você defini-lo dentro de uma classe.</span><span class="sxs-lookup"><span data-stu-id="3ad89-109">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ad89-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ad89-110">See Also</span></span>  
 <span data-ttu-id="3ad89-111">[NIB: versão do Visual Basic do Hello, World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c) </span><span class="sxs-lookup"><span data-stu-id="3ad89-111">[NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c) </span></span>  
<span data-ttu-id="3ad89-112"> [Estrutura de um programa Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md) </span><span class="sxs-lookup"><span data-stu-id="3ad89-112"> [Structure of a Visual Basic Program](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md) </span></span>  
<span data-ttu-id="3ad89-113"> [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)</span><span class="sxs-lookup"><span data-stu-id="3ad89-113"> [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)</span></span>
